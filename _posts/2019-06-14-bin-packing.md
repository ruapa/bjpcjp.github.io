---
date:   2019-06-14 0:0:0 -0500
layout: post
title: bin packing
categories: math
---

![illustration](/px/math/bin-packing.png)
<br>
Bin packing arises in a variety of packaging and manufacturing problems. Suppose that you are manufacturing widgets cut from sheet metal or pants
cut from cloth. To minimize cost and waste, we seek to lay out the parts so as to use as few fixed-size metal sheets or bolts of cloth as possible.


Identifying which part goes on which sheet in which location is a bin-packing variant called the <strong>cutting stock problem</strong>. Once our widgets have been successfully manufactured, we are faced with another problem—how best to fit the boxes into a minimum number of trucks needed to ship everything.

Even the most elementary bin-packing problems are NP-complete. Thus, we are
doomed to think in terms of heuristics instead of worst-case optimal algorithms.<br>

The following factors are key:

• __What are the shapes and sizes of the objects?__ – Solving a standard jigsaw puzzle is a much different problem than packing squares into a rectangular box. In 1-D bin packing, each object’s size is a simple integer. This is equivalent to packing boxes of equal width into a chimney of that width, and makes it a special case of the __knapsack problem__.

When all boxes are identical in size and shape, repeatedly filling each row
gives a reasonable, but not optimal, packing. Consider trying to fill a 3 × 3 square with 2 × 1 bricks. You can only pack three bricks using one
orientation, while four bricks suffice with two.

* __Are there constraints on the orientation and placement of objects?__ – Many
boxes are labeled “this side up” or “do not stack” (requiring them sit on top of any box pile). Respecting these constraints restricts our flexibility and increases the number of trucks needed. 

* __Is the problem on-line or off-line?__ – Do we know the complete set of objects to pack at the beginning of the job (an off-line problem)? Or will we get them one at a time and deal with them as they arrive (an on-line problem)?

Off-line heuristics order the objects by size or shape and then insert them into bins. Typical insertion rules are (1) select the first or leftmost bin the object fits in, (2) select the bin with the most room, (3) select the bin that provides the tightest fit, or (4) select a random bin.

First-fit decreasing is usually the best heuristic. Sort the objects in decreasing order of size, so that the biggest object is first and the smallest last. Insert each object one by one into the first bin that has room for it; if no bin has room, we must start another bin.

* __Execution time:__ First-fit decreasing can be done in O(n lg n + bn) time, where b ≤ min(n,m) is the number of bins used. Simply do a linear sweep through the bins on each insertion. A faster O(n lg n) implementation is possible by using a binary tree to keep track of the space remaining in each bin.

* In the case of nonconvex parts, considerable space can be wasted in the holes created by placing the part in a box. One solution is to find the maximum
empty rectangle within each boxed part and use this to contain remaining parts.

[Source: Algorithm Design Manual](/pdfs/math/bin-packing-ADM.pdf)