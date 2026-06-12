---
title: "[SOLVED] Find files with specific content"
date: 2008-07-29
forum: General Help
---

### Post by Paddy Landau on 2008-07-29
I want to search within a directory, and its large number of subdirectories, for all files that contain specific text.

I have tried a number of variations on the following ("searchtext" represents the text that I'm searching for, and I'm only interested in files with the extension ".php"):

fgrep --with-filename --max-count=1 --recursive --include=php searchtext *

However, I just can't seem to get it to do anything!

I can get results with this:

fgrep --with-filename --max-count=1 searchtext *.php

but of course that's not recursive, so it doesn't search the subdirectories.

Can anyone help me correct that "find" command, please?

---

### Post by Paddy Landau on 2008-07-29
I've just managed to answer my own question!

Here's the answer:

fgrep --with-filename --max-count=1 --recursive --include='*.php' -regexp=searchtext *

---

