---
title: "Need Help mouting USB ntfs storage 11.04/64bit"
date: 2011-08-05
forum: Hardware
---

### Post by Davekyn on 2011-08-05
My head is mush ... have installed Ubuntu 11.04 / 64 bit.
Have managed to get wireless card going after some issues, tweaked my sound so that it does not hiss and done a few other things that have left me completely drained........OMG.....why oh why am I doing this.

I told my friend I like a challenge!!!!!!!!!!!!!!!

So after working out how to mount my NTFS storage drive that I use in windows all the time, I need to be able to some how mount my sata USB dock that I use for all my SATA drives laying about the place.

could someone please lead me through this process.

I have manged to set up ntfs config ... but cant seem to get any response when hooking up my USB sata Dock

Thank You
Dave ;)

---

### Post by coffeecat on 2011-08-05
> **Davekyn said:**
> 
So after working out how to mount my NTFS storage drive that I use in windows all the time, I need to be able to some how mount my sata USB dock that I use for all my SATA drives laying about the place.

could someone please lead me through this process.

Put the SATA drive in the dock, plug the USB cable in, switch the dock on and wait a few seconds. The partition(s) will automount and a file browser window will open. Or at least that is what should happen. However....

> **Davekyn said:**
> I have manged to set up ntfs config ... but cant seem to get any response when hooking up my USB sata Dock


There are several 3rd-party apps in the repos that purport to help with drive mounting but which often cause more problems that they solve. Often because they have not been maintained for years. ntfs-config is one. Another is usbmount, which is not intended for GUIs. Have you, by chance, installed usbmount? And what have you done in ntfs-config to try to get SATA drives working?

Please confirm that your SATA drives indeed do not automount, and then we can investigate.

By the way, welcome to Ubuntu. I have a feeling that you might be making things more difficult for yourself than need be. Using ntfs-config to automount an internal NTFS partitions might be an example. If you needed the partition mounted on bootup, I can understand why you did that. But did you know that all you had to do was to open a Nautilus (file browser - equivalent to Windows Explorer) window and click on the partition where it is listed in the left pane?

---

### Post by Davekyn on 2011-08-06
Thanks Coffeecat, I am absolutely tired now ... I have no idea and must say despite many claims that Ubuntu is easy to use, I am finding it rather difficult.
I run a small home business repairing PCs and have done so for many years now. I started out in the days of the 286/386 and so on ... mind you windows based.
It's not a competition or anything, and in fact I pretty much ignore such bantering ...what I am getting at, is that if I struggle with Ubuntu, then its no wonder that many of my family and friends also find it very hard to learn.
Generally things are easy once you know how ... until someone reaches that point, its easy to over complicate things...lol...I have no idea what your talking about at his point.

I don't mind learning though and will take my time later. Just wanted to thank you for your response and perhaps look for some kind of reasoning as to why I am going through all this, when I have a perfectly running version of Windows 7 on the side. All be it inferior and full a leaks ... but for me ... not a problem.

I look forward to learning more about Ubutnu.
will post later ... going to play some Chess for now :)

---

### Post by Basher101 on 2011-08-06
All i can say is stick to ubuntu, you wont regret it! I also had my troubles, just to get it installed...i had backlight issues on bootup and could not even see a thing at first^^ I think i learned in that one month using ubuntu more about my computer than the past 10 years using windows. I am still amazed at how i can still discover new things to learn, just looking at all the varieties of linux, all the distros almost gets me hyped, im simply overwhelmed by so much possibilities of linux that windows could never give me. I simply LOVE it.
ps: Can't way until school starts. I did all the learning and using ubuntu linux during summer break. That makes me the only linux user in my whole school :-)

---

### Post by coffeecat on 2011-08-06
> **Davekyn said:**
> will post later

When you do, open a Nautilus (file browser) window - opening your home folder will be fine - click on "File System" in the left pane. Now open the /etc folder, scroll down to find the file called fstab and open it by double-clicking on it. It will open read-only in a text editor. Please copy and past that text between [noparse]```
 and 
```[/noparse] tags. The /etc/fstab file is used by the system for partition and device mounting. It is possible that ntfs-config has made a mess of it, or has created a line which is interfering with the udev-based automounting of external drives. We need to see the contents of /etc/fstab to exclude this possibility or to correct the error if it has occurred.

Apologies for forgetting to suggest this first time around.

Also, you didn't say whether or not you have installed the package usbmount. Many people install this in a mistaken believe that it will help. If you have installed it, uninstall it.

---

