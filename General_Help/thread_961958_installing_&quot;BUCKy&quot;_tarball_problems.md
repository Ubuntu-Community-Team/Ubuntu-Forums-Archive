---
title: "installing &quot;BUCKy&quot; tarball problems"
date: 2008-10-28
forum: General Help
---

### Post by weirb on 2008-10-28
Hi, I have just installed the 8.10 RC (I couldn't wait one day!) on to a dedicated computer to be used for phylogenetic analysis.

Some programs that I need are in the package manager and work fine. However the main reason for my installing linux was to run the application BUCKy 1.2 (Bayesian concordance analysis).

[http://www.stat.wisc.edu/~larget/bucky.html](http://www.stat.wisc.edu/~larget/bucky.html)

the install instructions are pretty simple. Just untar and make. I have installed the build-essential package.

However all I get are errors (a portion pasted below): 

bevan@phylo-linux:~/Desktop/BUCKy-1.2/src$ make
g++ -c -O3 bucky.C
In file included from bucky.C:88:
bucky.h: In function ‘double logA(double, int)’:
bucky.h:21: error: ‘exit’ was not declared in this scope
bucky.h: In function ‘double logUB(unsigned int)’:
bucky.h:35: error: ‘exit’ was not declared in this scope
bucky.h: In constructor ‘State::State(double, int, int, std::vector<Gene*, std::allocator<Gene*> >, bool, Rand&)’:
bucky.h:339: error: ‘sort’ was not declared in this scope
bucky.h: In member function ‘void State::setTop(int, int)’:
bucky.h:365: error: ‘sort’ was not declared in this scope
bucky.h: In member function ‘ConcordanceNode* ConcordanceEdge::getOtherNode(ConcordanceNode*)’:
bucky.h:795: error: ‘exit’ was not declared in this scope
bucky.h: In member function ‘ConcordanceNode* ConcordanceNode::getNeighbor(ConcordanceEdge*)’:
bucky.h:827: error: ‘exit’ was not declared in this scope

Can someone please help with this? I have used linux in the past but I am still pretty much a newbie

Thanks,

Bevan

---

### Post by weirb on 2008-10-28
Well I have solved my own problem. It seems the issue was that some #includes were missing which broke gcc 4.3.2. Apparently in In GCC 4.3, the C++ header dependencies have been cleaned up so you need to directly #include everything you use.


I simply added the lines:

#include <algorithm>
#include <stdio.h>
#include <stdlib.h>

to bucky.h 

and everything worked perfectly.

---

