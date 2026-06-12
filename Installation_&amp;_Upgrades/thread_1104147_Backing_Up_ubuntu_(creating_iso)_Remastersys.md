---
title: "Backing Up ubuntu (creating iso) Remastersys"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by .:Justus:. on 2009-03-23
Hey, well i just made a backup of my entire system using the backup command in remastersys, now i want to burn the iso of my system onto a dvd but i have no clue where the program saved the iso... Any help?

---

### Post by warfacegod on 2009-03-27
Try searching for ".iso"

Search for files is in the Places menu.

---

### Post by malfindin on 2009-03-27
Hi there. This my first post on the Ubuntu forums and I think I can help a lot with this one. My whole home based biz is based around remastersys. Because it lets you install your very own fully updated version of Ubuntu on other peoples computers. I don't charge for this, so don't think this post is in anyway a sales pitch. Just love to help out with this wonderful thing that is Ubuntu.

First off it stores the files in /home/remastersys/remastersys

Then some tips:

1. You can copy them, but you can't delete them unless you use "sudo nautilus". Better plan--use the *clean temporary* files function in the Remastersys programs. It has it's own user which has rights to it's own home directory. But....

2. Don't clean temporary files until you have copied the ISO. Guess what one of the temporary files is??? The ISO.

3. I test with VirtualBox 2.1.4. Just mount it as as an ISO.

4. Oh and check it out, with a little utility called Unetbootin you can put your whole sys, files and all, on a USB drive and boot live on other poeples computers in LESS TIME THAN THEY COULD BOOT NORMALLY! It has to be seen to be believed. Just treat the Remastersys as though it was a normal Ubuntu install disk...basically it is.

And to any admins out there, Feel free to grade me on my first post. If there are any other Remastersys questions out there also feel free to send them my way. It's a buggy little program but the bomb if used correctly.

---

