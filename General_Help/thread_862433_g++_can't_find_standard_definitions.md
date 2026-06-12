---
title: "g++ can't find standard definitions"
date: 2008-07-17
forum: General Help
---

### Post by eakmeister on 2008-07-17
I am trying to build a piece of software, and this is the output I get after running make:

```
<snipped>
In file included from /usr/include/c++/4.2/cstring:51,
                 from /usr/include/c++/4.2/bits/stl_algobase.h:66,
                 from /usr/include/c++/4.2/bits/stl_tree.h:67,
                 from /usr/include/c++/4.2/map:65,
                 from ../../include/nitf/TRE.h:11,
                 from TRE.cpp:5:
/usr/include/c++/4.2/cstddef:55: error: ‘::ptrdiff_t’ has not been declared
In file included from /usr/include/c++/4.2/iosfwd:49,
                 from /usr/include/c++/4.2/bits/stl_algobase.h:70,
                 from /usr/include/c++/4.2/bits/stl_tree.h:67,
                 from /usr/include/c++/4.2/map:65,
                 from ../../include/nitf/TRE.h:11,
                 from TRE.cpp:5:
/usr/include/c++/4.2/bits/postypes.h:78: error: ‘ptrdiff_t’ does not name a type
In file included from /usr/include/c++/4.2/bits/stl_algobase.h:74,
                 from /usr/include/c++/4.2/bits/stl_tree.h:67,
                 from /usr/include/c++/4.2/map:65,
                 from ../../include/nitf/TRE.h:11,
                 from TRE.cpp:5:
/usr/include/c++/4.2/bits/stl_iterator_base_types.h:104: error: expected type-specifier before ‘ptrdiff_t’
<snipped>
```

It goes on for a while, but most of the error messages are due to "ptrdiff_t", which should be defined in stddef.h

Yes I have build-essential installed, and I am using Ubuntu 8.04

---

### Post by eakmeister on 2008-07-17
anybody?  This seems like there is a fairly simple solution.

---

