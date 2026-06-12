---
title: "Set timeout when selecting OS"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by SPARTAN-118 on 2009-07-15
Hi, I rarely use my Windows Vista in my Dual-boot configuration, so I'd like to know:

Is there a way to either increase the timeout when my BIOS auto-selects Vista, or can I move Ubuntu to the top of the installed OS's?

I don't think it has to do with GRUB, since it's before I select Ubuntu, not when it says "Press ESC to return to menu. [Timeout#]"

I want to make it so Ubuntu either is at the top of the auto-selection list, or the timeout till auto-select is at least 20 seconds. 10 seconds, the default, is too short, as sometimes I'm distracted with something that demands my immediate attention. Then, I have to wait till Windows starts up, click the "Restart" button on the Logon Screen, and THEN  select Ubuntu.

That is really time-consuming, when I'm in a rush and just want to search something on Google, for instance, so is there a way to lengthen the time-out? Or bump Ubuntu to the top of the list?

Thanks,
SPARTAN-118

---

### Post by raymondh on 2009-07-15
> **SPARTAN-118 said:**
> Hi, I rarely use my Windows Vista in my Dual-boot configuration, so I'd like to know:

Is there a way to either increase the timeout when my BIOS auto-selects Vista, or can I move Ubuntu to the top of the installed OS's?

I don't think it has to do with GRUB, since it's before I select Ubuntu, not when it says "Press ESC to return to menu. [Timeout#]"

I want to make it so Ubuntu either is at the top of the auto-selection list, or the timeout till auto-select is at least 20 seconds. 10 seconds, the default, is too short, as sometimes I'm distracted with something that demands my immediate attention. Then, I have to wait till Windows starts up, click the "Restart" button on the Logon Screen, and THEN  select Ubuntu.

That is really time-consuming, when I'm in a rush and just want to search something on Google, for instance, so is there a way to lengthen the time-out? Or bump Ubuntu to the top of the list?

Thanks,
SPARTAN-118


Hello Spartan,

2 ways.

Edit the /boot/grub/menu.lst  to reflect your preferences..... or, if you're lazy like me today :), install (thru synaptic or terminal or add/remove) **startupmanager**, a GUI based program/app.  Once installed, access it from system > administration and set defaults (as well as others) there.  SUM also writes to the menu.lst.

reference material for reading:

[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Happy Ubuntu-ing.

---

### Post by SPARTAN-118 on 2009-07-16
Thanks, raymondhenson, I think that did the trick.

I opted to install the GUI, StartUp-Manager, since I prefer to see visual confirmation of what I do.

Besides, I've already had to re-install Ubuntu twice. I don't want to accidentally mess up my system because I accidentally deleted one line.

I'd rather use a program for that ;)

SPARTAN-118

---

### Post by raymondh on 2009-07-16
> **SPARTAN-118 said:**
> Thanks, raymondhenson, I think that did the trick.

I opted to install the GUI, StartUp-Manager, since I prefer to see visual confirmation of what I do.

Besides, I've already had to re-install Ubuntu twice. I don't want to accidentally mess up my system because I accidentally deleted one line.

I'd rather use a program for that ;)

SPARTAN-118

Good job and congratulations.

Here's a link from Herman's site.  It's about GRUB and what you can do to it by editing.  It's  good reading .....Herman's an excellent teacher and writer ... and should you need a solid reference/guide when you decide to get under the hood again and edit manually.

[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)

As a fellow UF member/friend once told me .... "if you learn to use the terminal, you can even make a commodore 64 run".  :)  

Try it someday.  No need to worry if you make a back-up copy of your original boot/grub/menu.lst.

Happy Ubuntu-ing.

EDIT :  I know enough to realize I need to learn much more.

---

### Post by SPARTAN-118 on 2009-07-16
Don't congratulate me yet...

While I managed to change the timeout for when Ubuntu is selected (increasing it from 3 seconds), that's not what I meant to do in the first place.

What I need to do is increase the timeout at the Operating System selection menu.

It looks something like this:

> You may now select your Operating System.
[INDENT]
[LIST]
[*]**[COLOR=Black]Windows Vista ([#] seconds until timeout)[/COLOR]**
[*]Ubuntu
[/LIST]
Press F8 for Advanced Options for this OS.[/INDENT]The Advanced Options don't have anything to do with the timeout, and GRUB only starts up *after* you select Ubuntu.

So, how do I change the timeout for when Windows Vista is selected? On the logo screen, when my computer starts up and the Toshiba and Intel logos are displayed, pressing F2 for Setup doesn't work, sine the timeout is separate from Setup.
Pressing TAB at the OS select screen only highlights the "Windows Memory Diagnostics Tool" option.

Like I said in my original post, I badly need to increase the timeout, or otherwise make Ubuntu the default OS the auto-select picks. StartUp-Manager doesn't do anything for this; only for GRUB, which is *after* you select Ubuntu.

I appreciate your help, but it seems like I need more! :mrgreen:

SPARTAN-118

---

### Post by raymondh on 2009-07-16
Is this a WUBI-installed Ubuntu? Which bootlader are you using?  

I ask because GRUB is a bootloader that allows you to choose between OS' and comes up ***before*** booting any OS.  Startupmanager writes to the /boot/grub/menu.lst which controls what actions GRUB will take.

See attachment.  I have set up windows as the default OS and it will take 100 secs. before it boots up windows.

A quick trick (while we figure this out) is to stop the time-out.  I normally (while the time is running down) press the spacebar.

---

### Post by SPARTAN-118 on 2009-07-16
Oh I didn't know that Windows Vista (Loader) meant that.

And yes, it is a WUBI install.

SPARTAN-118

Oh, and I just *had *to share this with you, since us Linux-ers use the Terminal so much...

LOL Oh, the irony!

---

### Post by raymondh on 2009-07-16
> **SPARTAN-118 said:**
> Oh I didn't know that Windows Vista (Loader) meant that.


So, is the timeout problem solved?  (while we're thinking about the keyboard problem):confused:

---

### Post by SPARTAN-118 on 2009-07-17
I am such an idiot.

You know what selecting "Windows Vista (Loader)" did?

Now, when I select Ubuntu, it just loads the menu again!

I'd like to know:

HOW CAN I RECOVER UBUNTU?!?!?!!?

Please, I can't lose all my files!

Darn it, I should have set up a backup routine and backed up my files to Windows earlier....

If I can't recover Ubuntu, can I at least recover my files? Isn't there software for WUBI installations that allows you to access Ubuntu's files? Some of my files I don't care about *that* much (though I'd still be upset to lose them), while others it took hours to download!

*Please,* help me!
:(SPARTAN-118

---

### Post by raymondh on 2009-07-17
> **SPARTAN-118 said:**
> I am such an idiot.

I should never have listened to you.

You know what selecting "Windows Vista (Loader)" did?

Now, when I select Ubuntu, it just loads the menu again!

So, raymond, I'd like to know:

HOW CAN I RECOVER UBUNTU?!?!?!!?

Please, I can't lose all my files!

Darn it, I should have set up a backup routine and backed up my files to Windows earlier....


HOW COULD YOU NOT WARN ME?!?!!?

If I can't recover Ubuntu, can I at least recover my files? Isn't there software for WUBI installations that allows you to access Ubuntu's files? Some of my files I don't care about *that* much (though I'd still be upset to lose them), while others it took hours to download!

*Please,* help me!
:(SPARTAN-118

Cool it, Spartan-118!

It being a WUBI install and ubuntu **BEING INSIDE windows ... your files are still INSIDE WINDOWS**.  See the [wiki]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?") for a how-to.

You asked for a way to delay the boot process to give you time.  I offered you 2 options and you decided to install startupmanager. I showed you a visual example that you can delay Vista as much as 100 secs. and even hinted that by pressing the spacebar, you can stop the timer. Only then (when asked) did you inform that it was a WUBI install

Read the wiki and proceed from there.

---

### Post by SPARTAN-118 on 2009-07-17
> **raymondhenson said:**
> Cool it, Spartan-118!

It being a WUBI install and ubuntu **BEING INSIDE windows ... your files are still INSIDE WINDOWS**.  See the [wiki]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?") for a how-to.

You asked for a way to delay the boot process to give you time.  I offered you 2 options and you decided to install startupmanager. I showed you a visual example that you can delay Vista as much as 100 secs. and even hinted that by pressing the spacebar, you can stop the timer. Only then (when asked) did you inform that it was a WUBI install

Read the wiki and proceed from there.

Sorry, I was just really depressed.

If you can just tell me what portion of the boot_menu.lst says which OS to boot, I'm sure I can fix it.

Since you can access boot_menu.lst from the LiveCD (in Windows' C:\ubuntu\disks\boot_menu.lst), can't I just edit it? 

I think I'm ready to get under the hood now ;)

Oh, and BTW, the Wiki, do I run those commands from the LiveCD's "try Ubuntu without installing" Terminal?

SPARTAN-118

---

### Post by raymondh on 2009-07-17
Spartan118,

No worries ... we all (you and I and others) have bad days.

Why not back-up first those files before editing.  That way, you can throw wubi "into-the-wind" if you make a mistake editing.

I am dual-booting (not a WUBI install).  Here is my boot/grub/menu.lst.  Again, this is GRUB ... not the boot.ini file of windows.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=10e85b73-beb7-4239-aa09-9f764551a01c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

Among the first 15 lines, notice the line DEFAULT   0 ?  That means that my Ubuntu (and top kernel) will load as GRUB will load by default Ubuntu.  If I wanted windows to default, I would put the appropriate number depending on where windows is. In my case, '6' because GRUB counts from ZERO and I have 2 kernels with recovery modes plus Memtest plus the line "other operating system".

In your case, you use the windows bootloader and will only access grub after you choose Ubuntu.  Unfortunately (now we know) we placed windows bootloader as the default action for GRUB....hence the loop-back into windows.

Check what is the default in the GRUB menu.lst.  Try to put 0 and see what happens.  Post back any error, no joy or success.

Some reading references:

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)
[http://www.stchman.com/grub_menu.html](http://www.stchman.com/grub_menu.html)

Good luck.

---

### Post by SPARTAN-118 on 2009-07-17
> **raymondhenson said:**
> Spartan118,

No worries ... we all (you and I and others) have bad days.

Why not back-up first those files before editing.  That way, you can throw wubi "into-the-wind" if you make a mistake editing.

I am dual-booting (not a WUBI install).  Here is my boot/grub/menu.lst.  Again, this is GRUB ... not the boot.ini file of windows.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=10e85b73-beb7-4239-aa09-9f764551a01c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        10e85b73-beb7-4239-aa09-9f764551a01c
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        10e85b73-beb7-4239-aa09-9f764551a01c
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        10e85b73-beb7-4239-aa09-9f764551a01c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        10e85b73-beb7-4239-aa09-9f764551a01c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        10e85b73-beb7-4239-aa09-9f764551a01c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```Among the first 15 lines, notice the line DEFAULT   0 ?  That means that my Ubuntu (and top kernel) will load as GRUB will load by default Ubuntu.  If I wanted windows to default, I would put the appropriate number depending on where windows is. In my case, '6' because GRUB counts from ZERO and I have 2 kernels with recovery modes plus the line "other operating system".

In your case, you use the windows bootloader and will only access grub after you choose Ubuntu.  Unfortunately (now we know) we placed windows bootloader as the default action for GRUB....hence the loop-back into windows.

Check what is the default in the GRUB menu.lst.  Try to put 0 and see what happens.  Post back any error, no joy or success.

Some reading references:

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)
[http://www.stchman.com/grub_menu.html](http://www.stchman.com/grub_menu.html)

Good luck.

Yay! It worked! :D

Actually, what I did was the first thing I *should* have done:

replace menu.lst with menu.lst.backup

LOL can't believe I missed that....

But you helped me understand my problem better!

menu.lst.backup's default was 0, as well as a 3-sec timeout, which I don't mind at all, since I rarely boot Ubuntu with the intention of booting Windows (after all, Windows *is* first. ;))

I deleted menu.lst after I changed the backup's name, and I also moved the [new? old?] menu.lst to a backup folder on Windows (appropriately named ubuntu-backup, located within C:\)

Any other precautions I should take?

SPARTAN-118

---

### Post by raymondh on 2009-07-17
> **SPARTAN-118 said:**
> Yay! It worked! :D

Actually, what I did was the first thing I *should* have done:

replace menu.lst with menu.lst.backup

LOL can't believe I missed that....

But you helped me understand my problem better!

menu.lst.backup's default was 0, as well as a 3-sec timeout, which I don't mind at all, since I rarely boot Ubuntu with the intention of booting Windows (after all, Windows *is* first. ;))

I deleted menu.lst after I changed the backup's name, and I also moved the [new? old?] menu.lst to a backup folder on Windows (appropriately named ubuntu-backup, located within C:\)

Any other precautions I should take?

SPARTAN-118

Well done Spartan118.

Now, is the keyboard working (from the previous post')?

Also, are we still looking on how to delay Vista from booting up ... aside from hitting the spacebar to stop the countdown?

Back up those personal files so you are neither dependent on any OS.

Congratulations.

---

### Post by raymondh on 2009-07-17
Also, now that you can boot back into Ubuntu ... check startupmanager to see what the default OS is. Just check to  **Make sure it is Ubuntu** *(and not windows bootloader)* or else we fall back to the same dilemna again.  If unsure, post back before editing.

PS. Backup those files (......sounding like a broken record :) )

---

### Post by SPARTAN-118 on 2009-07-17
LOL, about the keyboard thing...

It was just a funny Avatar I found while searching for my "Linux Spartan".

Anyway, I think I'll take a look around for Windows Bootloader editors...
Assuming, of course, you can't edit the bootloader from Ubuntu?

And yes, the default is "0", or Ubuntu 9.04.

Unfortunately, I can't back up my files (as of this moment) because I (this may sound pathetic) can't afford an External HDD. I know a 1 TB EHDD can be found at Best Buy for around $160 CAN, but I have my priorities in other areas at the moment.
And I don't feel like buying 50 CDs to backup onto... Unless the backup program can automatically spread it out, so I don't have to manually drag-n-drop every file I own?

Thanks for your help,
SPARTAN-118

---

