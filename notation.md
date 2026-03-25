# 記号表（Julia / Python (NumPy) / MATLAB 対応表）

このページでは，**Julia / Python (NumPy) / MATLAB** における基本的なベクトル・行列操作や構文の違いを，特徴的なものを中心にまとめます．  

- Julia: `LinearAlgebra` パッケージの利用を前提  
- Python: `NumPy` の利用を前提  


---

## ベクトルと行列の生成

| 操作 | Julia | Python (NumPy) | MATLAB |
|------|-------|----------------|--------|
| 行ベクトル | `v = [1, 2, 3]` | `v = np.array([1, 2, 3])` | `v = [1, 2, 3]` |
| 列ベクトル | `v = [1; 2; 3]` | `v = np.array([[1], [2], [3]])` | `v = [1; 2; 3]` |
| 行列 | `A = [1 2; 3 4]` | `A = np.array([[1, 2], [3, 4]])` | `A = [1, 2; 3, 4]` |
| ゼロ行列 | `A = zeros(2, 2)` | `A = np.zeros((2, 2))` | `A = zeros(2, 2)` |
| 単位行列 | `I = I(2)` | `I = np.eye(2)` | `I = eye(2)` |
| 乱数行列 | `A = rand(2, 2)` | `A = np.random.rand(2, 2)` | `A = rand(2, 2)` |


---

## 要素のアクセスとスライシング

| 操作 | Julia | Python (NumPy) | MATLAB |
|------|-------|----------------|--------|
| 要素アクセス | `A[1, 2]` | `A[0, 1]` | `A(1, 2)` |
| 行の抽出 | `A[1, :]` | `A[0, :]` | `A(1, :)` |
| 列の抽出 | `A[:, 2]` | `A[:, 1]` | `A(:, 2)` |
| 部分行列 | `A[1:2, 2:3]` | `A[0:2, 1:3]` | `A(1:2, 2:3)` |

> ※ Julia / MATLAB は 1-indexed，NumPy は 0-indexed．


---

## 基本的な演算

| 操作 | Julia | Python (NumPy) | MATLAB |
|------|-------|----------------|--------|
| 転置（非共役） | `transpose(A)` | `A.T` | `A.'` |
| 共役転置 | `A'` | `A.conj().T` | `A'` |
| 行列積 | `A * B` | `A @ B` | `A * B` |
| 要素ごとの積 | `A .* B` | `A * B` | `A .* B` |
| 逆行列 | `inv(A)` | `np.linalg.inv(A)` | `inv(A)` |
| 行列式 | `det(A)` | `np.linalg.det(A)` | `det(A)` |


---

## 和・最大値・最小値

| 操作 | Julia | Python (NumPy) | MATLAB |
|------|-------|----------------|--------|
| 和 | `sum(x)` | `np.sum(x)` | `sum(x)` |
| 最大値 | `maximum(x)` | `np.max(x)` | `max(x)` |
| 最小値 | `minimum(x)` | `np.min(x)` | `min(x)` |
| 最大値のインデックス | `argmax(x)` | `np.argmax(x)` | `[~, idx] = max(x)` |
| 最小値のインデックス | `argmin(x)` | `np.argmin(x)` | `[~, idx] = min(x)` |


---

## 関数の定義

<table>
  <thead>
    <tr>
      <th>操作</th>
      <th>Julia</th>
      <th>Python</th>
      <th>MATLAB</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1行関数</td>
      <td><code>f(x) = x^2</code></td>
      <td><code>def f(x): return x**2</code></td>
      <td><code>function y = f(x); y = x^2; end</code></td>
    </tr>
    <tr>
      <td>複数行関数</td>
      <td>
        <pre><code>function f(x)
    return x^2
end</code></pre>
      </td>
      <td>
        <pre><code>def f(x):
    return x**2</code></pre>
      </td>
      <td>
        <pre><code>function y = f(x)
    y = x^2;
end</code></pre>
      </td>
    </tr>
    <tr>
      <td>無名関数</td>
      <td><code>f = x -&gt; x^2</code></td>
      <td><code>f = lambda x: x**2</code></td>
      <td><code>f = @(x) x^2</code></td>
    </tr>
  </tbody>
</table>


---

## 条件分岐

<table>
  <thead>
    <tr>
      <th>操作</th>
      <th>Julia</th>
      <th>Python</th>
      <th>MATLAB</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>if 文</td>
      <td>
        <pre><code>if x &gt; 0
    println("正")
end</code></pre>
      </td>
      <td>
        <pre><code>if x &gt; 0:
    print("正")</code></pre>
      </td>
      <td>
        <pre><code>if x &gt; 0
    disp("正")
end</code></pre>
      </td>
    </tr>
    <tr>
      <td>if / elseif / else</td>
      <td>
        <pre><code>if x &gt; 0
    println("正")
elseif x &lt; 0
    println("負")
else
    println("ゼロ")
end</code></pre>
      </td>
      <td>
        <pre><code>if x &gt; 0:
    print("正")
elif x &lt; 0:
    print("負")
else:
    print("ゼロ")</code></pre>
      </td>
      <td>
        <pre><code>if x &gt; 0
    disp("正")
elseif x &lt; 0
    disp("負")
else
    disp("ゼロ")
end</code></pre>
      </td>
    </tr>
  </tbody>
</table>


---

## ループ構造

<table>
  <thead>
    <tr>
      <th>操作</th>
      <th>Julia</th>
      <th>Python</th>
      <th>MATLAB</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>for ループ</td>
      <td>
        <pre><code>for i in 1:5
    println(i)
end</code></pre>
      </td>
      <td>
        <pre><code>for i in range(5):
    print(i)</code></pre>
      </td>
      <td>
        <pre><code>for i = 1:5
    disp(i)
end</code></pre>
      </td>
    </tr>
    <tr>
      <td>while ループ</td>
      <td>
        <pre><code>i = 1
while i &lt;= 5
    println(i)
    i += 1
end</code></pre>
      </td>
      <td>
        <pre><code>i = 1
while i &lt;= 5:
    print(i)
    i += 1</code></pre>
      </td>
      <td>
        <pre><code>i = 1;
while i &lt;= 5
    disp(i)
    i = i + 1;
end</code></pre>
      </td>
    </tr>
  </tbody>
</table>
