---
title: "[SOLVED] edit grub menu"
date: 2008-10-21
forum: General Help
---

### Post by Rita G. on 2008-10-21
ubuntu 8.10

how do i get permission to edit grub menu?

---

### Post by ronnielsen1 on 2008-10-21
In a terminal type sudo gedit /boot/grub/menu.lst

---

### Post by Rita G. on 2008-10-21
wow..........that was easy!

i must have spent an hour or so trying to log in as root.

thanks ronnielsen1

---

### Post by oldos2er on 2008-10-21
> **ronnielsen1 said:**
> In a terminal type sudo gedit /boot/grub/menu.lst

 When calling a graphical application like gedit, use "gksudo" or "gksu" in place of sudo, i.e. 

gksu gedit /boot/grub/menu.lst

---

### Post by PsychedelicReaction on 2008-10-21
you can also install and use startupmanager from the repositories

---

### Post by ronnielsen1 on 2008-10-21
> When calling a graphical application like gedit, use "gksudo" or "gksu" in place of sudo, i.e. 

gksu gedit /boot/grub/menu.lst

End result is the same. Why does Ubuntu want you to run it that way?

---

### Post by Rita G. on 2008-10-21
thank you all!

you're such sweeties!

---

### Post by Idefix82 on 2008-10-21
> **ronnielsen1 said:**
> End result is the same. Why does Ubuntu want you to run it that way?

Have a look here:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by oldos2er on 2008-10-21
> **ronnielsen1 said:**
> End result is the same. Why does Ubuntu want you to run it that way?

 It has the potential to screw up ~/.ICEauthority , among other things. See [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by drs305 on 2008-10-21
RitaG,

I strongly recommend someone with your experience start by using StartUp-Manager (as mentioned by PsychedelicReaction). It is a gui-based app that will allow you set a variety of menu options, including default OS/kernel, menu timeout, how grub updates, numbers of kernels to display, etc.

I wrote a tutorial a while back about how to install and use StartUp-Manager. Here is the link: 
[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by sethvath on 2008-10-21
If you're calling a graphical app, use Alt+F2 and type in gksu gedit from the run command than using terminal. That way you can leave all sudo commands to terminal.

---

