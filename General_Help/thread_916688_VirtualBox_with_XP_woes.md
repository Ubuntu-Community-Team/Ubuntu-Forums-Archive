---
title: "VirtualBox with XP woes"
date: 2008-09-11
forum: General Help
---

### Post by spynappels on 2008-09-11
Hi guys, I hope you can help me.

I have a clean install of Windows XP running in a Virtual Box environment and I am having some major problems. Windows runs fine, and I can use Internet Explorer etc, but I have no sound, the SD card reader built into my machine which works fine with Ubuntu is not recognised, I cannot access my network printer and the screen resolution is limited to 1024 by 768. These problems are keeping me from migrating to Ubuntu on all my machines as I need a working XP install to sync with my WM device and for a few other things that only work in windows.

  I would love to get my VirtualBox machine working properly as then my other laptop can also be ubuntufied, so any help you can giv would be very much appreciated.

  Thanks very much.
   Stefan

---

### Post by fwre01 on 2008-09-11
do you have guest additions installed on your windows virtual machine?

---

### Post by spynappels on 2008-09-11
No, how do I do that? Get them from VirtualBox website?  I'm sorry but I'm kinda new at this virtualisation thing.

---

### Post by fwre01 on 2008-09-11
There is a button on the title bar in the window which the virtual machine is running in that says install guest additions. then it just launches it within windows. That should fix a lot of problems. Let me know what else isnt working afterwards

---

### Post by triphazard on 2008-09-11
The virtualbox help is very clear so i'd recommend starting there but i think, from memory, you might need to start the xp machine with an iso mounted (the iso comes with virtualbox).  If you look on the tools menu you should see "install guest additions".

Hmmm...this is the most vague post ever.  Sorry.  Searching the virtualbox help for guest additions is probably your best bet.  :)

---

### Post by spynappels on 2008-09-11
I got that, thanks for that.

  The screen resolution has been sorted out, but I still have no audio, no NAS and network printer and the SD card drive still does not show up.

 The audio and NAS are the greatest issues for me at the moment, the printer and SD card are secondary.

  thanks for your help so far.

   Stefan.

---

### Post by fwre01 on 2008-09-11
Make sure in the sound settings for your virtual machine you are using the right audio server. (you may need to change this to each server just to test it)

Whats the NAS issue? whats your NIC setup as? NAT? or HOST?

---

