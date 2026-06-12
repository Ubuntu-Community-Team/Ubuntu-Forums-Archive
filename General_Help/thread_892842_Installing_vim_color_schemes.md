---
title: "Installing vim color schemes"
date: 2008-08-17
forum: General Help
---

### Post by patchin_house on 2008-08-17
*Karaj geamikoj!*

This one will be very quick... I love using gvim every now and then, and I recently found myself downloading some cool color schemes. 

I know that they should go into usr/share/vim/vimcurrent/colors... but just dragging them to that folder won't do the job. The usr/share folder is read only by default.

O wise ones, any ideas?

Philip David
2008.08.17

---

### Post by pauper on 2008-08-17
Prepend "sudo" to "mv SOURCE DESTINATION".

---

### Post by indiv on 2008-08-18
The file manager on ubuntu is called **nautilus**.  You can open a command prompt and type **sudo nautilus &**, or create a command-line launcher that runs sudo nautilus.  The browser window that pops up will be able to do anything in any directory, so be careful!

You may find other helpful suggestions in this thread that are perhaps better:
[http://fedoraforum.org/forum/archive/index.php/t-20.html](http://fedoraforum.org/forum/archive/index.php/t-20.html)

---

### Post by patchin_house on 2008-08-19
Thank you for the warning...nautilus is indeed installed (although I rarely use it), so I'll give that a go (and then quickly reboot just to be safe!)

Philip David
2008.08.19

---

### Post by patchin_house on 2008-08-19
Yes! Running sudo nautilus did the trick! Many thanks, indiv!

Philip David
(go, vim, go!)
2008.08.19

---

### Post by indiv on 2008-08-19
That's good news.  I just found out from another thread that instead of **sudo**, you can use **gksu**.  gksu is the GUI version of sudo.  So if you wanted to create a full-access nautilus launcher on the launcher panel or desktop or something, you would use the command **gksu nautilus** instead of sudo nautilus.

---

### Post by ~LoKe on 2008-09-03
I downloaded a .vim file (impact.vim) and moves it to /usr/share/vim/vimcurrent/colors

But...how do I actually use it? O_O

---

### Post by ~LoKe on 2008-09-03
Anyone?  I managed to get the colors to change, but they're not what they're supposed to be.  They're supposed to look like [this](http://aimeta.deviantart.com/art/dwm-on-freebsd-74430457).

He gave me the config, [here](http://www.vim.org/scripts/script.php?script_id=1326).  Is that the wrong script or am I just doing something wrong?

---

