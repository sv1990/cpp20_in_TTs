Range-based algorithms
---


C++20 adds range based version for all algorithms

<table>
<tr>
<th>
C++
</th>
<th>
C++20
</th>
</tr>
<tr>
<td  valign="top">

<pre lang="cpp">
std::vector<int> v{2, 4, 1, 2};
std::sort(begin(v), end(v));
</pre>
</td>
<td  valign="top">
<pre lang="cpp">
std::vector<int> v{2, 4, 1, 2};
std::ranges::sort(v);
</pre>
</td>
</tr>
</table>

It also adds an additional  parameter for projections, i.e. Function-like objects that are applied on each object inside the range before comparing them.

<table>
<tr>
<th>
C++
</th>
<th>
C++20
</th>
</tr>
<tr>
<td  valign="top">

<pre lang="cpp">
std::vector&lt;std::pair&lt;int, std::string&gt;&gt; v{{2, 4}, {1, 2}};
std::sort(begin(v), end(v), [](auto&& l, auto&& r) {
	return l.second < r.second;
});
</pre>
</td>
<td  valign="top">
<pre lang="cpp">
std::vector&lt;std::pair&lt;int, std::string&gt;&gt; v{{2, 4}, {1, 2}};
std::ranges::sort(v, std::less<>{}, 
                  &std::pair&lt;int, std::string&gt;::second);
</pre>
</td>
</tr>
</table>