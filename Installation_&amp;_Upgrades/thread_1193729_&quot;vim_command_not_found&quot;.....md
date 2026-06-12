---
title: "&quot;vim command not found&quot;...."
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by itachis.eyes on 2009-06-21
ok i've been having problems with my audio driver working all the way and after an anurism or two i got them to work.
now i'm trying to fix the same problem on my ubuntu install and have been following this post: [http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)
i've gotten to the #> sudo vim /ect/modprobe.d/alsa-base command and come up with:
sudo: ./vim: command not found
so...what is the deal...do i need to install some kind of dependency for the vim command to work? if so where do i get this install? and if not...what do i need to do to get it to work?

---

### Post by Bachstelze on 2009-06-21
Please don't take this the wrong way, but [font="monospace"]vim[/font] isn't really the text editor you should use if you don't have much UNIX experience.

Replace [font="monospace"]vim[/font] with [font="monospace"]nano[/font] in that command. When you're done etiting your file in [font="monospace"]nano[/font], press Ctrl+O to save your file, Enter to confirm, and Ctrl+X to quit.

---

### Post by itachis.eyes on 2009-06-21
> **HymnToLife said:**
> Please don't take this the wrong way, but [FONT=monospace]vim[/FONT] isn't really the text editor you should use if you don't have much UNIX experience.

Replace [FONT=monospace]vim[/FONT] with [FONT=monospace]nano[/FONT] in that command. When you're done etiting your file in [FONT=monospace]nano[/FONT], press Ctrl+O to save your file, Enter to confirm, and Ctrl+X to quit.
no no, its fine...i know my way around windows very well, but now that i'm playing with linux its almost like i'm back at square one...almost. 
btw: thanks, that worked out great...well your help anyway i haven't rebooted yet so i won't know if that other post helped.

anyways once again thanks for your help

---

### Post by jowilkin on 2009-06-21
vim is a very nice editor, but it does take some time to learn to use it well.  It's not installed on Ubuntu by default, you can install it with ```
sudo aptitude install vim
```
There is a tutorial that comes with it called vimtutor, you can access it by typing at the command line ```
vimtutor
```

---

### Post by ad_267 on 2009-06-21
vim is just a text editor. You could replace vim with nano as already explained, or you could also use the default graphical text editor, gedit by using:
```
gksu gedit /ect/modprobe.d/alsa-base
```

---

### Post by itachis.eyes on 2009-06-22
yo peoples...i got it under-control, i used the nano editor instead of the vim editor and everything worked out great.

---

