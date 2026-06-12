---
title: "Laptop screen not restoring after sleep"
date: 2013-11-27
forum: Hardware
---

### Post by biswajitdey on 2013-11-27
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I have HP ProBook 4445s. I am using Ubuntu 13.04.[/COLOR]

[COLOR=#000000]Whenever I close the lid or suspend the laptop, the screen does not restore. [/COLOR]

[COLOR=#000000]The processor is on but I can't see anything on the screen.[/COLOR]

[COLOR=#000000]Please help if there is any way to fix this.[/COLOR]

[COLOR=#000000]Thanks and Regards,[/COLOR]
[COLOR=#000000]Biswajit Dey[/COLOR]

---

### Post by codenine75a on 2013-12-09
I have this problem too on a Toshiba Portege.  The laptop displays a screen but it will not recover after either a screen lock or ACPI recovery from sleep.  I suspect the ACPI code.
looking into recompiling the kernel since ACPI is in there.
Link [http://myrddin.org/howto/debian-kernel-recompiling/](http://myrddin.org/howto/debian-kernel-recompiling/)

*update 6:36a
The new kernel is compiling so I will explain what I did
[B][FONT=lucida console][COLOR=#333333]
sudo apt-get install linux-source[/COLOR]
[COLOR=#333333]cd /usr/src[/COLOR]
[COLOR=#333333]sudo tar jxvf linux-source-3.11.0.tar.bz2[/COLOR]
[COLOR=#333333]sudo ln -s linux-source-3.11.0 linux
cd linux
[/COLOR][/FONT][COLOR=#333333]
[/COLOR][COLOR=#333333][FONT=Courier New]sudo apt-get install kernel-package debhelper dpkg-dev
[/FONT][/COLOR][/B]**sudo kate Makefile**[COLOR=#333333][FONT=Segoe UI]Set EXTRAVERSION = -20131209n

I saved the file
[B]
[FONT=Courier New]sudo make oldconfig[/FONT]
[FONT=Courier New]sudo make menuconfig
[/FONT]I changed some suspected options in the menu
Power management and ACPI options --->
      [unchecked] Suspend to RAM and standby
      [checked] User space wake up sources interface (I do not know what it truly does but it states something about waking up in a user space so I selected it.)

[FONT=Courier New]sudo make-kpkg clean[/FONT][/B][/FONT][/COLOR]
[B][COLOR=#333333][FONT=Courier New]sudo time make-kpkg --initrd kernel_image

[/FONT][/COLOR][/B][FONT=Courier New][COLOR=#333333][B]I stopped there because the kernel is compiling and when I install it there may be a kernel panic.  That is when the OS freezes up and the keyboard lights flash.

*update 7:00a
Chit chat as it is compiling.  Who would mount a QNX file system or use the reiser file system?  I would not use QNX at all.  Reiser I may if I was going to run an extensive server or something that requires multiple passes over the same data on the hard drive.  That is because Reiser uses a btree algorithm for its filesystem.  The author of Reiser committed suicide and I think left reiser4.  Linux uses ext4 usually by default and it is a journalized filesystem.  I guess that means it is good for error correction and more accurate data recovery because it is journalized.

*update 11:42a
Nope that was not it.  There is a problem with the screen locker and closing the lid because it activates a screen saver when the lid is closed and the sleep option it selected.  The laptop lid options are under System Settings -> Power Management in KDE it may be the same for gnome.  I set mine to lock the screen when the lid is closed.

*update 12:38p
I believe that the lid option was for server farm terminals and not laptops.[/B][/COLOR][/FONT]

---

### Post by biswajitdey on 2014-01-29
Thanks for the reply codenine75a.

I do not wish to reinstall kernel, because I have some important setup on my current machine.

Is there a workaround to rectify the issue without reinstalling the kernel.

Help would be appreciated.

Thanks .

---

