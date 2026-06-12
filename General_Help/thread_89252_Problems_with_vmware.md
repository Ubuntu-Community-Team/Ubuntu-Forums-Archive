---
title: "Problems with vmware"
date: 2005-11-12
forum: General Help
---

### Post by dotinmouth on 2005-11-12
Hello

I'm trying to install vmware but i have problems. On of them is the version of gcc, but i resolve it with a link to the older version of gcc (gcc-3.4).  When i installed i hadn't any problem, but when i run vmware-config.pl as sudo, begin a new installation of vmware, and when it finish i can't run vmware. Vmware still says that i have to run vmware-config.pl. I try again but sudo is block. What can i do?


P.D. Sorry for my english

---

### Post by linuxbz on 2005-11-12
I did the same thing and got the same results. I had VMware working fine in Hoary.

---

### Post by jaddison on 2005-11-15
[QUOTE=dotinmouth]I'm trying to install vmware but i have problems. On of them is the version of gcc, but i resolve it with a link to the older version of gcc (gcc-3.4).  When i installed i hadn't any problem, but when i run vmware-config.pl as sudo, begin a new installation of vmware, and when it finish i can't run vmware. Vmware still says that i have to run vmware-config.pl. I try again but sudo is block. What can i do?[/QUOTE]

I am running into this issue as well.  Not only that, when I try to run 'sudo vmware-config.pl' again, sudo acts as though it is frozen.  I can't Ctrl-C either (to break out of the process).

Any subsequent usage of sudo, for any command, results in the same 'frozen' behaviour.  The UI still works fine, but no sudo command will work.  Package managers fail to start up as well (Synaptic, etc.)

I hope there's help our there!

---

### Post by krye on 2005-11-15
I had the same problem, and I'm really sorry, but I don't remember how I did to get it working correctly :$

Let me check my logs...

edit: oops, I deleted all my logs, sorry. But I'm pretty sure I managed to install it with the help of these forums, maybe a search?

---

### Post by jaddison on 2005-11-15
[QUOTE=jaddison]I am running into this issue as well.  Not only that, when I try to run 'sudo vmware-config.pl' again, sudo acts as though it is frozen.  I can't Ctrl-C either (to break out of the process).

Any subsequent usage of sudo, for any command, results in the same 'frozen' behaviour.  The UI still works fine, but no sudo command will work.  Package managers fail to start up as well (Synaptic, etc.)

I hope there's help our there![/QUOTE]

Ok, one of two problems solved - in the /etc/vmware directory, there is an empty file called 'not_configured'.  Rename, move or delete that file, and VMWare will start just fine.  I think I may be having networking trouble in my VMWare images, but the OSes start just fine.

The 'sudo' problem, described above is still outstanding though.  Has anyone had trouble with sudo freezing?

Thanks,

---

### Post by haTem on 2005-11-15
[QUOTE=jaddison]Ok, one of two problems solved - in the /etc/vmware directory, there is an empty file called 'not_configured'.  Rename, move or delete that file, and VMWare will start just fine.  I think I may be having networking trouble in my VMWare images, but the OSes start just fine.

The 'sudo' problem, described above is still outstanding though.  Has anyone had trouble with sudo freezing?

Thanks,[/QUOTE]

I am having this sudo problem as well and it is VERY annoying. I just reinstalled breezy because of it, but upon attempting to configure vmware again the problem  resurfaced. 

There is a note on the wiki about it, but it seems to be refering to people upgrading from hoary to breezy and is not clear on how to fix it. ([https://wiki.ubuntu.com/InstallingVMWare](https://wiki.ubuntu.com/InstallingVMWare) at the bottom of the page)

Please! If you know the solution to this problem, your posting it would be greatly appreciated :D.

---

### Post by haTem on 2005-11-15
After doing a bit more searching, I came across this thread:

[http://ubuntuforums.org/showthread.php?t=88124&highlight=sudo+vmware](http://ubuntuforums.org/showthread.php?t=88124&highlight=sudo+vmware)

I was not able to restart my network services (it would hang) but a reboot fixed it. I uninstalled vmware, and will be giving vmware-player a try (since I have already created my Virtual Machine with vmware).

Hopefully this will fix it for you too!

- haTem

---

### Post by jaddison on 2005-11-17
[QUOTE=haTem]After doing a bit more searching, I came across this thread:

[http://ubuntuforums.org/showthread.php?t=88124&highlight=sudo+vmware](http://ubuntuforums.org/showthread.php?t=88124&highlight=sudo+vmware)

I was not able to restart my network services (it would hang) but a reboot fixed it. I uninstalled vmware, and will be giving vmware-player a try (since I have already created my Virtual Machine with vmware).

Hopefully this will fix it for you too!

- haTem[/QUOTE]

I too removed VMWare 5 and everything returned to normal.  I've never seen that issue before with VMWare - it's always been a stable product for me.  Oh well.

VMWare player is all right for existing images, but since you can't even revert using it, it was rendered kind of useless for me.  (unless you can revert, and I am just too dumb to figure out why!)

Thanks for the input,

---

### Post by Yoda_Oz on 2005-11-17
I installed vmware with help from this thread:

[http://ubuntuforums.org/showpost.php?p=460713&postcount=8]("http://ubuntuforums.org/showpost.php?p=460713&postcount=8")

Pay particular attention to this post by Souki that mentions a French website. Don't go to the website though. Just follow the translated instructions Souki has given.

I installed vmware 5.5 beta using this howto. it works perfectly, although i cant seem to get the installed windows to recognise my usb drive. it wants to install drivers but it doesnt need them! stupid windows!

HOPE THIS HELPS...

---

### Post by dretep on 2005-11-22
Thank you!  I was finally able to get VMware 5.0 working after reading your post.

---

### Post by patrickfromspain on 2005-11-24
Hi there!

I've just installed the 30 day evaluation version of VMWARE 5.5. The first time I tried to install it it failed because of incorrect kernel headers. Downloaed the correct one and install went pefect until The modules perfectly fit into your kernel or something similar to that. After that, a couple of messages came out (I think starting vmware). After that the system looked up completely. I had to hard reboot... But no success in rebooting. It went all fine until the GDM login screen should appear. There the system completely froze again.

I don't know where I should start looking at.. no idea at all. I'm glad about having many kernels jeje.

Thanx!

---

### Post by Yoda_Oz on 2005-11-24
sorry, can't help you there... i dont know much about kernels.

are you sure its the kernel and not your xserver playing up? have you tried booting up into a terminal instead of the gdm?

---

### Post by patrickfromspain on 2005-11-25
thanks for replying. It's already solved. Today I've booted my computer into the k7 kernel... and went fine. I have run vmware config and all went ok. I can now start using it.

---

### Post by Yoda_Oz on 2005-11-25
i hate when people say their problem is solved but they dont explain how they solved it.
many a time i've gone into a forum looking for an answer to something ive been struggling with and a forum poster has had the EXACT same problem as me. suddenly they come up with a reply to say "dont worry now, ive solved the problem" without any explanation as to how they solved it...

so, patrickfromspain, how did you solve it?

sorry, guys... lack of sleep makes me a bit 'on edge' to say the least.

---

