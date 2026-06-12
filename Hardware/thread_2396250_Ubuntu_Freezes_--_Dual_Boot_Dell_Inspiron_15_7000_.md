---
title: "Ubuntu Freezes -- Dual Boot Dell Inspiron 15 7000 Gaming"
date: 2018-07-12
forum: Hardware
---

### Post by dogeatery on 2018-07-12
I finally managed to get Ubuntu installed on this beast of a machine but now I have new issues.

Within seconds or minutes of logging in as normal, the desktop freezes. The pointer can still be moved, both with a USB mouse and the trackpad, but all other functionality is ceased. The clock stops. The "loading" pointer stops spinning in circles, and clickable elements are nonresponsive to the pointer, as well as to clicking attempts. 

The longest I've managed to go before having this issue is about two minutes, although it sometimes freezes immediately after login, with a white pointer in the center of a black screen.

I am really at a loss for what to do next. While I've seen lots of people having trouble with Dell Inspiron computers in this forum, nobody has described the issue I'm experiencing.

---

### Post by RobGoss on 2018-07-12
There could be a number of reasons why something like this would happen. Please share the specs for this machine that would be a starting point

I also run a few Dell Inspiron's with any problems

---

### Post by dogeatery on 2018-07-12
Thanks for your quick response. Sorry for my poor form. Specs as follows:

CPU: Intel Core i5 2.5GHz (64 bit)
RAM: 16gb DDR4
GPU: Nvidia Geforce GTX1050 Ti w/ 64MB memory

As per all online instructions I could find, I've disabled Secure Boot and left UEFI intact. I can't seem to find any options regarding so-called Fast Boot, although everyone says I should disable it before installing.

Windows 10 came pre-installed and I've managed to get Ubuntu alongside with no apparent issues on that end. I've allocated a total of just over 100 gb of space to /root and /home, and 8gb of swap space (While I've read various things about swap space over the years, I have no idea what is an appropriate amount)

---

### Post by oldfred on 2018-07-12
Have you installed the nVidia proprietary driver?
Since very new card, you may need or want the ppa to get newest driver from repository. Do not download directly from nVidia.

       nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

You must have a fast boot setting somewhere in UEFI. It is required by Microsoft on all Windows 10 systems as part of making it seem that Windows boots faster.

Have you updated UEFI from Dell? And if NVMe SSD, updated firmware for SSD?

       
 DELL Inspiron 15 7000 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
[https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560](https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560) 
            Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)

---

### Post by dogeatery on 2018-07-14
Thanks, oldfred, for your thorough and thoughtful response to my inquiry. I haven't been able to reply until now.

> Since very new card, you may need or want the ppa to get newest driver from repository. Do not download directly from nVidia.

       nVidia install, purge if needed.
[URL="https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336"]https://ubuntuforums.org/showthread....6#post13735336
[/URL][URL="https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336"]
[/URL]
I want to do this but the PC freezes before I can take the necessary steps. Can I boot into a command line and do it? (I have an additional problem in that the PC is not hard-wired into a network. Connecting to a wifi network via command line isn't something I've had to do before)

> You must have a fast boot setting somewhere in UEFI. It is required by  Microsoft on all Windows 10 systems as part of making it seem that  Windows boots faster.

More than once, I've combed through the UEFI menus and didn't see anything that said "fast boot" ... 

Have you updated UEFI from Dell? And if NVMe SSD, updated firmware for SSD?[/QUOTE]

Definitely not at this time. I have an SSD. How can I update these things when my PC freezes?

As for the rest of your response, it seems like they are for booting and running the liveUSB. I have managed to install the OS from USB, but it freezes after I login with my password.

---

### Post by oldfred on 2018-07-14
Dell is about the only major vendor that will let you update UEFI from grub menu. Most including Dell update from within UEFI or Windows. You have to have the update in a FAT32 formatted partition for UEFI to be able to read it. I put it in the ESP - efi system partition.

I have not updated firmware on NVMe drive, you have to check with vendor.

Can you boot to command line with recovery mode, or second line in grub menu, may be submenu.

Have you tried booting with nomodeset boot parameter. That often is needed with nVidia, until proprietary driver installed.

Direct boot to UEFI from Grub menu.
       menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup 
 }

       Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)

---

### Post by dogeatery on 2018-07-14
I appreciate how quickly you respond to these posts! Unfortunately, a lot of what you've suggested is either over my head or requires some further instruction. I'm having a difficult time making sense of what you've written ...

How can I update UEFI from GRUB without an internet connection?

> Can you boot to command line with recovery mode, or second line in grub menu, may be submenu.

Yes, but what should I do from there?

> Have you tried booting with nomodeset boot parameter. That often is needed with nVidia, until proprietary driver installed.

How do I set that parameter? (I need hand-holding ... )

> Direct boot to UEFI from Grub menu.
       menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup 
 }

Is this what I should do to set nomodeset?

> Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article...nments?lang=en]("https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en")

I can't do this unless I can connect to the internet ...

---

### Post by oldfred on 2018-07-14
While you can install Ubuntu without Internet, it is very difficult to update without it.
And you just about need it to update UEFI.
You probably can use another computer to download UEFI update file from Dell & then copy to your Dell for update per Dell link above.

Are you getting grub menu?
If not you may need to press escape key from Dell logo on screen but before system starts booting. You may have to press more than once to catch the correct time.
You do need fast boot off in Dell. All UEFI systems have that setting as it is required by Microsoft for all Windows UEFI systems. Fast boot in UEFI is different than the fast start up setting in Windows which is hibernation.

Can you not get a wired Ethernet connection just to do install & updates?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

But again, you need Internet to download nVidia driver.

There are ways to download updates on one system, and copy to another. But that is pretty advanced. Do not know details as I have never done it. some info:
[https://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline/129543#129543](https://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline/129543#129543)

---

