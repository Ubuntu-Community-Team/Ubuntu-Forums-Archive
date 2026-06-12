---
title: "Multiple Ubuntus after Kernel upgrade"
date: 2005-11-23
forum: General Help
---

### Post by ubuntu27 on 2005-11-23
Hello. The problem I have is different from the problems that other people has. I do not get "Kernel Panic"

Yesterday at midnight, adjacent to the clock appeared a an icon similar to Jabber. And, when I clicked it, it told me that a new Kernel was installed, and that I need to restart as soon as possible.
Anyway, I restarted as it told me.

Oh yeah, on thing. I saw that people did "Apt-get distro-update" so they could update their kernel, after they were told to install it.
Funny, I didn't get any notice to download nor install a new kernel. 
It just told me that a new kernel was installed. (Automatically)

And now this is what it appears:

GNU GRUB Version 0.95 (639k lower/515048k upper memory)

Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)
Ubuntu, Kernel memtest86+

Other Operating Systems:
Windows NT/2000/XP
Windows NT/2000/XP (loader)


As you can see, now I have two options in order to start Ubuntu. It doesn’t give me a trouble, but, I guess it could be confusing. 
Is there a way to eliminate some of them?

By the way, I am having this problem AGAIN: [http://ubuntuforums.org/showthread.php?t=93652](http://ubuntuforums.org/showthread.php?t=93652)

It happens at random. :(  


Thank you in advance :)

---

### Post by installer on 2005-11-23
> **ubuntu27]Hello. The problem I have is different from the problems that other people has. I do not get "Kernel Panic"

Yesterday at midnight, adjacent to the clock appeared a an icon similar to Jabber. And, when I clicked it, it told me that a new Kernel was installed, and that I need to restart as soon as possible.
Anyway, I restarted as it told me.

Oh yeah, on thing. I saw that people did "Apt-get distro-update" so they could update their kernel, after they were told to install it.
Funny, I didn't get any notice to download nor install a new kernel. 
It just told me that a new kernel was installed. (Automatically)

And now this is what it appears:

GNU GRUB Version 0.95 (639k lower/515048k upper memory)

Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Ubuntu, kernel 2.6.12-9-386
Ubuntu, kernel 2.6.12-9-386 (recovery mode)
Ubuntu, Kernel memtest86+

Other Operating Systems:
Windows NT/2000/XP
Windows NT/2000/XP (loader)


As you can see, now I have two options in order to start Ubuntu. It doesn&#8217 said:**
> http://ubuntuforums.org/showthread.php?t=93652[/url]

It happens at random. :(  


Thank you in advance :)

Open Synaptic  you need to remove the Linux headers for kernel 2.6.12-9-386
Reboot and then re-run Synaptic and remove the residual config. 

Pretty sure this is correct but wait for somebody else to confirm.

---

### Post by sigma2805 on 2005-11-23
if you want, you can comment out those extra entries...

sudo gedit /boot/grub/menu.lst

type in your password when it asks for it and then place # signs at the beginning of each line that you want to comment out. for example, 

#title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
#root		(hd0,4)
#kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda8 ro single
#initrd		/initrd.img-2.6.12-10-386
#boot

---

### Post by ubuntu27 on 2005-11-23
Thank you **installer** for the reply.

How do I remove the residual config. ?

---

### Post by olavi on 2005-11-23
Let me ask you one thing: is this behavior (having multiple ubuntu kernels) perfectly normal?

---

### Post by installer on 2005-11-23
[QUOTE=ubuntu27]Thank you **installer** for the reply.

How do I remove the residual config. ?[/QUOTE]

Run Synaptic again and any residual configuration files from removed packages will be shown in left window, remove these items.

---

### Post by Neobuntu on 2005-11-23
If you want to get fancy, edit (sudo) /boot/grub/menu.lst (back it up first) and change the "true" selecetions to "false" WHERE you may want to reduce the item sthat are AUTOMATICALLY added to your GRUB menu with kernel image updates. I do not have recover items not memtest auto added because I don't need them. 

It's actually really cool how GRUB is updated along with ubnutu kernel updates. It can save your tale. You just have to leave your GRUB timeout setting (same file) long enough to see them (and press a key to stop the timeout.)

I hope a fix for the auto update K7 and Nvidia legacy that stops X in version 10 will be fixed soon.

---

### Post by seldenthuis on 2005-11-23
[QUOTE=olavi]Let me ask you one thing: is this behavior (having multiple ubuntu kernels) perfectly normal?[/QUOTE]

Yes, because if for some reason the new kernel doesn't work you should be able to boot the system with the old kernel.

---

### Post by ubuntu27 on 2005-11-23
[QUOTE=seldenthuis]Yes, because if for some reason the new kernel doesn't work you should be able to boot the system with the old kernel.[/QUOTE]

Glad to hear that. I was wondering the same thing as olavi. I though that maybe  there were some errord during the instalaltion og the new kernel.

BTY, talking about the new kernel, what they they improve, fixed? In one word, "What's new?"

---

### Post by sigma2805 on 2005-11-23
[QUOTE=seldenthuis]Yes, because if for some reason the new kernel doesn't work you should be able to boot the system with the old kernel.[/QUOTE]

the other thing to remember is that you booted into the previous kernel and are running it while you are installing the new kernel. Thats why it doesn't really get removed....just imagine how unstable your system would be if you remove the kernel you booted into..... :???:

---

### Post by ranf on 2005-11-24
[QUOTE=ubuntu27]
BTY, talking about the new kernel, what they they improve, fixed? In one word, "What's new?"[/QUOTE]
Look in the Security Announcements on this site.

---

### Post by sciurus on 2005-11-24
Sicne the new kernel works fine, what packages do I need to remove to actually get rid of the old, unneeded one?

linux-image-2.6.12-9-686
linux-restricted-modules-2.6.12-9-686

Anything else?

---

### Post by Mozzer on 2005-11-25
I also had this problem when I updated my kernel and I just assumed it was a silly error (e.g. "they forgot to remove the old entry on the grub menu"). But now it kinda makes sense... is it safe to remove then seeing as my new kernel is working just fine and dandy?

---

### Post by sapo on 2005-11-25
[QUOTE=Mozzer]I also had this problem when I updated my kernel and I just assumed it was a silly error (e.g. "they forgot to remove the old entry on the grub menu"). But now it kinda makes sense... is it safe to remove then seeing as my new kernel is working just fine and dandy?[/QUOTE]
yes it is, just remove the old linux-image package and the entry on menu will be removed as well :)

---

### Post by metoo on 2005-11-25
If you are unsure what kernel packages you have installed use the search function in synaptic.

Search for 2.6.12-9 or 2.6.12-9-686 and set the search type to version (not name & description).
All the packages having this version number will be listed and you can see which of them are installed.
Then uninstall them.
(right click, mark for uninstall, later in menu click proceed (de here, whatever this is in en) ).

People who have compiled a kernel/kernel module might have additional packages like the kernel sources.

---

### Post by Schmots on 2005-11-25
Wanna know how many kernels I have on my main system?  7 thats right 7.  each with little tweaks and minor changes, I recompile my kernel alot.  Why don't I delete them?  Cause there small, don't take up a lot of space and maybe some day I want to boot off them again.  Keep in mind the Kernel IS the OS, ubuntu is just a way of packaging that with a bunch of GNU programs.  A great way mind you, but thats it.  There is nothing wrong with having multiple kernels.. what if it comes out that the new kernel has some huge security hole on accident and you can't get the new one yet.. boot the old one.. as a good rule of thumb you should keep probably about 3 kernels on your system..  but hey, its linux, its up to you.

---

