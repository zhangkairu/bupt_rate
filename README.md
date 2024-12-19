# bupt_rate
吃完安眠药晕乎，不想复习期末，公选课选太多，遂用gpt编写了一下学期末的自动评教代码
### **使用方法**：
在评教页面打开控制台，将代码粘贴到控制台中并回车，即可自动填写评教表单。

### **注意点：**
1.每次评价完一个切换到另一个时，要如下点击一点这个td，不然输入进去没反应。
![image](https://github.com/user-attachments/assets/f22e9027-1110-4803-8acb-1ea6b9c2c6ff)
2.默认评分过高，最后要手动调整一下，把其中一个完全符合改成基本符合。

```
// 遍历每一行的 <td name="zbtd"> 元素
document.querySelectorAll('td[name="zbtd"]').forEach((row, index) => {
    // 在当前行中选择第一个单选框（完全符合）
    const radio = row.querySelector('input[type="radio"]:first-child');
    if (radio) {
        radio.click(); // 模拟点击事件
        console.log(`第 ${index + 1} 行的 '完全符合' 已被选中。Value: ${radio.value}`);
    } else {
        console.log(`第 ${index + 1} 行未找到 '完全符合' 的单选框。`);
    }
});
// 定义要选中的复选框的 value 值
const valuesToSelect = [
    "29752201F55DC596E0639037030AFF47", // 老师认真负责
    "29752201F55EC596E0639037030AFF47", // 老师非常有耐心
    "29752201F560C596E0639037030AFF47", // 老师教学水平高
    "29752201F561C596E0639037030AFF47"  // 老师能够调动上课积极性
];

// 遍历所有的 checkbox
document.querySelectorAll('input[type="checkbox"]').forEach((checkbox) => {
    if (valuesToSelect.includes(checkbox.value)) {
        checkbox.checked = true; // 选中复选框
        console.log(`复选框已选中：${checkbox.value}`);
    }
});
// 遍历所有的隐藏输入框
document.querySelectorAll('input[type="hidden"][name="pj03id"]').forEach((hiddenInput) => {
    if (hiddenInput.value === "1A4286766B7644D68B768C4E569DBA60") {
        // 找到第一个隐藏输入框对应的文本框并填入“没有”
        hiddenInput.closest('tr').querySelector('textarea[name="jynr"]').value = "没有";
        console.log("第一个框已填入：没有");
    } else if (hiddenInput.value === "33C2602E9CB34380B4A5A6003E03E96B") {
        // 找到第二个隐藏输入框对应的文本框并填入“都很好”
        hiddenInput.closest('tr').querySelector('textarea[name="jynr"]').value = "都很好";
        console.log("第二个框已填入：都很好");
    }
});

```
