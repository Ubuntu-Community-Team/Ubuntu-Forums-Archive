---
title: "[SOLVED] [vim] Syntax highlighting not happening"
date: 2008-10-24
forum: General Help
---

### Post by fiddler616 on 2008-10-24
Hello,
I am trying very hard to move from gedit to vim for my Python pursuits, and most things are going swimmingly--except I've hit a wall when it comes to syntax highlighting.
I downloaded [this]("http://www.vim.org/scripts/script.php?script_id=790"), and it said to install it in ~/.vim/syntax . I found .vim was actually in ~/etc/, but it didn't have a syntax folder. Should I create one?
I also saw that I could do it the old-fashioned way and 
```
:help source
```
it, but that just gave me the following error:
>  E433: No tags file
E149: Sorry, no help for source
So I'm out of things to try
Thanks in advance

---

### Post by bab1 on 2008-10-24
create a file ```
.vimrc
``` in your home directory.

Add  to it:```
syn on
```

---

### Post by fiddler616 on 2008-10-24
> **bab1 said:**
> create a file ```
.vimrc
``` in your home directory.

Add  to it:```
syn on
```
Er...
> $ vim
Error detected while processing /home/tmacdonald/.vimrc:
line    1:
E319: Sorry, the command is not available in this version: syn on
Press ENTER or type command to continue


---

### Post by Denestria on 2008-10-24
I struggled with getting syntax highlighting turned on as well.  I had to remove vim-tiny and make sure that vim-full is installed.

---

### Post by geirha on 2008-10-24
Yes, install [vim-full](apt://vim-full) then edit /etc/vim/vimrc as root, read through the commented options and enable the things you want.

You should try out [vim-gnome](apt://vim-gnome) too. It has better mouse integration.

---

### Post by jerome1232 on 2008-10-24
You actually just need vim-runtime to get that working, but yeah vim-full will get it done too.

---

### Post by blue13130 on 2008-10-24
The file .vimrc should actually read this:

syntax on

NOT 
syn on

---

### Post by geirha on 2008-10-24
> **blue13130 said:**
> The file .vimrc should actually read this:

syntax on

NOT 
syn on

They are both correct. syn is just a shorthand for syntax.

---

### Post by fiddler616 on 2008-10-24
Sweet! / Solved! / Thanks, all of you!

---

