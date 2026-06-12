---
title: "Toshiba A665 Laptop -- Illuminated Backlit Keyboard"
date: 2010-07-18
forum: Hardware
---

### Post by flbiggs on 2010-07-18
I installed Lucid on my new laptop, a Toshiba A665.  Everything seems to work very will right out of the box.  The only very minor issue I have run into is that I cannot figure out how to get the illuminated backlit keyboard to work.  It works fine under the native windows installation,and works fine through the Grub bootloader selection menu.  However, a few seconds after the laptop starts to install Ubuntu, the backlighting turns off.  The keyboard button (Fn-Z) does not turn it back on.  It is not the end of the world, but I kind of like the feature.  Anyone have any ideas?  Thanks

---

### Post by BritishEmperor on 2010-07-18
Hello !!

Check this out. It's aimed at Macbook Pro but I reckon you might be abled to get some info out of this. It's got some details regarding control of keyboard backlit LEDs through the use of an ambient light sensor, but if you ignore that it might be of some use.

[https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Keyboard](https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Keyboard)

Hope this helps.

---

### Post by k5wlf on 2010-07-18
Hi all,

I'm having the same problem. Mine's not a dual-boot install, Ubuntu 10.04 only. The KB lights up during POST, but goes off as soon as Linux starts to load. Nothing will bring it back. I went into the BIOS and set the KB lighting to 'Always On', but that was no help either.

Like the OP said, it's not a deal-breaker, but I was counting on being able to use the feature in dim/no light situations. All info appreciated.

TNX,
ldb
K5WLF

---

### Post by Aeling on 2010-08-06
Bump, same problem. Satellite A660, backlight works up until it starts booting. Fn-Z doesn't work. Any ideas?

---

### Post by piotao on 2010-10-12
bump, the same for me

Toshiba A665-3DV, lit is on when in BIOS, Windows, disabled while ubuntu10.10

---

### Post by al_agha20 on 2010-10-22
hey same problem here i have Toshiba satellite a665-s6067
when the system starts all the light goes off and when i put two fingers on the touch pad the mouse starts to jump crazy from place to place !!! any one can help ?

---

### Post by twopointfour on 2010-10-26
Bump. I just got a brand new Toshiba Satellite M645-S4080, but the backlit keyboard isn't working at all in Ubuntu. It works fine in Windows. I've searched the forums but can't find anything. Any help?

---

### Post by Deecie on 2010-10-26
Same problem on my A660. There's nothing that seems appropriate anywhere in /sys. Seems like it might be a driver thing.

---

### Post by Cigarmaster01 on 2010-10-26
Anybody knows what would be the best online place to buy a Toshiba A665? Any suggestion will be highly appreciate it.
Cheers!

---

### Post by twopointfour on 2010-10-27
I've been scouring the internet and it doesn't seem like anyone has gotten these Toshiba backlit keyboards working in linux yet. It might be helpful to identify what the actual hardware we have in common is. You can get a list of attached PCI cards by opening a terminal and typing lspci, and you can get a list of USB devices attached by typing lsusb. 

When I don't have any USB devices plugged in and type lsusb, here's my list:

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0930:0214 Toshiba Corp. 
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It's just a guess, but I think that "04f2:b1d6 Chicony Electronics Co., Ltd" is this backlit keyboard. None of my PCI hardware seems to fit it, and when I search for Chicony I find this badly-designed company website: [http://www.chicony.com.tw/](http://www.chicony.com.tw/) -- it appears that they make mobile keyboards. Does everyone else have that piece of hardware when they do an lsusb?

---

### Post by Zibeb on 2010-10-27
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0930:0214 Toshiba Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 064e:a216 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:1292 Apple, Inc. iPhone 3G
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Toshiba A660D-ST2G02 on this end, no chicony here.

---

### Post by Cigarmaster01 on 2010-10-29
Indeed...[http://www.chicony.com.tw/](http://www.chicony.com.tw/) sucks... :mad:

---

### Post by uplinked on 2010-10-29
Bump. Toshiba Satellite A665D, Karmic, no "Chicony" in lsusb.

I took a look in /sys/class/leds and found one device (mmc::) which doesn't seem to control anything (echo "255" | tee mmc::/brightness), was hoping to at least be able to manually control the brightness from here.

---

### Post by Zasekamoz-v on 2010-10-30
I have same problem with keyboard backlight on Toshiba Satellite A665-11T.
As far as i know Chicony usb device is web camera and /sys/class/mmc:: has something to do with Multi Media Card.

lsusb:
Bus 002 Device 003: ID 0955:0007 NVidia Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0930:0214 Toshiba Corp. 
Bus 001 Device 004: ID 1164:0871 YUAN High-Tech Development Co., Ltd 
Bus 001 Device 003: ID 0bda:58f2 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

LCD brightness dont work either. 
I treid Fn+F6/F7 and nothing, then i moved slider for LCD brightness in ubuntu power manager and now i can change britness from totaly black to about max 60% of full LCD brightness (slider is on 100%).

---

### Post by Zasekamoz-v on 2010-10-31
If ACPI is disabled in kernel boot line, the keyboard backlight work. Even Fn+y key combination work - to enable/disable backlight. 
The problem with ACPI disabled is that anything other then keyboard backlight, sound volume and mute don't work and OS can't detect all 8 cores (4*2 hiperthreaded).

Can anyone please tell me how can i configure/enable all 8 cpu cores with ACPI disabled?

---

### Post by Cigarmaster01 on 2010-11-02
Just got an HP....:popcorn: ....

---

### Post by Zibeb on 2010-11-05
Mark that as another success for disabling ACPI... Sadly, that breaks the touchpad switch, the ATI Display driver (for the ATI Radeon 5650) and a few other important things. Is there a way to disable ACPI's control over the keyboard, but still run with other things?

---

### Post by whytenoiz on 2010-11-13
Any progress on this issue? A665-S6093 here with same issue. The rest of the machine definitely agrees with Ubuntu Maverick, however. Just this single annoyance.

---

### Post by whitethunder922 on 2010-11-30
Same issue on Toshiba Satellite M645. Disabling ACPI gets the backlight working but breaks display brightness control and suspend.

---

### Post by al_agha20 on 2010-11-30
Disabling ACPI works perfectly fine on my laptop :)

---

### Post by JoeGoalie on 2010-12-19
My M645-S4080 is a lovely machine that runs 10.10 beautifully but, I'm having this one issue as well.  I'm not sure I want to risk disabling ACPI (mainly because I don't know what it is) if it is going to potentially turn off other useful stuff.

---

### Post by calgarc on 2010-12-23
your answer is in he bios... that is how i got mine working... but i eventually disabled it to save battery haha:D

---

### Post by Deecie on 2011-01-02
Are you able to explain how you actually used the BIOS to enable it? Was it by disabling ACPI (this didn't work for me)? Or some other method? May I ask what specific Satellite model you have?

---

### Post by luapyeltrah on 2011-01-26
I have an A665-6065 and had the same issue where the keyboard is not backlit and the controls near the power button don't work.  I recently installed Windows 7 on my computer in a dual-boot configuration, and I discovered that if I suspend my current Windows session and reboot into Ubuntu, the keyboard is backlit and the controls are working!  If I shut down Windows and reboot into Ubuntu, the keyboard isn't backlit and the controls don't work.  I can only speculate about this "phenomenon" although I suspect it's BIOS-related....?

---

### Post by mirza_farid on 2011-02-28
same problem on A665-S6093
wireless and backlight don't work:(

---

### Post by mirza_farid on 2011-03-01
nobody don't know how to solve it!!!
plz help me:(
my wired connection works but my wireless doesn't work!!!
atleast give me a link for ubuntu A665-S6093 driver

---

### Post by clytle374 on 2011-03-10
There is a guy that has done a lot of reverse engineering on toshiba laptop's acpi. 


Anyone want to go in on bribing the guy to fix this???

Thanks
Cory

---

### Post by MadCabbit on 2011-03-16
The stock A665-S6093 wireless is a Realtek RTL8188CE (lspci identifies it as a Realtek 8176).  Its not in the kernel, but Realtek has source on their website.  You need to have your current kernel source or headers installed (Ubuntu has headers installed by default).  Go to [http://www.realtek.com/](http://www.realtek.com/) to get the source.  Don't try searching in the main search box, you won't find anything.  Click on Downloads at the top, then type RTL8188CE in the Search Downloads box on the middle left to get the linux source.  Then all you need to do is untar, open up terminal and cd into the directory, then do "make" then "sudo make install", followed by a reboot, or just do "sudo modprobe rtl8192ce_pci" and it should start picking up wireless networks immediately.  Keep in mind that since this is not in the kernel natively, you'll have to do this every time a software update pulls in a new kernel.

---

### Post by SkekTek on 2011-03-18
For whatever it's worth I have a A665D-S5175 (AMI BIOS 1.2) with the same issue.  

ACPI disabled:  illuminated keyboard and touch panel illumination work perfectly but I lose battery information as well as other ACPI benefits.

ACPI enabled: everthing works except for keyboard and touch panel illumination.

It is probably just one pesky value in the ACPI table :(

EDIT: This bug has been reported [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683133](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683133). You should vote if it effects you. Hopefully it will get more attention and resolved faster.

---

### Post by pierreyy on 2011-07-11
is there a linux distro that supports the kb backlight.... if there is maybe we can start from there...(no clue if there is or not)

---

### Post by JoeGoalie on 2011-07-11
> **pierreyy said:**
> is there a linux distro that supports the kb backlight.... if there is maybe we can start from there...(no clue if there is or not)
 I don't know, I gave up on it.  The issues with the optimus drivers, the keyboard, and for whatever reason the cooling fan would spin up to max randomly for seemingly no reason.  I'm back on Win 7 for this machine.  Next laptop I'm going to have to do a bit more research next time.

---

### Post by twopointfour on 2011-07-11
> **pierreyy said:**
> is there a linux distro that supports the kb backlight.... if there is maybe we can start from there...(no clue if there is or not)

It looks like this is a Linux kernel issue that Ubuntu has offloaded onto the Linux project: [https://bugs.launchpad.net/linux/+bug/683133](https://bugs.launchpad.net/linux/+bug/683133)

Here's the bug on kernel.org: [https://bugzilla.kernel.org/show_bug.cgi?id=32742](https://bugzilla.kernel.org/show_bug.cgi?id=32742)

Which means that currently there are no Linux distros that support it, and there won't be until this bug is fixed. And in both bug trackers this bug is marked as low priority. Which I guess it is. I don't *need* my fancy backlit keyboard, but it sure would be cool. So I wouldn't hold your breath on getting it fixed unless you find a kernel hacker (or are a kernel hacker) to hire to fix it for you.

---

### Post by pierreyy on 2011-07-12
I agree that its not a high priority issue but does anyone know of a kernel hacker on the forum... its highly unlikely tha there isnt... anw im gunna keep lookin around.... Btw given that the kb backlite works on windows perfectly... can we copy smthn off the windows kernel? the mac related post a few pages ago didnt do anything for me... anyone has a clue what to do now?? thanks for ur support guys!

---

### Post by pierreyy on 2011-07-22
You know what, im done with this! i dont want the backlite anymore(well yh i do but u know)im just gunna get a candle and put that next to the goddamn keyboard!(im always open for new ideas)

---

### Post by hydrox24 on 2011-07-23
It's fair enough that some have decided to give this thread and issue up (that's their choice) but I also have a Toshiba satellite a660 and would really like a solution to this problem. The apple threads solution did nothing for me and I couldn't find anything other than screen brightness settings in the folders in the general area around the one specified in the apple thread. I think that a few things should be established at this point:
[LIST=1]
[*]acpi is what is causing the problem
[*]there is nothing to do with keyboard brightness in the /sys/class/leds/ area
[*]keyboard backlighting works up until ubuntu/linux is loaded (AKA it works in BIOS and grub)
[/LIST]

I am not a kernel hacker, far from it :D but I will look into some of the solutions posted for other laptop makes and see if we can do some sort of port.
Any help is appreciated, including keyboard make for toshibas, good pages of info on ACPI and any links to other helpful clues/sources.

Keep up the good work guys, I think we can really get somewhere with this thread.  :)

---

### Post by pierreyy on 2011-07-24
> **hydrox24 said:**
> It's fair enough that some have decided to give this thread and issue up (that's their choice) but I also have a Toshiba satellite a660 and would really like a solution to this problem. The apple threads solution did nothing for me and I couldn't find anything other than screen brightness settings in the folders in the general area around the one specified in the apple thread. I think that a few things should be established at this point:
[LIST=1]
[*]acpi is what is causing the problem
[*]there is nothing to do with keyboard brightness in the /sys/class/leds/ area
[*]keyboard backlighting works up until ubuntu/linux is loaded (AKA it works in BIOS and grub)
[/LIST]

I am not a kernel hacker, far from it :D but I will look into some of the solutions posted for other laptop makes and see if we can do some sort of port.
Any help is appreciated, including keyboard make for toshibas, good pages of info on ACPI and any links to other helpful clues/sources.

Keep up the good work guys, I think we can really get somewhere with this thread.  :)



i was looking around and found this post on an archlinux forum... in the quote he says that his backlite is working with ubuntu... did i misinterpret it or is it supported fot sony?

  [https://bbs.archlinux.org/viewtopic.php?id=121566](https://bbs.archlinux.org/viewtopic.php?id=121566)

  its good to see the thread is still goin.

---

### Post by pierreyy on 2011-07-24
Im looking around thwe web abd turns out that on certain asus laptops the backlight works
[https://launchpad.net/asus-keyboard-backlight](https://launchpad.net/asus-keyboard-backlight)
  on the bottom odf this page theres the code for the kbd light maybe itll give us some insight.
Also this could give us something to look into.( it doesnt work on toshiba    [http://forums.linuxmint.com/viewtopic.php?f=49&t=63815](http://forums.linuxmint.com/viewtopic.php?f=49&t=63815) )


so far ive  tested  
ubuntu 11.04
knoppix 6.2
puppy 5.2
backtrack 5 
 none of them read the kbd.

---

### Post by pierreyy on 2011-07-26
thread dead.....again

---

### Post by clytle374 on 2011-08-03
Good news and bad news.  I just rebooted this machine from windows and suddenly noticed that the keyboard back light was working. I couldn't do the FN-Zto toggle it on/off, but it came on with a keypress and stayed on for about 10 seconds. Having heard of such things, I shutdown and restarted, and it still works :) That is the good news.

Bad news is I gave up on Ubuntu this spring after having other acpi issues combined with all the package managing mess with kernel builds and went back to Gentoo. Not sure what package fixed it, but here is the upgrade log if any of you Ubuntu folks wish to chase it.

>  uname -a
Linux Cassandra-Laptop 2.6.38-gentoo-r4 #3 SMP Wed Jul 20 20:56:23 EDT 2011 x86_64 AMD Phenom(tm) II P920 Quad-Core Processor AuthenticAMD GNU/Linux


```
1311209132: Started emerge on: Jul 20, 2011 20:45:32
1311209132:  *** emerge  sys-fs/udisks
1311209137:  >>> emerge (1 of 1) sys-fs/udisks-1.0.3-r1 to /
1311209137:  === (1 of 1) Cleaning (sys-fs/udisks-1.0.3-r1::/mnt/nfs_portage/sys-fs/udisks/udisks-1.0.3-r1.ebuild)
1311209139:  === (1 of 1) Compiling/Merging (sys-fs/udisks-1.0.3-r1::/mnt/nfs_portage/sys-fs/udisks/udisks-1.0.3-r1.ebuild)
1311209171:  === (1 of 1) Merging (sys-fs/udisks-1.0.3-r1::/mnt/nfs_portage/sys-fs/udisks/udisks-1.0.3-r1.ebuild)
1311209172:  >>> AUTOCLEAN: sys-fs/udisks:0
1311209172:  === Unmerging... (sys-fs/udisks-1.0.3-r1)
1311209174:  >>> unmerge success: sys-fs/udisks-1.0.3-r1
1311209175:  === (1 of 1) Post-Build Cleaning (sys-fs/udisks-1.0.3-r1::/mnt/nfs_portage/sys-fs/udisks/udisks-1.0.3-r1.ebuild)
1311209175:  ::: completed emerge (1 of 1) sys-fs/udisks-1.0.3-r1 to /
1311209175:  *** Finished. Cleaning up...
1311209176:  *** exiting successfully.
1311209176:  *** terminating.
1311209913: Started emerge on: Jul 20, 2011 20:58:33
1311209913:  *** emerge  xf86-input-keyboard xf86-input-mouse xf86-input-evdev
1311209918:  >>> emerge (1 of 3) x11-drivers/xf86-input-keyboard-1.6.0 to /
1311209918:  === (1 of 3) Cleaning (x11-drivers/xf86-input-keyboard-1.6.0::/mnt/nfs_portage/x11-drivers/xf86-input-keyboard/xf86-input-keyboard-1.6.0.ebuild)
1311209940:  === (1 of 3) Compiling/Merging (x11-drivers/xf86-input-keyboard-1.6.0::/mnt/nfs_portage/x11-drivers/xf86-input-keyboard/xf86-input-keyboard-1.6.0.ebuild)
1311209957:  === (1 of 3) Merging (x11-drivers/xf86-input-keyboard-1.6.0::/mnt/nfs_portage/x11-drivers/xf86-input-keyboard/xf86-input-keyboard-1.6.0.ebuild)
1311209958:  >>> AUTOCLEAN: x11-drivers/xf86-input-keyboard:0
1311209960:  === (1 of 3) Updating world file (x11-drivers/xf86-input-keyboard-1.6.0)
1311209960:  === (1 of 3) Post-Build Cleaning (x11-drivers/xf86-input-keyboard-1.6.0::/mnt/nfs_portage/x11-drivers/xf86-input-keyboard/xf86-input-keyboard-1.6.0.ebuild)
1311209960:  ::: completed emerge (1 of 3) x11-drivers/xf86-input-keyboard-1.6.0 to /
1311209960:  >>> emerge (2 of 3) x11-drivers/xf86-input-mouse-1.7.0 to /
1311209960:  === (2 of 3) Cleaning (x11-drivers/xf86-input-mouse-1.7.0::/mnt/nfs_portage/x11-drivers/xf86-input-mouse/xf86-input-mouse-1.7.0.ebuild)
1311209960:  === (2 of 3) Compiling/Merging (x11-drivers/xf86-input-mouse-1.7.0::/mnt/nfs_portage/x11-drivers/xf86-input-mouse/xf86-input-mouse-1.7.0.ebuild)
1311209978:  === (2 of 3) Merging (x11-drivers/xf86-input-mouse-1.7.0::/mnt/nfs_portage/x11-drivers/xf86-input-mouse/xf86-input-mouse-1.7.0.ebuild)
1311209979:  >>> AUTOCLEAN: x11-drivers/xf86-input-mouse:0
1311209980:  === (2 of 3) Updating world file (x11-drivers/xf86-input-mouse-1.7.0)
1311209980:  === (2 of 3) Post-Build Cleaning (x11-drivers/xf86-input-mouse-1.7.0::/mnt/nfs_portage/x11-drivers/xf86-input-mouse/xf86-input-mouse-1.7.0.ebuild)
1311209980:  ::: completed emerge (2 of 3) x11-drivers/xf86-input-mouse-1.7.0 to /
1311209980:  >>> emerge (3 of 3) x11-drivers/xf86-input-evdev-2.6.0 to /
1311209980:  === (3 of 3) Cleaning (x11-drivers/xf86-input-evdev-2.6.0::/mnt/nfs_portage/x11-drivers/xf86-input-evdev/xf86-input-evdev-2.6.0.ebuild)
1311209981:  === (3 of 3) Compiling/Merging (x11-drivers/xf86-input-evdev-2.6.0::/mnt/nfs_portage/x11-drivers/xf86-input-evdev/xf86-input-evdev-2.6.0.ebuild)
1311210000:  === (3 of 3) Merging (x11-drivers/xf86-input-evdev-2.6.0::/mnt/nfs_portage/x11-drivers/xf86-input-evdev/xf86-input-evdev-2.6.0.ebuild)
1311210001:  >>> AUTOCLEAN: x11-drivers/xf86-input-evdev:0
1311210001:  === Unmerging... (x11-drivers/xf86-input-evdev-2.6.0)
1311210002:  >>> unmerge success: x11-drivers/xf86-input-evdev-2.6.0
1311210003:  === (3 of 3) Updating world file (x11-drivers/xf86-input-evdev-2.6.0)
1311210003:  === (3 of 3) Post-Build Cleaning (x11-drivers/xf86-input-evdev-2.6.0::/mnt/nfs_portage/x11-drivers/xf86-input-evdev/xf86-input-evdev-2.6.0.ebuild)
1311210003:  ::: completed emerge (3 of 3) x11-drivers/xf86-input-evdev-2.6.0 to /
1311210003:  *** Finished. Cleaning up...
1311210004:  *** exiting successfully.
1311210005:  *** terminating.
1311210387: Started emerge on: Jul 20, 2011 21:06:27
1311210387:  *** emerge --oneshot --nodeps =net-wireless/rtl8192se-2.6.0019.1207.2010 =x11-drivers/ati-drivers-11.6
1311210398:  >>> emerge (1 of 2) net-wireless/rtl8192se-2.6.0019.1207.2010 to /
1311210399:  === (1 of 2) Cleaning (net-wireless/rtl8192se-2.6.0019.1207.2010::/mnt/nfs_portage/net-wireless/rtl8192se/rtl8192se-2.6.0019.1207.2010.ebuild)
1311210408:  === (1 of 2) Compiling/Merging (net-wireless/rtl8192se-2.6.0019.1207.2010::/mnt/nfs_portage/net-wireless/rtl8192se/rtl8192se-2.6.0019.1207.2010.ebuild)
1311210460:  === (1 of 2) Merging (net-wireless/rtl8192se-2.6.0019.1207.2010::/mnt/nfs_portage/net-wireless/rtl8192se/rtl8192se-2.6.0019.1207.2010.ebuild)
1311210461:  >>> AUTOCLEAN: net-wireless/rtl8192se:0
1311210461:  === Unmerging... (net-wireless/rtl8192se-2.6.0019.1207.2010)
1311210465:  >>> unmerge success: net-wireless/rtl8192se-2.6.0019.1207.2010
1311210466:  === (1 of 2) Post-Build Cleaning (net-wireless/rtl8192se-2.6.0019.1207.2010::/mnt/nfs_portage/net-wireless/rtl8192se/rtl8192se-2.6.0019.1207.2010.ebuild)
1311210466:  ::: completed emerge (1 of 2) net-wireless/rtl8192se-2.6.0019.1207.2010 to /
1311210466:  >>> emerge (2 of 2) x11-drivers/ati-drivers-11.6 to /
1311210466:  === (2 of 2) Cleaning (x11-drivers/ati-drivers-11.6::/mnt/nfs_portage/x11-drivers/ati-drivers/ati-drivers-11.6.ebuild)
1311210474:  === (2 of 2) Compiling/Merging (x11-drivers/ati-drivers-11.6::/mnt/nfs_portage/x11-drivers/ati-drivers/ati-drivers-11.6.ebuild)
1311210502:  === (2 of 2) Merging (x11-drivers/ati-drivers-11.6::/mnt/nfs_portage/x11-drivers/ati-drivers/ati-drivers-11.6.ebuild)
1311210504:  >>> AUTOCLEAN: x11-drivers/ati-drivers:1
1311210504:  === Unmerging... (x11-drivers/ati-drivers-11.6)
1311210510:  >>> unmerge success: x11-drivers/ati-drivers-11.6
1311210513:  === (2 of 2) Post-Build Cleaning (x11-drivers/ati-drivers-11.6::/mnt/nfs_portage/x11-drivers/ati-drivers/ati-drivers-11.6.ebuild)
1311210513:  ::: completed emerge (2 of 2) x11-drivers/ati-drivers-11.6 to /
1311210513:  *** Finished. Cleaning up...
1311210514:  *** exiting successfully.
1311210514:  *** terminating.

```

But it is possible :)
Cory

---

### Post by clytle374 on 2011-08-09
Well it worked until last night.  I didn't run any updates or change any configs either. 

I tried going into windows and it works there, but nothings after the kernel starts to load in linux.

No idea what happened, but at least I have 2 witnesses so I don't have to question my sanity.

Cory

---

### Post by pierreyy on 2011-08-15
guess whos pulling an all- nighter to try to fix it... thank you... much appreciated!

---

### Post by clytle374 on 2011-08-15
Let me know if you figure it out, been irritating me since it quit working.

If only I had changed something to explain it quiting.

Cory

---

### Post by pantropik on 2011-08-16
The suspense is killing me. I KNOW this is just a simple matter of flipping an ACPI switch somewhere, I've just been waiting impatiently for someone to figure out how and where.

Any news?

---

### Post by clytle374 on 2011-08-16
> **pantropik said:**
> The suspense is killing me. I KNOW this is just a simple matter of flipping an ACPI switch somewhere, I've just been waiting impatiently for someone to figure out how and where.

Any news?

I wish I knew enough on the subject to have tested what was happening when it was working.  After I did a complete shutdown and restart I figured it was here to stay.  

Cory

---

### Post by pierreyy on 2011-08-16
hey i have a question for clytle374...

 was this taken when the backilte was working?

---

### Post by pierreyy on 2011-08-16
well i hate to be the bearer of bad news.. but i couldnt figure anythin out... sry...anw do you think that there is a way to bypass the acpi just at this point?

---

### Post by clytle374 on 2011-08-16
It was working when I posted that.  One would think that disabling the acpi for it would make it work, but the acpi is a black hole in my knowledge.  

 
I'm going to see if I can get anything to work, but I have poison ivy right now and my roommate who uses that laptop has been hospitalized for it in the past so I'm not touching it right now.

---

### Post by pierreyy on 2011-08-16
> **clytle374 said:**
> It was working when I posted that.  One would think that disabling the acpi for it would make it work, but the acpi is a black hole in my knowledge.  

 
I'm going to see if I can get anything to work, but I have poison ivy right now and my roommate who uses that laptop has been hospitalized for it in the past so I'm not touching it right now.
 

 haha okay... when the acpi is disabled the backlite runs... but alot of ther more important features dont so thats not a solution...

---

### Post by clytle374 on 2011-08-16
> **pierreyy said:**
> haha okay... when the acpi is disabled the backlite runs... but alot of ther more important features dont so thats not a solution...

What I was thinking was that maybe acpi could be enabled, but the kernel leave the back light under bios control. But that probably isn't possible. Acpi was working properly when the black light was working.  

I logged in remotely and was trying to find something in /var/log/messages about it. The file is huge and I backed it up, but sadly these forums only show that my post was 1 week ago which does nothing help me find what date that was to narrow down searching the messages file.  

Also the log is stuffed full of messages from the wireless card saying it is sleeping.  I think it is way to big to attach.

Cory

---

### Post by pantropik on 2011-08-20
Here's what just happened. Well, first a little backstory. I've got a Macbook Pro that runs natty pretty much perfectly. I actually found myself MUCH preferring Ubuntu to Lion, but that's a whole other story. Anyway, I recently got a Toshiba Qosmio X775-3D, which is a beast of a thing with a quad core CPU, a Geforce 560M, etc. For gaming, watching Blu-Rays, etc, Windows 7 is pretty awesome. But when I use it at work I kinda have an Ubuntu-based workflow setup I'm very used to and comfortable with, so I really wanted to get natty on this thing. 

It also has a really cool red-backlit keyboard, which absolutely refuses to work with Linux. Or so I thought. It was REALLY bugging me since everything else works great pretty much out of the box. It's shocking how little you have to do to get a Linux box configured anymore. 

Long story short? Boot into Windows 7. Manually hibernate the system. Power back on, boot into Ubuntu and ... keyboard backlight works perfectly, times out after whatever time you specify in the BIOS, comes back on when you press a key. The best part? It sticks after a suspend/resume cycle. It sticks after a FULL shutdown and power cycle. I'm guessing that as long as I don't boot Windows and then shut it down without hibernating my keyboard will just keep working.

So now I have natty on my monster and it's working beautifully.

---

### Post by pantropik on 2011-08-20
Another update.  Just to see what would happen, I booted back into Windows, then rebooted and loaded Ubuntu. As expected, as soon as the kernel started loading the keyboard lighting shut off and remained dead.

I rebooted to Windows and, at the login screen, manually selected "Hibernate" and let it hibernate. As soon as it was done hibernating and had powered down I hit the power button and selected Ubuntu. And as soon as the kernel started loading the backlight died. I was pretty crestfallen at that point, so I let Ubuntu load and then rebooted.

During the POST and on the GRUB menu the backlighting worked. Yet again, once the kernel started loading, nothing.

So I remembered that I left the thing running Windows, sleeping. It had auto-hibernated after however long it takes to do that. Then, I had opened the lid and chose NOT to resume Windows in GRUB, but to boot Ubuntu and leaved Windows hibernated, and THAT is when the backlight worked.

So I went back to Windows and told it to hibernate when I close the lid, rather than sleep. I'd essentially be doing what I'd done accidentally before, this time without waiting for it to sleep for several hours before hibernating.

After I closed the lid, the hard drive light churned and churned (8GB of RAM is a lot of page out to disk, I guess) and eventually the hibernate was complete and it shut off. I opened the lid, booted Ubuntu, and now have a backlit keyboard. I can reboot. I can suspend/resume. I can shut down entirely and it'll still work.

I have no idea why.

---

### Post by hydrox24 on 2011-08-21
I am about to check this with my satelite a660-07t I will edit this post in with the results as soon as I can :)

Unfortunately, I can't seem to hibernate using windows... some sort of issue that requires re-installation to fix. So it would be good if someone else could verify the claim in the previous post with another laptop and perhaps then we can look into a way to give the issue a REAL fix.
P.S I am starting to think that this is almost purely to-do with how ubuntu handles the BIOS, perhaps it would be good if everyone that posts with related info mentions BIOS version and type? just a suggestion...

---

### Post by pantropik on 2011-08-25
That sucks.

Mine is still working very reliably. As long as I hibernate Windows by closing the lid and then leave it hibernated I can reboot, suspend/resume, power off, do whatever I want with the Qosmio + Ubuntu and the keyboard backlight works fine. If I boot Windows and leave it anything OTHER than hibernated (by closing the lid, NOT by choosing Hibernate from the menu) then no luck.

It's weird, but I don't really mind since I have no need to boot Windows unless I want to play a game, which I haven't had much time for lately.

---

### Post by pierreyy on 2011-08-26
i just checked it out... went into windows, changed the setting of what it does when i close the lid ( into hibernating) restarted my computer and BAM!!!


                       didnt work =(

---

### Post by hydrox24 on 2011-08-26
Did windows hibernate actually work at all though? and if it did then can you post some info on your BIOS version, computer model etc?

---

### Post by pantropik on 2011-08-27
Well, that sucks. On my Qosmio X775 it works every time. Sorry it didn't work for you. Was worth a shot.

---

### Post by pierreyy on 2011-08-28
> **hydrox24 said:**
> Did windows hibernate actually work at all though? and if it did then can you post some info on your BIOS version, computer model etc?


   windows did hibernate properly... as for my bios version it is 1.80, computer model, toshiba satellite a665, core i5, 4 gb ram, intel( what ever the hell is built in) graphics card, umm any thing else.... oh yh, ubuntu natty narwhal(11.04) 32 bit , and  i think unity is a bit buggy but a step forward nonetheless... =)

---

### Post by hydrox24 on 2011-09-01
I am running on BIOS version 2.00, which is the latest version for my model according to the toshiba website.
I was hoping that some sort of super awesome kernel hacker would come along and give us a patch, if you're looking at the post and are a super awesome kernel hacker then I would be willing to pay $10 via paypal for you service to fix this issue.
If you are willing to contribute a small amount to a kernel hacker that fixes our issue (can be even less than $10) then please chime up. I think that although this seems like a trivival matter, it would be so awesome to have this issue fixed properly.

---

### Post by pierreyy on 2011-09-01
hahah this thread just went from support into despair!

---

### Post by pierreyy on 2011-09-08
Okay so i have bios version 1.8 and "pantropik" has version 2.0 so i updated my bios from the toshiba website but i havent checked it yet.... ill get back to you once its done...wish me luck!

---

### Post by clytle374 on 2011-09-08
Again, I'm running gentoo, but after the last update the keyboard is lighting up again.  No control with the FN-Z, just the timer after a key-press.  I videoed it this time for evidence. 

Kernel was updated to 2.6.39-gentoo-r3.  

If there is anything that might help figure out what changed let me know.

Cory

PS Has anyone else had trouble with the harddrive?  Mine has started showing bad sectors in the last week, up to 166 now.  I've heard there is a bug causing false reporting of bad sectors, but I had lots of strangeness during the last update so the drive really might be failing.

---

### Post by SmileyCactus on 2011-09-11
I'm on an A660, running 11.04 and my backlight used to work perfectly (apart from fn-z, which has never done anything). A couple of days ago, after updates, I started up and I too lose my light when Ubuntu loads :(

As far as I can tell none of the updates should have impacted the keyboard, but here they are if it helps:

Commit Log for Fri Sep  9 15:07:19 2011


Upgraded the following packages:
evince (2.32.0-0ubuntu12.2) to 2.32.0-0ubuntu12.3
evince-common (2.32.0-0ubuntu12.2) to 2.32.0-0ubuntu12.3
gcstar (1.5.0-1ubuntu2) to 1.6.1ubuntu1
libevdocument3 (2.32.0-0ubuntu12.2) to 2.32.0-0ubuntu12.3
libevview3 (2.32.0-0ubuntu12.2) to 2.32.0-0ubuntu12.3
miro (3.5.1-1ubuntu1) to 4.0.3-1ubuntu1~pcf1~natty
miro-data (3.5.1-1ubuntu1) to 4.0.3-1ubuntu1~pcf1~natty
shotwell (0.9.3-0ubuntu0.1) to 0.11.1-1~natty1

Installed the following packages:
ffmpeg2theora (0.24-2ubuntu1)
libavahi-compat-libdnssd1 (0.6.30-0ubuntu2)
libcddb-perl (1.220-1)
libgail-3-0 (3.0.8-0ubuntu1)
libgd-gd2-perl (1:2.41-1)
libgd-graph-perl (1.44-4)
libgd-text-perl (0.86-6)
libgtk-3-0 (3.0.8-0ubuntu1)
libgtk-3-bin (3.0.8-0ubuntu1)
libgtk-3-common (3.0.8-0ubuntu1)
libwebkitgtk-3.0-0 (1.3.13-0ubuntu2)
libwebkitgtk-3.0-common (1.3.13-0ubuntu2)

---

### Post by pierreyy on 2011-09-20
alright... i have a question... can we find the driver for windows and reconfigure that to fit in the linux kernel? another thing... why does the backlite keyboard work in ubuntu on ather laptop brands? can we use that to copy some configuration settings from there.... also, the backlight works on the quosmio( see earlier posts) what configuration difference is there between the a665 and the quosmio regarding the keyboard settings, can we use that to workaround the problem? thanks in advance guys ( and sorry about the laundry list :P)

---

### Post by maul9999 on 2011-09-20
> **flbiggs said:**
> I installed Lucid on my new laptop, a Toshiba A665.  Everything seems to work very will right out of the box.  The only very minor issue I have run into is that I cannot figure out how to get the illuminated backlit keyboard to work.  It works fine under the native windows installation,and works fine through the Grub bootloader selection menu.  However, a few seconds after the laptop starts to install Ubuntu, the backlighting turns off.  The keyboard button (Fn-Z) does not turn it back on.  It is not the end of the world, but I kind of like the feature.  Anyone have any ideas?  Thanks

You need drive in order to get it work.  It is not easy to find the right drive.  Every if it is in OS without backlit drive, it won't work.

---

### Post by clytle374 on 2011-09-22
Mine quit working again after working for over a week.  I'm sure at this point it is some left over setting from windows. 

Cory

---

### Post by hydrox24 on 2011-09-29
If anyone here is familiar with the omnibook developers then I think that the omnibook module is the way to go in getting KBD backlighting implemented for our laptops. So go over to their sourceforge page and I have already posted a feature request so back or duplicate it or whatever you need to do to get their attention.

---

### Post by Murdoc_of_puts on 2011-10-08
Ok, so here's a little piece of info.  I recently installed OpenSuse, the keyboard light was working until I figured out I need ACPI support to read the battery power, so it wouldn't just shut off.  So there's the same problem in another OS.  Not much help, however, shortly before I switched back to Ubuntu, it started working again.  So I think that they fixed that problem.  Someone with more knowledge in this area might want to look into what they did to get it to work.  There are also some Japanese college kids who are working on porting linux into Toshibas.  I can't think of the name of the project off hand, but it might also be worth looking into.  I'm also trying to figure out a way to make this work, so between all of, those that are still interested, we should be able to come up with something? Maybe?

I have a Satelite A665 running UBU11.04 kernel 2.6.38-11 gen

I do have some fn keyboard buttons working though, so maybe that's another way.  
fn buttons that work- 
volume up
volume down
briight up
bright down
hybernate
print screen 
key pad on/off
sound on/off

---

### Post by pierreyy on 2011-10-14
hey guys do you think the new linux kernel will be able to read the backlighting? i hope so... does anyone have a clue??

---

### Post by alphadelta14 on 2011-10-14
> **pierreyy said:**
> hey guys do you think the new linux kernel will be able to read the backlighting? i hope so... does anyone have a clue??

I just got 3.0.0-12 and there is still no backlit keyboard support. I was hoping that it would do it.

How do you turn APCI off from the GRUB menu anyways? That's something I want to play with.

---

### Post by pierreyy on 2011-10-15
It failed here too :/

---

### Post by pierreyy on 2011-10-30
thread dead?:P    anyone?

---

### Post by JoeGoalie on 2011-10-30
> **pierreyy said:**
> thread dead?:P    anyone?

I wish something would come of this.  It is one of the few reasons I don't use linux on this laptop.  I have a M645 with Nvidia Optimus, that is the other reason I don't use it.  Of course, I've heard good things about bumblebee and being able to somewhat use Optimus.  Still haven't tried it though.

---

### Post by alphadelta14 on 2011-10-30
For those who would like to at least enable it at boottime via grub, you can edit your GRUB config file ( /boot/grub/grub.cfg ).
Copy your favorite menuentry{} block and edit one and add "acpi=off" to the end of the "linux   /boot/..." line. (This has to be changed for every kernel upgrade)
Unfortunately, off is the only option I get working. (I really wish "ht" would work). Besides hyperthreading, the OS doesn't know if the power is removed. The Fn keys and backlit screen still are as functional as they were before, and obviously, the keyboard works to the settings in BIOS.
I say this because if you are like me, you are either at home all the time connected to constant power and cool lights would be awesome, or you are on the go and lights are a waste and you just need the battery control.

---

### Post by lorentzr on 2011-10-31
Mine worked great for the last 6 months or so and suddenly stopped less than a week ago. Soon after I upgraded to 3.0.0-??, but I can't be sure that's exactly when it happened. What could have happened to break it? I miss it.

---

### Post by hydrox24 on 2011-11-11
I just upgraded from 10.04 where non of the lights on my sattelite worked to the new 11.10 release of ubuntu with the 3.0+ kernel. What is particularly interesting is that the light above my mousepad and the light in the "sattelite" logo in the bottom left-hand corner of my laptop now work well. the keyboard continues to lack any lighting however. Maybe it is worth asking the relevant people what changes were made to the LEDs and lights configuration in ACPI in the 3.0+ kernel, or maybe asking canonical what changed in 11.10. Can someone run lucid or 10.10 on kernel 3.0+ to see what makes the difference? what are other peoples experiences with this?

---

### Post by mrcan321 on 2011-11-15
for satellite p755-10g in ubuntu 10.10 , as it mentioned, after grub BK turns of and FN+z key doesnt work. but other FN combinations are working. now i am trying to disable acpi. so lets wait to see what becomes.:)

edit: i couldnt find acpi setting in bios. so keyboard backlight is still turned of.

---

### Post by Murdoc_of_puts on 2011-11-16
If you want to disable acpi you can change the Grub entry for a load option (os build that your loading)  I think it's in bootloader/grub/etc/grub.conf, but you would find the line ACPI=force in your grub.conf, change that to ACPI=no .  Also if you can enter variables into your load option before starting (you have a little bar you can type into before you select the load option) you could just type ACPI=no there as well. (Grubconf the program found in repos will let you set this up easily).  However BE WARNED disabling ACPI will also shut off things that deal with power(battery power reader, back screen light, and several other things.)  You will enter into the plugged in default power settings, but will recieve no notice if your battery dies, It'll just shutoff or power down.  This is a reason why this option doesn't work for me, but I hope this could help you.

---

### Post by piotao on 2011-12-30
Hi all,

I would like to say big thank you for investigating and finally for finding the way of enablig this keyboard.

I'm working on Toshiba A665-3DV laptop, with the Ubuntu Linux 10.04 changed without reinstall to the Ubuntu Mint 11.04, which works great and has a nice menu :)

I defined an additional entry in the grub.conf file for base config, with options added: acpi=off for the kernel line, and just to be sure, in another line, I set acpi=off.

This indeed disabled ACPI support, so now I have:
- keyboard highlight working nicely
- still no Fn+Z key working (as usual)
- unfortunately only the single CPU was found, with base clock set to 1.73 GHz (so it is hot and coolers spins on making quite a noise)
- maybe some other issues, which I did not notice yet.

Anyway, the keyboard works and I can work in darkness at night! The setting added for the second config in Grub satisfies myself nearly completely.

The last comment is that this whole issue is rather silly and definitely should not have SO LOW priority. This key highlight was one of the things I looked for before I bought this laptop. And now it's solved only on this f****d ms windows, while we - real Linux users, have to suffer...

Thank you all for help and this nice thread. I'll wait until this will be solved (unfortunately I'm unable to help with hacking) :(

GL & HF! Linux RULEZ because of it's community!

---

### Post by hydrox24 on 2012-01-15
Unashamed bump for this important thread. It might seem low priority, but this feature is extremely important to many people and if we can get it working will help create a better linux user experience for all toshiba computers.

---

### Post by pierreyy on 2012-01-16
> **hydrox24 said:**
> Unashamed bump for this important thread. It might seem low priority, but this feature is extremely important to many people and if we can get it working will help create a better linux user experience for all toshiba computers.

bump +1

---

### Post by //yardo on 2012-01-26
Well, I read through the entire thread hoping to get a resolution to the backlight problem... 

I'm on a Toshiba x775-3dv78. I love my laptop except for that one issue. :confused:

---

### Post by ryologic on 2012-03-05
Bump again. Just read through the whole thread. I can verify that the Windows Hibernation method works to enable the backlight on my a660. Is it possible that windows is running some kind of initialization at boot that enables the keyboard functionality? There must be some way to figure out what it's doing, I just don't know enough to extract that information.

---

### Post by hydrox24 on 2012-03-05
I would really like to have a resolution to this issue once and for all. Can we please get a dev/hacker on board with this thread?
Although it may not seem it, having a backlight on the keyboard is very important for many people and this should be a trivial problem to solve for someone well  versed in the kernel.

---

### Post by lorentzr on 2012-03-17
It's especially frustrating for me since it worked for months and then suddenly disappeared.

---

### Post by Curryfrotch on 2012-04-04
Well, I have some good news! I upgraded to 12.04 and found a modicum of advancement in our lighted keyboard issue. 
[Screenshot]("http://i.imgur.com/7K11y.jpg")

Yep, if you hit Fn+z an indicator pops up for the keyboard backlight!

The bad news is its still not working...but maybe soon?

---

### Post by pierreyy on 2012-04-13
> **Curryfrotch said:**
> Well, I have some good news! I upgraded to 12.04 and found a modicum of advancement in our lighted keyboard issue. 
[Screenshot]("http://i.imgur.com/7K11y.jpg")

Yep, if you hit Fn+z an indicator pops up for the keyboard backlight!

The bad news is its still not working...but maybe soon?

... fingers crossed

---

### Post by lorentzr on 2012-04-28
I just installed Kubuntu 12.04 and I'm not getting that behavior.  :(

---

### Post by Curryfrotch on 2012-05-07
> **lorentzr said:**
> I just installed Kubuntu 12.04 and I'm not getting that behavior.  :(

Huh, that's odd. I even get it when running the 12.04 Ubuntu live disc. It must be Unity DE. Do you have any other Fn key functionality in Kubuntu?

---

### Post by lorentzr on 2012-05-07
> **Curryfrotch said:**
>  Do you have any other Fn key functionality in Kubuntu?

Yes, all others seem to work. The various function keys work and even Fn 3 & 4 work for sound. (You know I just now noticed, while typing this message, the "light keyboard" icon on the z key!) Yeah, maybe the Gnome folks are ahead of KDE? Phooey....

---

### Post by rljhr on 2012-05-07
I have just got a Toshiba P770 because it had an iluminated keyboard. Yes Fn Z brings up an icon. No it does not light up my life!

---

### Post by pierreyy on 2012-06-20
bump

---

### Post by hydrox24 on 2012-07-17
Just upgraded my laptop to 12.04 and now, when I hit the keyboard backlight function key (Fn + z) I get the popup.

The popup, if compared to the one for volume, is similar to having the volume off but not muted (the icon is white, the bar below it is completely grey)

---

### Post by pierreyy on 2012-08-11
so i was playing a game on my windows partition when it suddenly crashed ( surprise surprise :P ). i had to do hold down the power button to shut it down... i tried boot back into Ubuntu... it acted  a bit weird ( i used the recovery mode to get it to boot) anw when it booted into Ubuntu the backlight from the keyboard was on... 

it there is anything you guys need to figure out why its working, just let me know!

i have a toshiba a665, dual boot between win7 and ubuntu 12.04

---

### Post by davenation on 2012-08-13
Hi everyone.

I'm new here and I want to install one distribution of linux on my toshiba a665 s6067 because windows got me tired of errors and crashes, I've been reading about you said of the KB and some other stuff, so, I want you to tell me or recommend which linux distribution should I install to get a nice start with the OS.

thanks in advance

---

### Post by madrang on 2012-08-29
With my Toshiba Qosmio x770 i can go to /sys/class/backlight/toshiba
In that folder there are some files that seems to be used to control the backlight. I just dont know the values i need to enable it.

---

### Post by tobie.de.beer on 2012-09-03
I got a X770 a week ago and tried about everything to get the keybord backlight and the LCD Brightness to work,

So far I found the following:

Keyboard backlight:
I can get it working as per the Bios setting by using a Win7 install disk and let it run until it require some input (choosing language etc.) and then holding the power button in for 5 sec. After that booting in linux the keybord backlight works (no Ctrl-Z though) I plan to make a partition with only the startup stuff from the install disk for that purpose. 
# EDIT: and it is working: use: d:\boot\bootsect /NT60 e: and copy all the stuff from the install disk to the drive (I ommited some stuff
# noteably the Install.wim a rather huge file) ( c: running windows installation d: windows install disk e: new partition formatted to ntfs
# for this purpose) for more info on creating this, have a look at the process to create a usb install disk. I simply ran sudo update-grub 
# afterward to have this in my grub menu. Now after I ran windows, I boot into this 'install disk' and hold the power switch down until it 
# powers off, afterward linux have a lit keyboard....
EDIT: Windows is breaking the above setup - I guess I'll have to cary a windows install disk around

For the Screen Brightness I had to use the addon for:
nvidia-dkms 
with:
echo X | sudo tee -a /sys/class/backlight/acpi_video0/brightness
where X is 0 to 7

The 3D stuff I could get to work but only as a addon program not as part of the Display driver (Nvidia does not support 3D on Linux and Geoforce) see: [http://users.csc.calpoly.edu/~rsomers/cpe572/](http://users.csc.calpoly.edu/~rsomers/cpe572/)

More on topic....

To me it seems that somewhere in the bios the latest default setting for the OS is stored (for acpi), when windows shut down it changes these setting before it powers down, and then linux load these (powered down windows) setting come into effect agian. Thefore swiching off while windows is running leave the righ settings in the bios somewhere...

Anyone knows much about reading bios setting and storing/resoring them?

---

### Post by nelsonhoover on 2013-01-03
Bump   :-\"

Toshiba 665 here too. Same problem.

---

### Post by hydrox24 on 2013-02-16
The issue with the A665 Laptops still has note been fixed in 12.04 and needs to be addressed for Toshiba laptops as a whole. They're popular laptops and this is a major usability issue. If we could get a Dev in here, it's surely a relatively small job to get the keyboard back-light working but still one that has a good return on it?

---

### Post by naftilos13 on 2013-03-05
I currently have a toshiba P755-11Q laptop , the combination FN+Z doesn t light up my keyboard and i have also tried booting to win7 and then holding the power button .Some times it worked for me but the next time i restarted my laptop the light was off again . a thing i should mention here is that i usually work without my battery . Recently i downloded HIRENS BOOT CD 15.2 RESTORED BY PROTEUS V1.1 , when i boot my laptop from it and tried to load MINI WINDOWS 7 from it i got errors and failed to boot so tried the last line of HIRENS main menu where it says ALTERNATIVE BOOT METHOD(GRUB4DOS).From that point i managed to load MINI WINDOWS 7 , my backlight keyboard was ON and i could control it with FN+Z . So i lighted up my keyboard and just shut down from MINI WIN 7 .Next reboot was without HIRENS so when i finally loged on to ubuntu, the keyboard was finally ON!!!  If i shutdown/restart my laptop with the battery on it the keyboard backlight stays ON all the times , if the baterry or the power cable is not attached to the laptop the keyboard light goes OFF and i have to repeat the whole process.I believe this is the best solution for my needs until now.Another strange information for those of you that understand a few more things  than a normal user like me is that during some restarts a sign of the power button appears on the bottom right corner of the first  black screen  where it suggests the pressing of F2 or F12 .When i entered bios setup with F2 i noticed that the tabs of the bios POWER MANAGEMENT & ADVANCED MENU are gray and don t give you the normal ability to change the settings , just display them. Of course when i restarted without any battery everything was normal.

---

### Post by tanzantj on 2013-03-06
I have a Toshiba satellite u945 (14'' ultrabook).  I've been fighting with this same problem for a few months. Tonight I found that if I boot my Windows 7 OS into safe mode and then just shut it down once I reach the login prompt my keyboard works when I boot into Ubuntu (12.10).  The hibernate workaround never worked for me but this safe mode seems to do the trick. I've tested and my success is reproducible.

Sumpin' is better than nothin'.

---

### Post by saugata on 2013-03-08
This trick worked for my Toshiba Satellite P740. Thanks.

---

### Post by MetalPotatoHead on 2013-04-10
There is a way to make keyboard backlight work in toshiba qosmio x770, I didn't tried in other toshiba computer, but I suppose it works too.
If you install windows (in my case I installed windows 7), just a clean install, without installing nothing, the lights work all the time in ubuntu, but you cannot turn them off, just in bios.

---

### Post by Twengg Rich on 2013-06-10
Have any of you guys tried **booting up a windows install dvd** and then **pressing the keyboard backlight key** on top of the keyboard? I did this and it worked for my toshiba satellite p755 s5265. You may not notice a change immediately, but after reboot into ubuntu, keyboard lights are on. 

I have only ubuntu and mint installed.

---

### Post by mesiu842 on 2014-04-07
There is a simple solution for toshiba backlight, found it long ago, just didn't knew it's such a big problem until I returned to Debian :-)
try to add 

blacklist toshiba_acpi 

module to /etc/modprobe.d/

This module appeared somewhere in the beginnig of kernel 3.0, previously there wasn't any module for toshiba. I was looking at changes in kernel a lot in the past (because they were working on WiFi network card) and as soon as this module appeared it turned out it's for newer toshiba laptops (those with EFI BIOS). You can check the source code if you don't believe me :-) (could changed since that time, I didn't have time to look at it since then)

Default ACPI is still working fine. Just don't forget to reboot, because rmmod -f toshiba_acpi won't solve the problem :-)

After removing that module all works fine: acpi, backlight Fn+Z shortcut, all other shortcuts (except Eco key)

---

### Post by raf-angius on 2014-04-08
Mesiu I tried your solution but it doesn't work for me (toshiba u940-103): blacklisting toshiba_acpi disable every function key in my model, including screen brightness... It seems to be hard to make this backlight working... So afraid, everything works well with 13.10 on this machine! But I still can't see my keyboard in the darkness!

---

### Post by naftilos13 on 2014-05-17
Just tested the blacklist toshiba solution in ubuntu 14.04 and it didn t worked for me , this time even the logo of the keyboard stopped  appearing when i was pressing FN+Z.
Another very strange thing i would like to share (tested only in 13.10) is that if i install kernel 3.9.5 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and boot up , the keyboard light is on 
and stays on in every kernel until i log on in windows.

---

