# C++ STL 在算法竞赛中的核心用法

## 目录
- 字符串处理
- Vector 容器
- 输入输出技巧
- 常用算法函数
- 实战例题

---

## 一、字符串处理

### 1. string 基础操作

```cpp
#include <string>
using namespace std;

// 创建和初始化
string s1 = "Hello";
string s2(5, 'A');      // "AAAAA"
string s3(s1, 1, 3);    // "ell"

// 基本操作
s1.length();            // 或 s1.size()
s1.empty();             // 判断是否为空
s1.clear();             // 清空字符串

// 访问字符
char c1 = s1[0];        // 快速访问（不检查边界）
char c2 = s1.at(0);     // 带边界检查的访问

// 修改操作
s1 += " World";         // 追加字符串
s1.append("!!!");       // 追加
s1.push_back('!');      // 追加单个字符
s1.insert(5, ",");      // 在位置5插入
s1.erase(5, 1);         // 删除位置5的1个字符

// 查找操作
size_t pos = s1.find("World");
if (pos != string::npos) {
    cout << "找到在位置: " << pos << endl;
}

// 子串操作
string sub = s1.substr(0, 5); // "Hello"
```

### 2. getline() 详细用法

```cpp
#include <iostream>
#include <string>
using namespace std;

string line;
getline(cin, line);                // 默认到换行符

string data;
getline(cin, data, ',');           // 指定分隔符

while (getline(cin, line)) {
    // 处理每一行
}

while (getline(cin, line) && !line.empty()) {
    // 直到空行
}
```

### 3. 实用转换函数

```cpp
// 数字转字符串
int num = 123;
string str_num = to_string(num);

// 字符串转数字
string str = "456";
int num1 = stoi(str);
long num2 = stol(str);
double num3 = stod("3.14");

// 字符串流分割
#include <sstream>
string input = "1 2 3 4 5";
stringstream ss(input);
int x;
while (ss >> x) {
    cout << x << " ";
}
```

---

## 二、Vector 容器

### 1. 创建和初始化

```cpp
#include <vector>
using namespace std;

vector<int> vec1;
vector<int> vec2(10);
vector<int> vec3(5, 100);
vector<int> vec4 = {1, 2, 3, 4, 5};

vector<vector<int>> matrix(5, vector<int>(5, 0));
```

### 2. 访问元素

```cpp
vector<int> vec = {10, 20, 30, 40, 50};
cout << vec[0] << endl;
cout << vec.at(0) << endl;
int first = vec.front();
int last = vec.back();
```

### 3. 容量操作

```cpp
int size = vec.size();
bool is_empty = vec.empty();
vec.capacity();
vec.reserve(1000);
vec.shrink_to_fit();
```

### 4. 修改操作

```cpp
vec.push_back(10);
vec.emplace_back(20);
vec.insert(vec.begin() + 2, 30);

vec.pop_back();
vec.erase(vec.begin() + 1);
vec.clear();
```

### 5. 迭代器遍历

```cpp
for (int i = 0; i < vec.size(); i++) {}
for (auto it = vec.begin(); it != vec.end(); it++) {}
for (const auto& num : vec) {}
for (auto it = vec.rbegin(); it != vec.rend(); it++) {}
```

### 6. 蓝桥杯高频用法

```cpp
vector<int> nums;
int x;
while (cin >> x) nums.push_back(x);

vector<vector<int>> graph(n);
graph[u].push_back(v);

vector<int> prefix(arr.size() + 1, 0);

sort(vec.begin(), vec.end());
vec.erase(unique(vec.begin(), vec.end()), vec.end());
```

---

## 三、输入输出技巧

### 1. 加速 IO

```cpp
ios::sync_with_stdio(false);
cin.tie(nullptr);
```

### 2. 常见输入模式

```cpp
cin >> n;
getline(cin, str);
```

### 3. 格式化输出

```cpp
#include <iomanip>
cout << fixed << setprecision(2) << pi;
```

---

## 四、常用算法函数

### 1. 排序与查找

```cpp
sort(vec.begin(), vec.end());
binary_search(vec.begin(), vec.end(), 5);
```

### 2. 其他算法

```cpp
reverse(vec.begin(), vec.end());
rotate(vec.begin(), vec.begin() + 2, vec.end());
next_permutation(vec.begin(), vec.end());
```

### 3. 数值算法

```cpp
#include <numeric>
accumulate(vec.begin(), vec.end(), 0);
```

---

## 五、实战例题

### 例题 1：矩阵输入

```cpp
vector<string> matrix;
```

### 例题 2：单词频率统计

```cpp
map<string, int> wordCount;
```

### 例题 3：DP 斐波那契

```cpp
vector<long long> dp(n + 1);
```

### 例题 4：BFS 图遍历

```cpp
queue<int> q;
```

---

## 重要提醒

- vector 复制是深拷贝，注意性能
- 修改容器后迭代器可能失效
- 使用 reserve() 优化性能
- [] 不检查边界，at() 会检查
- getline 会读取整行（包括空格）

---

## 快速参考表

| 操作 | 函数 | 时间复杂度 | 说明 |
|---|---|---|---|
| 字符串长度 | str.length() | O(1) | 等价 size() |
| 整行读取 | getline | O(n) | 默认 \n |
| 排序 | sort | O(n log n) | 默认升序 |
| 二分查找 | binary_search | O(log n) | 已排序 |
| 去重 | unique | O(n) | 需排序 |

---

*适用：蓝桥杯算法竞赛 / C++11 及以上*

最后更新：2024 年

