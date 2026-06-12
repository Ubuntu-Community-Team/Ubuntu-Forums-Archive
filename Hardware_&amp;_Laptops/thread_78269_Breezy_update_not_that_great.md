---
title: "Breezy update not that great"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by pepster on 2005-10-18
Actually very disappointing so far for my HP nx8220.
Live CD will not boot. Complains about acpi. Have to boot with noacpi.

Then X will not start because of a bug in the ati drivers.

Hoary worked well on the machine, kernel,acpi and drivers. I even got the external screen working ...

-Joseph

---

### Post by OneZ on 2005-10-18
I also have a HP nx8220. When I installed Ubuntu 5.10, I got the same X-windows problem. Now, it has been fixed. You can refer the follow thread:

[http://ubuntuforums.org/showthread.php?t=74296&highlight=nx8220]("http://ubuntuforums.org/showthread.php?t=74296&highlight=nx8220")

It means:
1. Install 5.10 into nx8220, you will get the error message;
2. Do the following command,
```
apt-get install xorg-driver-fglrx
```
3. Use the xorg.conf-1 to replace /etc/X11/xorg.conf, or use fglrxconfig to generate your xorg.conf;
4. Do the following command,
```
sudo /etc/init.d/gdm restart
```
5. Now, X-window should be work.

A review also mentioned this problem. [http://distrowatch.com/dwres.php?resource=review-ubuntu]("http://distrowatch.com/dwres.php?resource=review-ubuntu")

For the ACPI, I still use the F.04 BIOS. I tried to refresh some new bioses. The ACPI always doesn't work, even thought CentOS 4.0/4.1.

---

### Post by pepster on 2005-10-18
[QUOTE=OneZ]
For the ACPI, I still use the F.04 BIOS. I tried to refresh some new bioses. The ACPI always doesn't work, even thought CentOS 4.0/4.1.[/QUOTE]

Thanks, but the above still leaves me confused. Does acpi work for you or not? and in which bios version (and how do you find the bios version under linux anyway?)

And BTW, when I tried the live CD a second time it booted with acpi. I wonder what it will do the third time.

Thanks, Joseph

---

### Post by OneZ on 2005-10-18
Th BIOS version in my nx8220 is F.04. You can check it in BIOS. It means you need press F10 after turn on the nx8220 and before login the OS. Check the item 'System Information' in BIOS.

Only F.04 bios, the linux can do the restart operation. Otherwise, the system will be stop on 'Rebooting ...'.

I never use 5.10 live cd. When I install it into nx8220, I just enter:```
linux vga=771
```.

---

### Post by pepster on 2005-10-18
I have taken the plunge and updated to the latest kernel F-0F.

Was able to boot hoary. restart works. Also was able to boot the live breezy, and after editing xorg.conf to run Gnome.

A search in bugzilla shows the X problem has not been solved for the nx8220.

acpi working. Battery icon working.

-Joseph

---

### Post by OneZ on 2005-10-18
That's great.

My nx8220 can also do the RESTART now with F.0F BIOS.

The solution for the X problem is [http://ubuntuforums.org/showthread.php?t=74296&highlight=nx8220]("http://ubuntuforums.org/showthread.php?t=74296&highlight=nx8220"). We have to fix it manually. Anyway, it works at least.

---

### Post by pepster on 2005-10-19
I will wait in the hope that the ati driver will get fixed. I just got the clone/dual monitor thingy to work in hoary - don't feel like doing it again for the fglrx.

(And Jani - 8220 laptop tester) says fonts are blurred with fglrx.

---

### Post by shute on 2005-10-19
[QUOTE=OneZ]...
3. Use the xorg.conf-1 to replace /etc/X11/xorg.conf, or use fglrxconfig to generate your xorg.conf;
...[/QUOTE]

OneZ,

I am new for Linux and have the same problem when installing ubuntu 5.10 on my nx8220.

Thank you for made it work, but what does it mean: "Use the xorg.conf-1 to replace /etc/X11/xorg.conf", and how could I do it? Could you give me some details, or recommond me some documents to read?

Shute

---

### Post by OneZ on 2005-10-19
It's not me to let it work. The solution is from [http://ubuntuforums.org/showthread.php?t=74296&highlight=nx8220]("http://ubuntuforums.org/showthread.php?t=74296&highlight=nx8220"). Please pay attention on #7 and #9 post.

1. Install 5.10 into nx8220;
2. Config the network card and confirm it works;
3. Install xorg-driver-fglrx into system;```
apt-get install xorg-driver-fglrx
```
4. Download [xorg.conf-1.bz2]("http://ubuntuforums.org/attachment.php?attachmentid=2850&d=1129200412"). Then uncompress it and replace /etc/x11/xorg.conf. ```
sudo cp xorg.conf-1 /etc/X11/xorg.conf
```
5. restart gdm.```
sudo /etc/init.d/gdm restart
```
6. In xorg.conf-1, the keyboard layout has been setup to GB 105 keys. In gnome terminal, you will get some 'wrong' char. You can modify it to US 101 keys.

---

### Post by gannis on 2005-11-29
Fine! 

That file made X work for me.
However, the FontPath was not appropriate so some apps got messed up.
And of course my swedish keybord needs "se".

By the way, this was discussed here: 
[http://www.ubuntuforums.org/showpost.php?p=457498&postcount=8](http://www.ubuntuforums.org/showpost.php?p=457498&postcount=8)

---

### Post by amp_man on 2005-12-04
Thanks, this worked perfectly for me with my HP ze2308wm (the recent wal-mart black friday laptop) \\:D/

edit: okay, so it worked for a little while....

---

### Post by S.Fart on 2005-12-27
[QUOTE=OneZ]Th BIOS version in my nx8220 is F.04. You can check it in BIOS. It means you need press F10 after turn on the nx8220 and before login the OS. Check the item 'System Information' in BIOS.

Only F.04 bios, the linux can do the restart operation. Otherwise, the system will be stop on 'Rebooting ...'.

I never use 5.10 live cd. When I install it into nx8220, I just enter:```
linux vga=771
```.[/QUOTE]

Thanks Your code just saved me. I had suse 10 on my nx8220 and was getting tired of stuff not working so i thought i would give kubuntu a try.
Already have it  on a desktop box and its rock solid and an easy install.

But i just could'nt get it to install until i used the "vga=771" code. I was wondering if any one knew what that code actually did ??

---

