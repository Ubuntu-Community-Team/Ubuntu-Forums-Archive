---
title: "how to make the vi-reader simpler?"
date: 2008-08-18
forum: General Help
---

### Post by susruta101 on 2008-08-18
when I use the ***vi <filename>*** from terminal, in Fedora or SuSE I get a colourful vi-reader. Its helpful to program in that. it colours the opening and closing braces and if I press tab, the void space also have some colour. Can we do that in Ubuntu too?

and whenever I import a program from anywhere else, and open it in Ubuntu 8.04, every line in the program has a ***M^*** at the end. How to remove that?

---

### Post by indiv on 2008-08-18
ubuntu comes with vim-tiny to save disk space.  Install the vim or vim-full package:

sudo apt-get install vim
OR
sudo apt-get install vim-full

Now edit vimrc to get syntax highlighting for pretty colors (/etc/vim/vimrc affects all users):
sudo vi /etc/vim/vimrc
scroll down to the line that says "syntax on
delete the quote character (") to uncomment the line.


The ^M is a Windows line ending (like if you created the file in Windows notepad.exe and then edited it in vim, you may see ^M at the end of each line).  vim supports detecting line endings, and if you install the full package, you shouldn't have this problem anymore.

If you do continue to have the problem, in vim do this:
:set ff
<it should print ff=dos.. if it doesn't, try this:>
:e ++ff=dos

There are otherwise many ways to fix line endings.  Just search for 'vim line endings' or something similar in google.

[B]
If things don't match the vim you're used to on other systems, just look at your vimrc on the other linux systems and copy the settings you like to make ubuntu vim match.
[/B]

---

### Post by susruta101 on 2008-09-08
Thanks a lot...I did this and my problem is solved..

---

### Post by xadder on 2008-09-08
You can also get rid of the dos-endings by converting the file externally,
using e.g. the dos2unix command on the file.

---

