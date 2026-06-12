---
title: "Additional boot option in GRUB"
date: 2008-10-15
forum: General Help
---

### Post by sink74 on 2008-10-15
I recently set up dual boots of Ubuntu on my work and home desktops.  After switching the default boot option in GRUB to Windows (spouse is not exactly ready for the switch), I found a problem once yesterday's updates were installed.

Specifically, I now have two new lines in the GRUB boot-loader for my dual boot.  The Ubuntu lines (normal and recovery) in the menu have been augmented with two other lines.  Instead of a single line like 

Ubuntu 8.04.1, kernel 2.6.24-19-generic

I now have these lines, with the associated recovery options.

Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-21-generic

Does anyone have any information about this?  I imagine I just need to change my default boot option, but what is the difference in these options?

---

### Post by Elfy on 2008-10-15
You've had a kernel update - they get added to the menu list. You could edit the file and rather than keep changing the default move the windows part so it's above all of the ubuntu options.

Backup and open the file for editing
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```


In the file there is a line which looks like this

> ### BEGIN AUTOMAGIC KERNELS LIST
Cut and paste the whole windows stanza above this line and change default to 0 again

---

### Post by sink74 on 2008-10-15
I see. Thanks.  Out of curiosity, is there a benefit to keeping multiple versions of the kernel in the boot list?

---

### Post by Sam on 2008-10-15
> **sink74 said:**
> I see. Thanks.  Out of curiosity, is there a benefit to keeping multiple versions of the kernel in the boot list?

Yes, by example, if you compile a custom kernel, you may keep an old one in case something wrong happens. Or if kernel update will bring some issue, you can easily revert to an other kernel that works.

---

### Post by Newtothegame on 2008-10-27
> **forestpixie said:**
> You've had a kernel update - they get added to the menu list. You could edit the file and rather than keep changing the default move the windows part so it's above all of the ubuntu options.

Backup and open the file for editing
```
sudo cp /boot/grub/menu.lst
gksudo gedit /boot/grub/menu.lst
```


In the file there is a line which looks like this


Cut and paste the whole windows stanza above this line and change default to 0 again

Hey Guys, 

Am still a major noob here. My comp is currently running a dual boot and with the kernal updates my login screen looks like a dos book. So i attempted to launch the file with the terminal script aboved and I get this error: "cp: missing destination file operand after `/boot/grub/menu.lst'
Try `cp --help' for more information." 

I checked the package manager and Grub is installed. What am I missing? 

-Newtothegame

---

### Post by Sam on 2008-10-27
> **Newtothegame said:**
> Hey Guys, 

Am still a major noob here. My comp is currently running a dual boot and with the kernal updates my login screen looks like a dos book. So i attempted to launch the file with the terminal script aboved and I get this error: "cp: missing destination file operand after `/boot/grub/menu.lst'
Try `cp --help' for more information." 

I checked the package manager and Grub is installed. What am I missing? 

-Newtothegame

The 'cp' command need at least two arguments, the source and the destination.```
sudo cp /boot/grub/menu.lst [COLOR="Red"]/boot/grub/menu.lst.bak[/COLOR]
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Elfy on 2008-10-27
command was missing something, it isn't now

That said unless this thread deals with your problem you shouldn't follow it, all that this thread deals with is editing the menu list not no boot after a kernel update.

You might be better served startiung a thread of your own - [http://ubuntuforums.org/showthread.php?t=726219](http://ubuntuforums.org/showthread.php?t=726219)

---

### Post by Newtothegame on 2008-10-27
> **forestpixie said:**
> command was missing something, it isn't now

That said unless this thread deals with your problem you shouldn't follow it, all that this thread deals with is editing the menu list not no boot after a kernel update.

You might be better served startiung a thread of your own - [http://ubuntuforums.org/showthread.php?t=726219](http://ubuntuforums.org/showthread.php?t=726219)


Hey thanks Forestpixie and Sam. I was being a big dramatic about the DOS book. I have about 5 boot options when it starts up and would like to clean this up a bit. 

Thanks,

-Newtothegame

---

### Post by Elfy on 2008-10-27
aaah - 

kernel
kernel recovery
kernel
kernel recovery
memtest

I'd always keep 2 sets - just in case the newest has a problem

I assumed you meant that once you booted it left you at a command prompt :)

You can edit it if you wish but if you have problems then it's not easy to get it back.

---

### Post by Newtothegame on 2008-10-27
First off, Forest your awesome for the quick responses, you to SAM. 

as for my screen it looks like a mess when it boots. I dont mind keeping a back up but it just keeps adding kernels I am up to 3 kernels 3 kernal recoverys a memtest and two xp boot options. < about to look into the xp reasoning as well> 

Anyhow, is there anyway to keep a backup, and make the new kernals update over the newest. 

Also, looking at the menu.lst it lists the names of all the kernals, is there anyway to just hide one? Can i change the boot order of xp in this as well? 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Embedded
root		(hd0,2)
savedefault
makeactive
chainloader	+1

Another issue is where do i set the value to 0 if i do decide to do the first listed option? 

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ebdfd48c-37af-46bd-8d70-e4075f7a976a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

---

### Post by Elfy on 2008-10-27
Near to the top of the file - you'll find this, it counts from 0 

> default		0

IF you have 3 kernels then you could lose 1 safely, not sure why you have 2 win ones - if you want xp to always be first then I would suggest moving it so that it is always 0 which is what post #2 is about if you need to be sure then post your menu list and someone will help - it _must_ be above the automagic line though.

If you think 3 options is too many - you wouldn't like mine, I have 12

---

