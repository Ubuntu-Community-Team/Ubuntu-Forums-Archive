---
title: "Synaptic freezes after upgrade from 7.10 to 8.04"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by hierogrammate on 2009-03-16
Greetings:

Today, I decided to upgrade from 7.10 to 8.04 using the Update Manager (btw, have Ubuntu in a dual-boot configuration with Windows XP). Everything went smoothly until the "cleanup" phase after the upgrade install: **the PC froze** and  I had to **force-restart** the machine. 

Apparently, the update did take place anyway, since I managed to boot into Ubuntu 8.04 without any problem. As far as I can tell, it runs fine.

However, when I try to use the update manager it says that "Not all updates can be installed." If I choose the "partial update," nothing really seems to happen. 

If I select instead the Close button, I get a "Software index is broken" message. If I try to follow the suggested solutions, either using **Synaptic** or run "**sudo apt-get install -f**," it asks me if I want to uninstall "**linux-image-2.6.22-15-generic**." When I say "yes," it starts working on something but, after it types the line "Updating /boot/grub/menu.lst ..done" *the machine **locks** completely* and I have to reboot the PC. (BTW, when I open Synaptic, linux-image-2.6.22-15-generic is highlighted red and already marked for removal... it apparently never manages to get rid of it though.)

Because the computer freezes, I'm unable to post any screenshots. Did something become corrupt during upgrade? If so, how can I I fix it so "**sudo apt-get install -f**" stops crashing at the end?

I'm sorry if I am not being too technical in my description, but I'm still rather green using Ubuntu (or Linux, for that matter), and I'm not sure what other details to add to my question. I've searched the forum, but the few posts I've found doesn't really seem to address this particular issue (I may be wrong, though, maybe I just didn't understand the explanations being given). 

I'd appreciate any help on this matter. I hope I don't have to reinstall the whole thing :-(

Ed.

---

### Post by zvacet on 2009-03-18
Try with 

```
sudo apt-get --purge remove linux-image-2.6.22-15-generic
```

---

### Post by hierogrammate on 2009-04-01
Thanks. I'll try that and see what happens.

Ed

---

### Post by hierogrammate on 2009-04-01
No luck. Same thing happened. This is what appeared in the terminal:

```

edwin@edwin-desktop:~$ sudo apt-get --purge remove linux-image-2.6.22-15-generic
[sudo] password for edwin: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
edwin@edwin-desktop:~$ sudo dpkg --configure -a
edwin@edwin-desktop:~$ sudo apt-get --purge remove linux-image-2.6.22-15-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  g++-4.1 libstdc++6-4.1-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-2.6.22-15-generic
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 63.8MB disk space will be freed.
Do you want to continue [Y/n]? 

(Reading database... 144884 files and directories correctly installed)
Removing linux-image-2.6.22-15-generic...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory... found: /boot/grub
Searching for default file... found: /boot/grub/default
Testing for an existing GRUB menu.lst file... found: /boot/grub/menu.lst
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.22-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


```

Then the computer freezes. :(

Ed

P.S. Apparently the package is never removed and nothing is really fixed in this process, since after restart the problem is still there. :(

---

### Post by hierogrammate on 2009-04-18
Only want to try to ask again one more time about this, to see if anyone can share a link or idea of what may be going on. Otherwise I'll just scrap the partition and reinstall it. :(

Thanks,

Ed

---

