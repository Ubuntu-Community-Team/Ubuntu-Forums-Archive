---
title: "nautilus automatic emblems"
date: 2008-07-11
forum: General Help
---

### Post by lgoster on 2008-07-11
Hi everybody,

I would like first to explain a problem I had, and then the possible solution.

I configured nautilus to edit my '.c' files using 'gvim' by default. To my surprise, I noticed that only for some '.c' files I had the option of 'Open with gvim' when I right-clicked on a particular file. On other '.c' files I just had an 'Open' option which did nothing when I selected it. For this latter case Nautilus did indicate me that the source was a C file ('Properties' option). 

The problem was, in fact, that for the latter files the 'executable' flag was activated. After changing all .c files to rw mode (with no 'x' flag), the behavior of Nautilus was correct (i.e. I obtained the 'Open with gvim' option).

In order to avoid possible problems, I now have 'Column view' and added the 'Permissions' column to the view pane. However, if other people have an 'Icon View' this is not possible.

Thus, I would like to ask if Nautilus can add automatically emblems to those files that e.g. are executable. This would allow users to easily locate executable files.

Thanks!

Luis

---

