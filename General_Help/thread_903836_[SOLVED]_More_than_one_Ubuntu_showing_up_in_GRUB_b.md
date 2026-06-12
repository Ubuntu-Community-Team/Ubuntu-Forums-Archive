---
title: "[SOLVED] More than one Ubuntu showing up in GRUB boot menu!"
date: 2008-08-28
forum: General Help
---

### Post by _Atreides_ on 2008-08-28
Hello guys, I am running a dual boot Ubuntu/Vista. The Grub menu used to contain only one Ubuntu and Vista, but now it has two Ubuntus! (Picture is Attached). Can someone kindly explain why this is happening/what I should do about it? Thanks in return!

[[IMG]http://img240.imageshack.us/img240/6707/p1010093nt3.th.jpg[/IMG]](http://img240.imageshack.us/my.php?image=p1010093nt3.jpg)

---

### Post by jespdj on 2008-08-28
That's because some time in the past you installed an update to the Linux kernel.

You can get rid of it by uninstalling the packages from the old kernel (2.6.24-16 in your case). Go to System / Administration / Synaptic Package Manager. Search for "2.6.24-16". Select all the relevant Linux packages for the old kernel that you want to uninstall, and apply.

(Be careful; don't uninstall the wrong packages, or you might screw up your system!).

---

### Post by drs305 on 2008-08-28
jespdj has it right in how to remove older kernels and removing them from the menu display.

For more information, take a look at this tutorial, it will explain it and how to safely modify the grub menu with StartUp-Manager (recommended) or manually editing menu.lst:

[Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by mb_webguy on 2008-08-28
It's the same Ubuntu, you've simply upgraded your kernel.  It's a bit like a Windows service pack, but... well, not.  The kernel, which is the core of the Linux operating system, is updated fairly regularly, and will be included in your regular Ubuntu updates.  When it is, a new entry will appear in the GRUB menu, allowing you to boot using a earlier kernel in case the new kernel causes problems (which isn't terribly common, but possible).  You can change your GRUB menu.lst to control how many of these additional kernels are displayed (or to display none, if that's what you want).

Just go into the terminal and type "gksu gedit /boot/grub/menu.lst", and look for the following lines:```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

```

Change that last line to "# howmany=1" if you only want to show one kernel in the GRUB menu.  DO NOT remove the leading hash ("#")!

Now save and exit, and type "sudo update-grub".

---

### Post by coffeecat on 2008-08-28
You can uninstall the old kernel if you want, but most people like to keep at least one old kernel in reserve to boot into in case the newest gives problems. The -16 kernel is not doing any harm there and so long as you have plenty of room on your hard drive, you might as well keep it until the -19 kernel is superseded by a twenty-somthing kernel.

---

### Post by ubunt_user on 2008-09-02
Since this post already deals with the my question I would just like to ask one more thing. I am getting a notification to update the Kernel. If I go ahead, will the new Kernel override the current GRUB.
Meaning to say that as of now I have Vista and Ubuntu (8.04) as dual boot. So after the update is complete, would I have 3 option (2 Ubuntu and 1 Vista) in GRUB or only Ubuntu options.
The reason for this question is because I have read articles/posts on net that Kernel updates (in Ubuntu) sometimes messes the GRUB. If its the case, can you also let me know in case these kind of things happen, how can I have things working correctly.

---

### Post by _Atreides_ on 2008-09-02
It will update the GRUB Menu. However, this can easily be changed again.

---

### Post by drs305 on 2008-09-02
> **ubunt_user said:**
> Since this post already deals with the my question I would just like to ask one more thing. I am getting a notification to update the Kernel. If I go ahead, will the new Kernel override the current GRUB.
Meaning to say that as of now I have Vista and Ubuntu (8.04) as dual boot. So after the update is complete, would I have 3 option (2 Ubuntu and 1 Vista) in GRUB or only Ubuntu options.
The reason for this question is because I have read articles/posts on net that Kernel updates (in Ubuntu) sometimes messes the GRUB. If its the case, can you also let me know in case these kind of things happen, how can I have things working correctly.

You should not lose you windows option. When you update the kernel, at some point it will ask if you want to keep your current settings or use new ones. If you elect to keep your current settings, the new kernel will be downloaded  and the menu will be updated to show the new kernel but the old kernel will still be running. 

At this point I would recommend you use Startup-Manager. From within SUM, you can then select which kernel or OS to use as default, even windows if you desire. You can also select how many kernels to view, although I would recommend you keep all in view until you are sure you like the new kernel update.  For instructions on how to install and run SUM, see the link in my signature line.

---

