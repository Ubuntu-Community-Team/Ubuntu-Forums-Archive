---
title: "Installing 9.04 Server under Microsoft Virtual Server 2005 R2"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by benutne on 2009-05-14
What should be fairly straightforward, doesn't seem to be.  Just grabbed the 32 bit version of 9.04 Server Edition and mounted it to a vanilla virtual machine using a virtual IDE disk.  I get to the point right after I choose the language and it asks whatn I want to do (install, test memory, test CD, etc.) and as soon as I hit enter on the "Install" option, "Test CD for defects", or "Rescue a Broken System" a bunch of text scrolls by and I'm stuck.  The installer seems to crash.  Anyone experienced anything like this?  I'm just trying to throw together a quick LAMP server to test some software out and figured a VM was the way to go.

---

### Post by jespdj on 2009-05-14
Try using [VirtualBox](http://www.virtualbox.org) instead of Microsoft Virtual Server.

---

### Post by benutne on 2009-05-14
> **jespdj said:**
> Try using [VirtualBox](http://www.virtualbox.org) instead of Microsoft Virtual Server.

IF that is my only option, I'll give it a shot but I've already got MVS2005 installed and several virtual machines running under it.  Thanks for the fast reply.

---

### Post by jingram076 on 2009-06-05
I've successfully installed version 8.04 LTS Server in Virtual Server 2005 R2.  Please check my blog out at [http://askcts.blogspot.com](http://askcts.blogspot.com) and rep my most recent blog.  Here's how to do it:
 
These instructions assume that you know how to use VI Editor.  If you don't [here ]("http://www.atmos.albany.edu/deas/atmclasses/atm350/vi_cheat_sheet.pdf")is a cheat sheet.  There are a number of things that need to be noted when attempting an Ubuntu 8.04 Server install as a guest using Microsoft Virtual Server 2005 R2, as follows: 
**Stage 1 - Boot options for the Install **

In order to commence the "Install from CD" after booting the 8.04 Server CD, you must add the boot options vga=771 (or vga=791) and noreplace-paravirt. 
 [B] Example:   --/boot/vmlinuz-2.6.24-18-generic root=UUID-XXXXXXXXXXX ro quiet splash vga=771 noreplace-paravirt-- 
[/B]The vga option will allow you to see stuff as VS2005 is a bit odd with video, and the noreplace-paravirt stops the install kernel from constantly rebooting the machine! 
**Stage 2 - Post-Installation, Replacing the "server" kernel with "generic" kernel **

The default kernel that is installed with 8.04 Server is the linux-2.6.24-16-server kernel - but since this has been optimized for i686 CPU's, it seems (to me anyway) that this will NEVER RUN under MS VS 2005 R2 (all you get is a critical "BUG: Int 6: CR2 00000000" freeze) - so the solution is to replace the "server" kernel with the "generic" kernel which is not optimised only for i686 CPU instruction sets and works in VS2005. 

To install the generic kernel, I found this was best done at the very last step of the Installation process - DO NOT choose "Continue" to reboot, instead choose "Go Back" and then choose the menu option that gives you a terminal. 
In the terminal at the end of the installation process (be careful the following assumes you've configured networking and the virtual machine has internet access which it should if you completed those steps during the installation), do the following: [B]
    #> chroot /target /bin/bash    #> aptitude install linux-generic    #> aptitude remove linux-server linux-image-server linux-image-2.6.24-16-server linux-ubuntu-modules-2.6.24-16-server    #> exit[/B]
Staying in the terminal, it is now wise to edit the grub menu to add the boot options to the generic kernel so that it will start correctly (yes, the same boot options as the install CD); you do it like this: [B]
    #> nano /target/boot/grub/menu.lst[/B]
Look for the lines similar to below, and add the boot options (i.e. vga=771 noreplace-paravirt) at the end of the kernel line. [B]
    title Ubuntu 8.04, kernel 2.6.24-18-generic    root (hd0,0)    kernel /boot/vmlinuz-2.6.24-18-generic root=UUID-XXXXXXXXXXX ro quiet splash vga=771 noreplace-paravirt    ..[/B]Then we chroot back into the target and update the grub menu like this: [B]
    #> chroot /target /bin/bash    #> update-grub    #> exit[/B]
And exit the Terminal to return to the Installation menu options, by typing: [B]
    #> exit[/B]
Then select "Finish the Installation" and choose "Continue" to reboot. 
Once the OS boots, log in and type in the following command prompt: [B]
    #> cd ../..     #> cd boot/grub    #> sudo vi menu.lst [/B]
Comment out out all ubuntu-server kernals, do not comment out the ubuntu-generic kernals. To save your changes: [B]
    Shift + z + z[/B]

---

### Post by benutne on 2009-06-05
Very interesting.  I'll see if I can get that working.  Thanks for the post.

---

### Post by jingram076 on 2009-06-09
Were you able to get it to work?

---

### Post by under_dog on 2009-10-15
Hi ... I've been having problems getting Ubuntu 9.04 to work under Virtual Server 2005. When I try:

[B]   #> aptitude install linux-generic

[/B]"Couldn't find any package whose name or description matched 'linux-generic'"

Is that package name correct?

---

