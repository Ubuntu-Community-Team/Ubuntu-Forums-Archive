---
title: "Please help-- Command Line on startup!"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by id10twork on 2009-04-25
I'm using a laptop. When I try to boot since the update, it gets to the Ubuntu screen, the loading bar goes across, then a command screen comes up and tells me something about it waited too long, then it comes up and says Think Box version 10.x.x and tells me I need to enter some commands and to type "help" for help; I type help, and all of the commands are very foreign to me and I tried to screw around by just typing one in, and it never does anything except go to the next line (probably b/c I have no idea what I'm doing). Someone please help! I have all my data on there and would like to not lose any of it, if possible. :confused:

---

### Post by id10twork on 2009-04-25
more information: the message it gives me is it cannot wait any longer for the root and it can't find the module cat /proc/modules; ls /dev

---

### Post by id10twork on 2009-04-25
I have looked past thru previous posts and thought 
[http://ubuntuforums.org/showpost.php?p=6581939&postcount=322](http://ubuntuforums.org/showpost.php?p=6581939&postcount=322) might help because it seems I'm having somewhat of the same problem, but it told me that it could also not find those.](*,)

---

### Post by DracoJesi on 2009-04-25
I'm pretty sure this was mentioned in the release notes...

> Users have reported slower than normal detection of SATA hard drives on systems with Intel D945 motherboards in Ubuntu 9.04. This may cause the system to drop to a busybox initramfs shell on boot with a "Gave up waiting for root device." error. Wait a minute or two and then exit the initramfs shell by typing 'exit'. Booting should proceed normally. If it doesn't, wait a bit longer and try again. Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel. (290153) 

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

### Post by mtalavera on 2009-04-25
I've having the same exact problem.  I've may have complicated things because I have two hard drives in a RAID 1 mirror configuration and the error message says it cannot find the root partition /dev/md1.  I'm really a newbie, so I'm not sure how to proceed at this point.

---

### Post by id10twork on 2009-04-25
DracoJesi thanks for the reply and article. I waited for 20 mins on my last attempt to use the "exit" fix (tried in a few intervals), but it did not work. also, I checked out my specs and that is not my motherboard. It looks like I'm back at square one.

---

### Post by DracoJesi on 2009-04-25
> **id10twork said:**
> DracoJesi thanks for the reply and article. I waited for 20 mins on my last attempt to use the "exit" fix (tried in a few intervals), but it did not work. also, I checked out my specs and that is not my motherboard. It looks like I'm back at square one.

np, and hmmm, well, is there any way you could copy what it says word for word...

and any idea what think box refers to?

---

### Post by id10twork on 2009-04-26
i eventually booted into another partition, grabbed all my data from the one i screwed up, and did a new install of jaunty. i do have the entire error word for word, but it did say, "can't find the module cat /proc/modules; ls /dev" and told me that my UUID did not exist

---

