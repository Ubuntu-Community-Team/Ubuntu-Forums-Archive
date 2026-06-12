---
title: "fix mbr with windows xp computer"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by ciclopropano on 2009-08-22
I helped a friend to unistall ubuntu from his computer and now we need a windows disk to fix the mbr so that windows is bootable again
the problem is that we dont have a disk of the windows version originaly installed in the computer and we are not sure about what version of windows xp is installed

can I do the fixmbr thing with any version of windows xp CD or does it has to be the same version as the one installed?

---

### Post by HolyMythos on 2009-08-22
I don't know how to fix your problem but I'm kinda facing something like yours too. Did you just delete Ubuntu without changing the mbr? Because I'm thinking about deleting Ubuntu but I don't know how to change the mbr without the installation CD for Vista (what I currently have).

---

### Post by ciclopropano on 2009-08-22
I just ereased the partitions where ubuntu (actually kubuntu) and  linux swap were and resized the windows partition using a windows program. there might be a way to do it from ubuntu and fix the mbr from there but I dont know how
I actually followed this [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

---

### Post by sahabcse on 2009-08-22
for fixing the grub issue please follow below url

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)

---

### Post by ciclopropano on 2009-08-22
> **sahabcse said:**
> for fixing the grub issue please follow below url

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)

but there's no point on fixing the grub if the computer is only going to have windows installed

---

### Post by stlsaint on 2009-08-22
HALT THE PRESS!! guys you do not have to erase ubuntu y on earth would anybody want to do that!! :) Grub did not erase windows unless you jacked something up during install!! please post your menu.lst here so that we can assist you further...dont erase anything yet!! type this in terminal...

sudo gedit /boot/grub/menu.lst

and post what you get!!

---

### Post by stlsaint on 2009-08-22
> **stlsaint said:**
> HALT THE PRESS!! guys you do not have to erase ubuntu y on earth would anybody want to do that!! :) Grub did not erase windows unless you jacked something up during install!! please post your menu.lst here so that we can assist you further...dont erase anything yet!! type this in terminal...

sudo gedit /boot/grub/menu.lst

and post what you get!!


gedit is the text editor i use...if you use nano than replace gedit with nano or whatever you use!!

---

### Post by louieb on 2009-08-22
:confused: not the 1st - won't be the last - lots of ways to fix - [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

---

### Post by ciclopropano on 2009-08-22
> **stlsaint said:**
> HALT THE PRESS!! guys you do not have to erase ubuntu y on earth would anybody want to do that!! :) Grub did not erase windows unless you jacked something up during install!! please post your menu.lst here so that we can assist you further...dont erase anything yet!! type this in terminal...

sudo gedit /boot/grub/menu.lst

and post what you get!!
this is not my cumputer we are talking about if you read carefully, so its not my choice. I just need to get windows back to normal
I know, I would have kept linux if it was mine but it's not
So far no one has answered the original question

can I use any windows xp CD version to fix the mbr or does it has to be as the same version installed on the computer???

---

### Post by stlsaint on 2009-08-22
try downloading "DaRt for XP" or try xp cd...should work...havent tried in a while!!

---

### Post by louieb on 2009-08-22
> **ciclopropano said:**
> So far no one has answered the original question..can I use any windows xp CD version to fix the mbr ... Yes

---

### Post by presence1960 on 2009-08-22
> **ciclopropano said:**
> this is not my cumputer we are talking about if you read carefully, so its not my choice. I just need to get windows back to normal
I know, I would have kept linux if it was mine but it's not
So far no one has answered the original question

can I use any windows xp CD version to fix the mbr or does it has to be as the same version installed on the computer???

I would try any XP install CD and do [this]("http://ubuntuforums.org/showthread.php?t=1014708")
it can't hurt because it will only write to the MBR where GRUB is. it won't touch the windows partition. At the very worst you will be where you are now- unable to boot except there will be no GRUB.

---

### Post by presence1960 on 2009-08-22
> **HolyMythos said:**
> I don't know how to fix your problem but I'm kinda facing something like yours too. Did you just delete Ubuntu without changing the mbr? Because I'm thinking about deleting Ubuntu but I don't know how to change the mbr without the installation CD for Vista (what I currently have).

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Go there to download the Vista recovery console iso and then burn it as an image to CD. This is the recovery console only not a Vista installation disc. Then go [here]("http://ubuntuforums.org/showthread.php?t=1014708") and follow instructions for Vista when booting off that CD

---

