---
title: "Ubuntu auto-updating to kernel 2.6.28-13"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by jpaisneto on 2009-06-19
Hello!

I used update manager and it updated my 2.6.28-11 kernel (with jaunty) to 2.6.28-13. Was this supposed to happen? And now I have to decide which kernel to boot with, because they both appear on grub! Shouldn't the other one be removed?

Thank you,
João

---

### Post by bryonak on 2009-06-19
Always use the newest kernel, which should be selected by default.
Such upgradees usually bring a few minor (and often non-noticable) improvements.

---

### Post by jpaisneto on 2009-06-19
> **bryonak said:**
> Always use the newest kernel, which should be selected by default.
Such upgradees usually bring a few minor (and often non-noticable) improvements.

So, why do I still have the old kernel version on grub? Wouldn't my pc become unstable with the newest kernel? I didn't know Ubuntu would update the kernel until Karmic...

---

### Post by gradinaruvasile on 2009-06-19
Be warned though: 
If u have installed proprietary video drivers like the ones on Nvidias site, they may have to be reinstalled (i at least had to reinstall them every time the kernel was upgraded). 
Also compiled/installed third party apps/games may crash on such occasions.

Its quite a turnoff (it happened to me also) to see that the X crashes/apps crash for no apparent reason. Or worse, it wont boot at all. Im speaking from experience.

I think Ubuntu should show some warnings/info for the users when doing kernel upgrades. People have the habit to launch the default grub option you know. If that doesnt work...

---

### Post by bryonak on 2009-06-19
> **jpaisneto said:**
> So, why do I still have the old kernel version on grub? Wouldn't my pc become unstable with the newest kernel? I didn't know Ubuntu would update the kernel until Karmic...

All the kernels are left in the menu, so you can choose if you want to use very specific options. After a few months, you usually get quite a list...
These 2.6.28-XX are just minor bugfixes and not supposed to be unstable. For example the 2.6.31 kernel is already in production, maybe 2.6.32 will be included in Ubuntu 9.10.

If you want to clean up the menu list, press Alt+F2 and type ```
gksudo gedit /boot/grub/menu.lst
```
There scroll down, where you can delete all the entries you don't like. Just make sure one is left, so you have a boot option. You can also rename the "title" attribute to whatever you like.
Additionally, there's an option somewhere in the middle to set how many boot entries should be showed, which you can set to 1.

[color=red]EDIT: *But caution, think well before making such changes. A typing error can render your system temporarily unbootable, which isn't hard to fix but requires effort.*[/color]


> **gradinaruvasile said:**
> Be warned though: 
If u have installed proprietary video drivers like the ones on Nvidias site, they may have to be reinstalled (i at least had to reinstall them every time the kernel was upgraded). 
Also compiled/installed third party apps/games may crash on such occasions.


Personally I've never had to reinstall my graphics drivers on a minor kernel update... on a major one sure, but those don't occur in-between.
Maybe that's because I use the proprietary nvidia drivers from the repository... there's quite a difference between "blessed" repository programs and self-compiled ones, but I wouldn't recommend compiling things for new users anyway.

---

### Post by ptn107 on 2009-06-19
When a new kernel is installed there is absolutely no reason not to keep at least one of the older ones.

---

### Post by jpaisneto on 2009-06-19
> **gradinaruvasile said:**
> Be warned though: 
If u have installed proprietary video drivers like the ones on Nvidias site, they may have to be reinstalled (i at least had to reinstall them every time the kernel was upgraded). 
Also compiled/installed third party apps/games may crash on such occasions.

Its quite a turnoff (it happened to me also) to see that the X crashes/apps crash for no apparent reason. Or worse, it wont boot at all. Im speaking from experience.

I think Ubuntu should show some warnings/info for the users when doing kernel upgrades. People have the habit to launch the default grub option you know. If that doesnt work...

I install my NVidia drivers with "Hardware Drivers" and I noticed during the installation that it was checking if I already had the latest driver.

---

### Post by jpaisneto on 2009-06-19
> **bryonak said:**
> All the kernels are left in the menu, so you can choose if you want to use very specific options. After a few months, you usually get quite a list...
These 2.6.28-XX are just minor bugfixes and not supposed to be unstable. For example the 2.6.31 kernel is already in production, maybe 2.6.32 will be included in Ubuntu 9.10.

If you want to clean up the menu list, press Alt+F2 and type ```
gksudo gedit /boot/grub/menu.lst
```There scroll down, where you can delete all the entries you don't like. Just make sure one is left, so you have a boot option. You can also rename the "title" attribute to whatever you like.
Additionally, there's an option somewhere in the middle to set how many boot entries should be showed, which you can set to 1.

[COLOR=red]EDIT: *But caution, think well before making such changes. A typing error can render your system temporarily unbootable, which isn't hard to fix but requires effort.*[/COLOR]




Personally I've never had to reinstall my graphics drivers on a minor kernel update... on a major one sure, but those don't occur in-between.
Maybe that's because I use the proprietary nvidia drivers from the repository... there's quite a difference between "blessed" repository programs and self-compiled ones, but I wouldn't recommend compiling things for new users anyway.

Do you think I should update my kernel to the latest version? I don't need it to be extremely stable, I think I can handle some (small) bugs. How would that improve my system?

---

### Post by jpaisneto on 2009-06-19
> **ptn107 said:**
> When a new kernel is installed there is absolutely no reason not to keep at least one of the older ones.

If I remove the older kernel am I removing it? So I shouldn't remove it, right? It doesn't take a lot of space, does it?

---

### Post by raymondh on 2009-06-19
> **jpaisneto said:**
> Hello!

I used update manager and it updated my 2.6.28-11 kernel (with jaunty) to 2.6.28-13. Was this supposed to happen? And now I have to decide which kernel to boot with, because they both appear on grub! Shouldn't the other one be removed?

Thank you,
João


Hello Joao,

May I offer a different approach?

Download thru terminal or synaptic 'startupmanager'.

Access it from system > administration

Use it to set boot options (i.e.  which kernel to boot, how long, etc) and advanced options (for hiding/limiting kernels to be shown, etc).

Startupmanager also writes to your menu.lst ... which means you can also edit your menu.lst should you prefer not to install this GUI (SUM).

I always try to keep 2 kernels.  That way, if the latest is borky, I can then resort to using the older, tested, tweaked kernel.

Just a different approach to consider....

Good luck,

---

### Post by jpaisneto on 2009-06-19
> **raymondhenson said:**
> Hello Joao,

May I offer a different approach?

Download thru terminal or synaptic 'startupmanager'.

Access it from system > administration

Use it to set boot options (i.e.  which kernel to boot, how long, etc) and advanced options (for hiding/limiting kernels to be shown, etc).

Startupmanager also writes to your menu.lst ... which means you can also edit your menu.lst should you prefer not to install this GUI (SUM).

I always try to keep 2 kernels.  That way, if the latest is borky, I can then resort to using the older, tested, tweaked kernel.

Just a different approach to consider....

Good luck,


As I only have 2 kernels, maybe it's a good idea to keep both, right? But if I remove one of them later, I'll try that program, it seems easier :D

Thank you!

---

### Post by raymondh on 2009-06-19
> **jpaisneto said:**
> As I only have 2 kernels, maybe it's a good idea to keep both, right? But if I remove one of them later, I'll try that program, it seems easier :D

Thank you!

Sure, it's always a good idea to have a spare :)  BTW, startupmanager does NOT remove kernels.  It just hides them from you....should you decide and until you decide otherewise....and make life simpler (view-wise).

Happy Ubuntu-ing.

---

### Post by jpaisneto on 2009-06-19
> **raymondhenson said:**
> Sure, it's always a good idea to have a spare :)  BTW, startupmanager does NOT remove kernels.  It just hides them from you....should you decide and until you decide otherewise....and make life simpler (view-wise).

Happy Ubuntu-ing.

Thank you :p

It only removes it from grub's list, right? Could anyone tell me how to **remove** a kernel? Like, if I install a newer kernel the older ones become useless, I can keep one as backup, but I don't need 3 or 4, do I? Thank you all :D

---

### Post by markbuntu on 2009-06-19
No, you do not need a bunch of kernels lying around but, unless you are pressed for space, there is also no need to remove them. If you do want to remove them you can do so with the Synaptic package manager but be very very careful.

---

### Post by jpaisneto on 2009-06-20
> **markbuntu said:**
> No, you do not need a bunch of kernels lying around but, unless you are pressed for space, there is also no need to remove them. If you do want to remove them you can do so with the Synaptic package manager but be very very careful.

Ok, thanks.

Do you think I should update to the latest kernel version? What are the advantages and disadvantages?

---

### Post by drs305 on 2009-06-20
jpaisneto, welcome to the Ubuntu forums. 

StartUp-Manager is a pretty easy way to change menu.lst settings and also kernel displays in the menu. The following guide explains a lot about what happens when a new kernel is released and your various options for displaying and/or removing older ones.

Here is the link:
[https://help.ubuntu.com/community/StartUpManager]("https://help.ubuntu.com/community/StartUpManager")  (Wiki)

[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")  Ubuntu Forums thread


StartUp-Manager is a great tool for use with grub (Grub Legacy). It is not quite as good with Grub 2, as many of the options are not yet available.

---

### Post by jpaisneto on 2009-06-20
> **drs305 said:**
> jpaisneto, welcome to the Ubuntu forums. 

StartUp-Manager is a pretty easy way to change menu.lst settings and also kernel displays in the menu. The following guide explains a lot about what happens when a new kernel is released and your various options for displaying and/or removing older ones.

Here is the link:
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)  (Wiki)

[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)  Ubuntu Forums thread


StartUp-Manager is a great tool for use with grub (Grub Legacy). It is not quite as good with Grub 2, as many of the options are not yet available.


Ok, thank you. It's the same program raymondhenson told me to use. But thanks for the links, they were really helpful. But can't anybody tell me if it is recommended to update to the latest kernel, or if that's even possible :confused:

Thank you for all your answers!

---

### Post by drs305 on 2009-06-20
> **jpaisneto said:**
> Ok, thank you. It's the same program raymondhenson told me to use. But thanks for the links, they were really helpful. But can't anybody tell me if it is recommended to update to the latest kernel, or if that's even possible :confused:

Thank you for all your answers!

You can select the new kernel during boot and see if you have any problems. If you don't, you could use StartUp-Manager to set it as the default OS. If you have problems, just reboot and select the older kernel. 

If you don't see the menu during boot, you can press the ESC key to show the grub menu and make your selection.

To set which kernel to use as the default, open StartUp-Manager and select the kernel in the Boot Options tab. SUM also has an option which decides whether to automatically use a new kernel as soon as it's installed (on next boot) or to continue to use the older kernel until you change it manually (via SUM or editing menu.lst manually).

To see which kernel is actually running, you can run this command:
```

uname -r

```

---

### Post by jpaisneto on 2009-06-20
> **drs305 said:**
> You can select the new kernel during boot and see if you have any problems. If you don't, you could use StartUp-Manager to set it as the default OS. If you have problems, just reboot and select the older kernel. 

If you don't see the menu during boot, you can press the ESC key to show the grub menu and make your selection.

To set which kernel to use as the default, open StartUp-Manager and select the kernel in the Boot Options tab. SUM also has an option which decides whether to automatically use a new kernel as soon as it's installed (on next boot) or to continue to use the older kernel until you change it manually (via SUM or editing menu.lst manually).

To see which kernel is actually running, you can run this command:
```

uname -r

```

Thank you, but that's not what I'm asking. Like, Jaunty uses kernel 2.6.28 and the latest stable kernel is 2.6.30, right?

I wanted to know if it's possible/recommended to update from 2.6.28 to 2.6.30, to fix bugs and improve performance, etc.

I hope I made myself clear. Thanks.

---

### Post by raymondh on 2009-06-20
> **jpaisneto said:**
> Ok, thank you. It's the same program raymondhenson told me to use. But thanks for the links, they were really helpful. But can't anybody tell me if it is recommended to update to the latest kernel, or if that's even possible :confused:

Thank you for all your answers!

Joao,

Kernels always come with fixes for problems that were recognized as troublesome in the previous kernel/s.  Newer kernels also bring (what we hope) more stability, maturity and general improvements. In those regard, yes it is **my** advantage to upgrade to the lates kernel.  I believe that the more tests done on a kernel, the better.

However, I also recognize that newer kernel versions may not include the drivers that made my system function (when I was using the older kernel) .... which means more work/tweaking for me.  Is is stressfull work?  Not when I have the old one standing by :)

Here's a link on improvements of kernels. It may give you an idea of what happens (or is included) in a newer kernel.

[http://www.ibm.com/developerworks/linux/library/l-dev26/](http://www.ibm.com/developerworks/linux/library/l-dev26/)
[http://www.linuxhq.com/index.html](http://www.linuxhq.com/index.html)

---

### Post by jpaisneto on 2009-06-21
> **raymondhenson said:**
> Joao,

Kernels always come with fixes for problems that were recognized as troublesome in the previous kernel/s.  Newer kernels also bring (what we hope) more stability, maturity and general improvements. In those regard, yes it is **my** advantage to upgrade to the lates kernel.  I believe that the more tests done on a kernel, the better.

However, I also recognize that newer kernel versions may not include the drivers that made my system function (when I was using the older kernel) .... which means more work/tweaking for me.  Is is stressfull work?  Not when I have the old one standing by :)

Here's a link on improvements of kernels. It may give you an idea of what happens (or is included) in a newer kernel.

[http://www.ibm.com/developerworks/linux/library/l-dev26/](http://www.ibm.com/developerworks/linux/library/l-dev26/)
[http://www.linuxhq.com/index.html](http://www.linuxhq.com/index.html)


Thanks, I'm using KernelCheck to update the kernel. I hope I'm doing it correctly xD

I'm waiting for Karmic Alpha 3, maybe then I'll install it... Is it stable enough already?

I removed the older kernel, I'm not sure why (maybe it was because apt-get autoremove removed the older kernel headers, or because I installed Nvidia drivers from the official site, I'm not sure) but it wasn't working well. So I uninstalled it :|

---

### Post by raymondh on 2009-06-21
> **jpaisneto said:**
> Thanks, I'm using KernelCheck to update the kernel. I hope I'm doing it correctly xD

I'm waiting for Karmic Alpha 3, maybe then I'll install it... Is it stable enough already?

I removed the older kernel, I'm not sure why (maybe it was because apt-get autoremove removed the older kernel headers, or because I installed Nvidia drivers from the official site, I'm not sure) but it wasn't working well. So I uninstalled it :|

Karmic is still in testing stage.... and I don't know if it may work "out-of-the-box" as it all depends on how your system specs will react to/with the changes. That is why I always have the older (already tweaked) kernel as standby.

Nevertheless, congratulations.  And, if you need assistance in tweaking your new kernel, the UF is only a power-button and browser away :)

---

### Post by jpaisneto on 2009-06-21
> **raymondhenson said:**
> Karmic is still in testing stage.... and I don't know if it may work "out-of-the-box" as it all depends on how your system specs will react to/with the changes. That is why I always have the older (already tweaked) kernel as standby.

Nevertheless, congratulations.  And, if you need assistance in tweaking your new kernel, the UF is only a power-button and browser away :)

Now I understand the community support thing, you're all great! Thanks a lot!

I think being unstable is one of the best things in Linux, it makes us learn so much!

When Karmic Alpha 3 comes out I'll maybe try it, I won't install it now because I think there's something wrong with booting with grub :)

Thank you :D

---

### Post by raymondh on 2009-06-21
> **jpaisneto said:**
> Now I understand the community support thing, you're all great! Thanks a lot!

I think being unstable is one of the best things in Linux, it makes us learn so much!

When Karmic Alpha 3 comes out I'll maybe try it, I won't install it now because I think there's something wrong with booting with grub :)

Thank you :D

And you are most welcome.

Happy Ubuntu-ing.

---

### Post by jpaisneto on 2009-06-21
> **raymondhenson said:**
> And you are most welcome.

Happy Ubuntu-ing.

Thank you :)

---

### Post by FatherDale on 2009-06-22
> **ptn107 said:**
> When a new kernel is installed there is absolutely no reason not to keep at least one of the older ones.

Agreed. If something breaks, I want the last kernel as a backup. In Ubuntu, I've had to use this one time, and that one time made me glad I did that. :D

---

