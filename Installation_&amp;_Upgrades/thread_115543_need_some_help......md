---
title: "need some help....."
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by sharn on 2006-01-10
hi i came here because i have a problem with ubuntu. after i do a default install i reboot and it comes up with error 17 for grub....... now i think i can find out how to fix this if i can get into my normal ubuntu instead of on live :???:  soo my question is: can i make a boot disk to bypass grub and load linux?? :confused:

EDIT: wow by how long its taken you guys to post on others i thought youd have posted on mine by now too..... but anyway im gonna be gone for 1 1/2 - 2 hours and ill check this when i get back

---

### Post by Zelut on 2006-01-10
just doing a quick search of the wiki I found this... this might help you out.

[recovering Grub]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")

---

### Post by Sef on 2006-01-10
I wrote this in another thread:

Here is what Gentoo's documentation says about it:

5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Be sure to check your root(x,y) settings in your grub.conf. 

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.

[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

Here is another thread that dealt with this issue:

[http://ubuntuforums.org/showthread.php?t=101316](http://ubuntuforums.org/showthread.php?t=101316)

---

