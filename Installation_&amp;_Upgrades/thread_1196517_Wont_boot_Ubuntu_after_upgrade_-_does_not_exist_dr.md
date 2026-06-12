---
title: "Wont boot Ubuntu after upgrade - does not exist dropping to a shell"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by sincityharley on 2009-06-25
[SIZE=2]Boot from (hd0,4) ext3 75c68421-23d8-4504-88b3-d7582cfd8fb1[/SIZE]
[SIZE=2]Starting up ...[/SIZE]
[SIZE=2]Loading, please wait...[/SIZE]
[SIZE=2]Check [COLOR=black]cryptopts[/COLOR]=source= bootarg cat /proc/cmdline[/SIZE]
[SIZE=2]or missing modules, devices: cat /prod/modules ls /dev[/SIZE]
[SIZE=2]-r ALERT /dev/disk/by-uuid/8861ed01-c9f3-439f-8e11-b3d7da35e683 does not exist.[/SIZE]
[SIZE=2]Dropping to a shell![/SIZE] 
 
Above is what I got after Ubuntu told me that there was an update/upgrade available. I did the update and after a reboot this is what I got. It now gives me a prompt with (initramfs) I am not sure what any of this means. I do have a lot of data that I really need off my install or I would have just wiped and reinstalled. I googled this message and there is quite a bit out there with regards to others getting the same message but nothing out there with regards to showing a beignner how to resolve. I could really use some help on this one. Please be gentle with instructions. Im not so hot with linux yet but I am great at following directions. Also I encrypted my entire HD with luks when I did the original install, not sure if that matters.

---

### Post by sincityharley on 2009-06-27
I have spent all night trying to find an answer with no luck. In trying to fix my origianal issue I have now broken my computer further with a Grub Loading : Error 15. I figure I am screwed at this point. I am assuming that nobody know how to fix my situation. Since thats the case would anyone be able to tell me how to at least get my data off the drive so that I can format it and do a fresh install? Thanks

---

### Post by sincityharley on 2009-06-27
So here's a question. If I boot up with the Live CD is there a way that I can access my data thats actually on my hard drive? What do I have to run to do that. When booted with my live cd i only see a user Ubuntu. Where as when my computer worked normally I have a few different users under the home folder.

---

### Post by sincityharley on 2009-06-27
I am still working on this issue. Today I pulled my Ubuntu hard drive out and hooked it up to my hard drive adapter. I plugged it in via via usb to another ubuntu machine and it show that there is only a 255mb partition with only lost+found on it. I plugged it into a windows machine and its shows the same 255 and also shows the rest of the drive as healthy. The rest of the drive is in accessable I am assuming due to the fact that I have it encrypted. Can anyone please tell me how to get my data off the drive???

---

