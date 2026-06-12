---
title: "Ubuntu 15.04 support for Asus Transformer Book Chi series?"
date: 2015-08-01
forum: Hardware
---

### Post by max60 on 2015-08-01
I'm looking to buy an Asus Transformer Book T300 chi or T100 chi and would like to know if linux runs well on the device. The devices are fairly new, having only been released earlier this year and not a lot of people have tried using them with linux or ubuntu. Has anyone had any luck installing ubuntu 15.04 on any of these two devices or have any knowledge of how the linux kernel runs on them?

Here are spec pages for the devices:

[https://www.asus.com/Commercial-Notebooks/ASUS_Transformer_Book_T300_Chi/specifications/](https://www.asus.com/Commercial-Notebooks/ASUS_Transformer_Book_T300_Chi/specifications/)

[https://www.asus.com/us/Notebooks_Ultrabooks/ASUS_Transformer_Book_T100_Chi/specifications/](https://www.asus.com/us/Notebooks_Ultrabooks/ASUS_Transformer_Book_T100_Chi/specifications/)

---

### Post by gudzwabofer on 2015-08-05
I haven't found a wealth of information either but I'm hoping it's relatively smooth. I've just paid for mine, and should be receiving it in the next day of two. I'll be attempting a triple boot with the preinstalled windows, ubuntu studio, and android. I'll let you know how it goes.

---

### Post by dr8 on 2015-08-13
I just completed a Kubuntu 14.04 install on my T300 Chi (alongside my Windows 10 install). It runs fairly well, with some issues:

- Installation from a *buntu live USB is made much easier if you have a USB keyboard and mouse also connected. Since there's only a single micro usb port, it's best to have a hub. I used the 3-port hub built into my HooToo USB 3.0 gigabit adapter. 
- Wifi worked out of the box, including during setup
- Bluetooth works fine with the keyboard dock (after pairing), but not until you've logged into KDE (and possibly Unity as well). Makes logging into the display manager somewhat complicated.
- Keyboard Fn shortcuts don't work (can probably be resolved with xmodmap or similar)
- Sound works out of the box

I sort of followed the process for installing Ubuntu onto a Surface Pro 3 that I found here [http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/](http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/) with the exception that to get into the UEFI/BIOS on the Chi, it's Volume - and the Power button. I didn't bother with the Secure Boot/rEFInd setup and just left Secure Boot disabled. grub2 seems to work just fine to launch both Kubuntu and Win10. Of course the grub menu also doesn't work with the BT keyboard, so you may want to set Windows as the default boot item. I think the volume buttons actually moved the selected item in the grub screen, but I could have just imagined this. 

If you've got any questions about the process, let me know.

EDIT: I've had a chance to play around with it some more and here's a few more findings:

- Touchscreen works as a pointer in Xorg
- Was able to get keyboard dock to work at a system level, so logging into lightdm works fine. I followed the guide here: [http://ubuntuforums.org/showthread.php?t=1479056&p=9363229#post9363229](http://ubuntuforums.org/showthread.php?t=1479056&p=9363229#post9363229) to get the keyboard paired and working across Windows and ubuntu
- I was right in that the Volume - button works during the grub selection screen. Unfortunately only the down button works, but to work around this, I re-ordered the grub boot items so Windows is first and default, and pressing the Vol Down allows me to highlight Ubuntu, and the Windows button acts as an Enter key. Easy enough to switch between OSes. I used the info here to perform this: [http://ubuntuforums.org/showthread.php?t=1805642&p=11053897#post11053897](http://ubuntuforums.org/showthread.php?t=1805642&p=11053897#post11053897)
- Haven't been able to get the trackpad working as a mouse. xinput lists the device, but it doesn't seem to want to do anything with it.

EDIT2: more notes:

- I re-enabled Secure Boot
- EFI partition is automatically mounted at /boot/efi, which makes editing EFI simple
- Installing rEFInd was cake; grab the binary package for *buntu from [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) and install it with dpkg. It generated the MOK keys and installed itself in /boot/efi/EFI/refind
- Upon first rEFInd boot, I had to import the keys as mentioned in the Ubuntu on Surface Pro 3 link above
- Volume keys work in the rEFInd boot manager, but it's Vol + that moves to the right, and Vol - moves the cursor down. There's no way to go left or up, so I reordered the boot entries in refind.conf 
- With rEFInd installed (and Secure Boot enabled), Windows no longer has a red background during boot/shutdown, which indicates Secure Boot is either off or UEFI is not working right
- Some Fn key combinations don't produce any sort of key events (e.g. Fn+F5 or F6 for screen backlight), so I remapped these functions to alternate key combinations
- Still no luck with the touchpad. Not a big issue for now, as I'll just use my active stylus or BT mouse
- Battery widget shows both notepad and keyboard battery values on hover 
- Battery life seems very comparable so far

---

### Post by gudzwabofer on 2015-10-29
[TABLE="class: tborder, width: 100%, align: center"]
[TR]
[TD="class: thead, align: right"]  #[**18**]("http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/linux-on-the-asus-transformer-book-t300-chi-4175549427-post5442145/#post5442145")[/TD]
[/TR]
[TR]
[TD="class: alt1, width: 175"][gudzwabofer]("http://www.linuxquestions.org/questions/user/gudzwabofer-1015378/")
LQ Newbie
 
Registered: Aug 2015
Posts: 2

Rep: [IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/reputation/reputation_off.gif[/IMG]

[/TD]
[TD="class: alt1"]I'm almost to the end of completing a triple boot of Windows 10, Ubuntu Studio Wily Werewolf 15.10 64bit, and Android Lollipop x86 5.1 rc1 64bit. Here's what I've done so far with the help of a few different forums and blog posts.

1. Upgraded the preinstalled Windows 8 to Windows 10.
2. Reduced the size of the windows partition from within windows to give me enough unallocated space for ubuntu.
3. Set aside a temporarily formatted portion for Android.
4. Disabled windows secure boot and smart boot as they are said to interfere with multi-boot attempts.
5. Bought a usb hub and a usb keyboard so I could get through the part of the ubuntu setup where you need to type stuff. This also came in handy later for the android install which didn't recognise the touchscreen.
6. I first attempted the ubuntu studio install with a usb drive containing 14.04 which failed at the Grub creation stage near the end, however I have since read that only 14.10 and up are compatible with UEFI. For this I needed to go with the limited support version of Ubuntu Studio, which is presently 15.10. This install went off without a hitch.
7. Paired the wireless keyboard. This glitches a little sometimes and needs to be re-pared, as I have also found in windows, so I assume it's at least partly a hardware issue.
8. Attempted the copying from within ubuntu method of installing android, couldn't get it to work.
9. Installed android from a boot flash drive, selecting no for both the grub options, and reformatting my previously set aside drive as ext4 because it's the only format compatable with UEFI, thus enabling me to install apps, which was impossible with the ext3 format. Android worked seamlessly when I ran it from the end of the install.
10. I'm still attempting to create a grub entry to enable me to get back into Android from boot.[/TD]
[/TR]
[/TABLE]

---

### Post by sfrineggi on 2015-12-10
> **dr8 said:**
> I just completed a Kubuntu 14.04 install on my T300 Chi (alongside my Windows 10 install). It runs fairly well, with some issues:

- Installation from a *buntu live USB is made much easier if you have a USB keyboard and mouse also connected. Since there's only a single micro usb port, it's best to have a hub. I used the 3-port hub built into my HooToo USB 3.0 gigabit adapter. 
- Wifi worked out of the box, including during setup
- Bluetooth works fine with the keyboard dock (after pairing), but not until you've logged into KDE (and possibly Unity as well). Makes logging into the display manager somewhat complicated.
- Keyboard Fn shortcuts don't work (can probably be resolved with xmodmap or similar)
- Sound works out of the box

I sort of followed the process for installing Ubuntu onto a Surface Pro 3 that I found here [http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/](http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/) with the exception that to get into the UEFI/BIOS on the Chi, it's Volume - and the Power button. I didn't bother with the Secure Boot/rEFInd setup and just left Secure Boot disabled. grub2 seems to work just fine to launch both Kubuntu and Win10. Of course the grub menu also doesn't work with the BT keyboard, so you may want to set Windows as the default boot item. I think the volume buttons actually moved the selected item in the grub screen, but I could have just imagined this. 

If you've got any questions about the process, let me know.

EDIT: I've had a chance to play around with it some more and here's a few more findings:

- Touchscreen works as a pointer in Xorg
- Was able to get keyboard dock to work at a system level, so logging into lightdm works fine. I followed the guide here: [http://ubuntuforums.org/showthread.php?t=1479056&p=9363229#post9363229](http://ubuntuforums.org/showthread.php?t=1479056&p=9363229#post9363229) to get the keyboard paired and working across Windows and ubuntu
- I was right in that the Volume - button works during the grub selection screen. Unfortunately only the down button works, but to work around this, I re-ordered the grub boot items so Windows is first and default, and pressing the Vol Down allows me to highlight Ubuntu, and the Windows button acts as an Enter key. Easy enough to switch between OSes. I used the info here to perform this: [http://ubuntuforums.org/showthread.php?t=1805642&p=11053897#post11053897](http://ubuntuforums.org/showthread.php?t=1805642&p=11053897#post11053897)
- Haven't been able to get the trackpad working as a mouse. xinput lists the device, but it doesn't seem to want to do anything with it.

EDIT2: more notes:

- I re-enabled Secure Boot
- EFI partition is automatically mounted at /boot/efi, which makes editing EFI simple
- Installing rEFInd was cake; grab the binary package for *buntu from [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) and install it with dpkg. It generated the MOK keys and installed itself in /boot/efi/EFI/refind
- Upon first rEFInd boot, I had to import the keys as mentioned in the Ubuntu on Surface Pro 3 link above
- Volume keys work in the rEFInd boot manager, but it's Vol + that moves to the right, and Vol - moves the cursor down. There's no way to go left or up, so I reordered the boot entries in refind.conf 
- With rEFInd installed (and Secure Boot enabled), Windows no longer has a red background during boot/shutdown, which indicates Secure Boot is either off or UEFI is not working right
- Some Fn key combinations don't produce any sort of key events (e.g. Fn+F5 or F6 for screen backlight), so I remapped these functions to alternate key combinations
- Still no luck with the touchpad. Not a big issue for now, as I'll just use my active stylus or BT mouse
- Battery widget shows both notepad and keyboard battery values on hover 
- Battery life seems very comparable so far



[COLOR=#333333]hello, I have a problem I installed Android-x86 dual boot with Windows 10 on asus [/COLOR][COLOR=#272727]t100ta[/COLOR][COLOR=#333333], I chose to use the grub2 instead of refind, because refind in touch mode or mode with the volume keys not working. I thought Grub2 worked with the volume +/- buttons but unfortunately does not go, but just with the keyboard arrow keys as refind[/COLOR]
[COLOR=#333333]Do you have any suggestions?[/COLOR]
[COLOR=#333333]thank you very much

[/COLOR]Emanuele

---

### Post by jbMacAZ on 2015-12-27
The T_**1**_00-CHI bluetooth keyboard does not operate at all with linux at this time, unless it is paired to an external USB bluetooth adapter.  I can also confirm that bluetooth does not run at boot time (even with an external USB adapter.)  Editing grub to add a default selection and a timeout can be quite helpful.  An external USB (non-bluetooth) keyboard will work with distro installation, grub and normal linux operation.

---

### Post by me_6650 on 2015-12-27
I just installed linux mint onto my T300 Chi transformer book over the holidays. I used LM 17.3 found here: [https://www.reddit.com/r/SurfaceLinux/comments/3w8du2/outofthebox_support_for_linux_mint_173_cinnamon/](https://www.reddit.com/r/SurfaceLinux/comments/3w8du2/outofthebox_support_for_linux_mint_173_cinnamon/) 

It works perfectly out of the box. This distro was originally made for the Surface tablet series but it have nearly full functionality with the T300 Chi tablet. The only thing I see after a few days of use is that the screen rotation in tablet mode does not work. The bluetooth keyboard, wifi, tablet buttons, etc all work perfectly. Take a look.

---

### Post by jbMacAZ on 2015-12-27
> **me_6650 said:**
> I just installed linux mint onto my T300 Chi transformer book over the holidays. I used LM 17.3 found here: [https://www.reddit.com/r/SurfaceLinux/comments/3w8du2/outofthebox_support_for_linux_mint_173_cinnamon/](https://www.reddit.com/r/SurfaceLinux/comments/3w8du2/outofthebox_support_for_linux_mint_173_cinnamon/) 

It works perfectly out of the box. This distro was originally made for the Surface tablet series but it have nearly full functionality with the T300 Chi tablet. The only thing I see after a few days of use is that the screen rotation in tablet mode does not work. The bluetooth keyboard, wifi, tablet buttons, etc all work perfectly. Take a look.

Thanks for the tip.  This is the first distro that I didn't have to edit before booting.  However, with the T**1**00-CHI, no wifi, no bluetooth.  I think I can get persistence working with a simple grub edit (for liveUSB).  Wifi is a driver issue that can be easily dealt with.  The 300-CHI is different from the 100-CHI, with a different processor and optionally more RAM.  Perhaps this thread should say "...Book _*300-*_CHI".  Anyway, I will still use this remix.  I like the added features.

Update:  I added "persistent" in grub.cfg (before "quiet splash --") and made sure there was an empty casper-rw file in the root of the USB (or a USB data partition by that name.)    The wifi driver was already present, I only needed to copy the nvram data file (brcmfmac43241b4-sdio.txt) to /lib/firmware/brcm/.  Wifi worked at next liveUSB boot.  T100-CHI is still not ready for prime time, but each bit of progress is appeciated.

---

### Post by dr8 on 2015-12-30
> **me_6650 said:**
> I just installed linux mint onto my T300 Chi transformer book over the holidays. I used LM 17.3 found here: [https://www.reddit.com/r/SurfaceLinux/comments/3w8du2/outofthebox_support_for_linux_mint_173_cinnamon/](https://www.reddit.com/r/SurfaceLinux/comments/3w8du2/outofthebox_support_for_linux_mint_173_cinnamon/) 

It works perfectly out of the box. This distro was originally made for the Surface tablet series but it have nearly full functionality with the T300 Chi tablet. The only thing I see after a few days of use is that the screen rotation in tablet mode does not work. The bluetooth keyboard, wifi, tablet buttons, etc all work perfectly. Take a look.

So the touchpad on the BT keyboard works OOTB? That's the only thing I'm missing in ubuntu. Will have to give Mint a try if that's the case, if for no other reason than to see how they got support working.

EDIT: After loading Mint, and trying to use the same linkkey that Windows uses, I lose touchpad (but retain keyboard). Having to constantly re-pair the dock when booting into different OSes is a pain, so it looks like Mint will get keyboard and a separate BT mouse.

---

### Post by dr8 on 2015-12-31
> **sfrineggi said:**
> [COLOR=#333333]hello, I have a problem I installed Android-x86 dual boot with Windows 10 on asus [/COLOR][COLOR=#272727]t100ta[/COLOR][COLOR=#333333], I chose to use the grub2 instead of refind, because refind in touch mode or mode with the volume keys not working. I thought Grub2 worked with the volume +/- buttons but unfortunately does not go, but just with the keyboard arrow keys as refind[/COLOR]
[COLOR=#333333]Do you have any suggestions?[/COLOR]
[COLOR=#333333]thank you very much
[/COLOR]

No idea here on how to get the volume keys to do anything different. It would probably have to be a BIOS/firmware update by Asus to change their behavior during boot.

---

### Post by landa-martin on 2016-01-05
> **jbMacAZ said:**
> The T_**1**_00-CHI bluetooth keyboard does not operate at all with linux at this time, unless it is paired to an external USB bluetooth adapter.  I can also confirm that bluetooth does not run at boot time (even with an external USB adapter.)  Editing grub to add a default selection and a timeout can be quite helpful.  An external USB (non-bluetooth) keyboard will work with distro installation, grub and normal linux operation.

Hi, I can confirm this issue. By change isn't there any progress? I mean to make working T100-CHI bluetooth keyboard without need of external USB bluetooth adapter. Thanks in advance, Martin

---

### Post by landa-martin on 2016-01-08
I bought external USB Bluetooth adapter to solve issue with not working keyboard. I can see new device by launching `hcitool dev` or in Unity dialog. Unfortunately connecting to Asus T100CHI Docking is failing. I tried automatic PIN detection and other choices, none of them are working, so I am am unable to pair devices. Any idea how to solve this issue? Thanks in advance. Martin

---

### Post by jbMacAZ on 2016-01-08
> **landa-martin said:**
> Hi, I can confirm this issue. By change isn't there any progress? I mean to make working T100-CHI bluetooth keyboard without need of external USB bluetooth adapter. Thanks in advance, Martin

There has been some very recent progress on getting the internal bt device running.  However,
1) the CHI keyboard is a little weird* and it often takes several attempts to pair it with either the internal or an external USB bluetooth.  I have a logitech bt keyboard that behaves much better.
2) to get internal bt working you will need
     _a) very recent development tools (Ubuntu-Wily repos at a minimum, nothing older, especially not Mint)
     _b) build your own kernel 4.3.3 with the bt device ID code BCM2E71 patched (along with all the other T100 device specific patches)
     _c) build and install a custom bluez bluetooth stack - a very frustrating experience if you have stale repositories or easily unmet dependencies
     _d) a device driver .hcd file
     _e) an iterative installation procedure (persistence and patience) and edits to rc.local
  *  f) recommend installing blueman - bluetooth device manager for pairing management.  Much better than default manager, but still not great.

Fortunately, the Ubuntu/T100 G+ group has done a great job gathering the instructions, patches and where to get the files (check all bluetooth threads, many good hints away from main thread.)   It also helps to look at the LinuxFromScratch bluez page for more build hints.  Or just wait for the Linux 4.4 or 4.5 release.  The next T100 kernel should have most of this already done!  With what is available so far, I still have to pair every boot.  While, I won't recommend this to anyone right now, I finally believe bluetooth support will happen for the T100CHI!

---

### Post by Bucky Ball on 2016-01-09
I advise all of you, particularly those who have only just started working on this, to install or upgrade to 15.10 (or clean install 14.04 LTS is you want an LTS release). 15.04 is out of support in about two weeks in which case you'll need to upgrade anyway and this issue may or may not be relevant, may have changed in your new 15.10 install. 

EOL releases are not officially supported here. Good luck.

---

### Post by landa-martin on 2016-01-09
> **jbMacAZ said:**
> 
Fortunately, the Ubuntu/T100 G+ group has done a great job gathering the instructions, patches and where to get the files (check all bluetooth threads, many good hints away from main thread.)   It also helps to look at the LinuxFromScratch bluez page for more build hints.  Or just wait for the Linux 4.4 or 4.5 release.  The next T100 kernel should have most of this already done!  With what is available so far, I still have to pair every boot.  While, I won't recommend this to anyone right now, I finally believe bluetooth support will happen for the T100CHI!

Do you mean Linux kernel releases available at [1]?

BTW, meanwhile I bought external USB Bluetooth adapter. Now I can see in Bluetooth Manager (blueman) ASUS T100CHI DOCKING device. But all my attempts for pairing (use random passkey) are failing (Failed to add device). Do you have any advice how to find out what is wrong?

[1] [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Bucky Ball on 2016-01-09
> **landa-martin said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

The point I'm trying to make. This link is to the Wily daily kernel. Wily = 15.10 which you are going to need to upgrade to in a couple of weeks anyway. Why install the 15.10 kernel in 15.04, which is almost EOL, when you are going to need to upgrade to 15.10 in a couple of weeks?

Anyway, good luck with it. Over and out. :)

---

### Post by landa-martin on 2016-01-09
> **Bucky Ball said:**
> The point I'm trying to make. This link is to the Wily daily kernel. Wily = 15.10 which you are going to need to upgrade to in a couple of weeks anyway. Why install the 15.10 kernel in 15.04, which is almost EOL, when you are going to need to upgrade to 15.10 in a couple of weeks?

Sorry, the thread title is outdated, I have upgraded to 15.10 some weeks ago.

---

### Post by landa-martin on 2016-01-10
> **landa-martin said:**
> Do you mean Linux kernel releases available at [1]?

BTW, meanwhile I bought external USB Bluetooth adapter. Now I can see in Bluetooth Manager (blueman) ASUS T100CHI DOCKING device. But all my attempts for pairing (use random passkey) are failing (Failed to add device). Do you have any advice how to find out what is wrong?

[1] [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

BTW, I tried to install 4.4.0RC8 Wily on my T100CHI. And computer stopped working (no WIFI, touchscreen not working). I must to reinstall the PC from scratch. Why touchscreen is not working on Linux kernel 4.4? Thanks for feedback in advance.

---

### Post by jbMacAZ on 2016-01-11
> **Bucky Ball said:**
> The point I'm trying to make. This link is to the Wily daily kernel. Wily = 15.10 which you are going to need to upgrade to in a couple of weeks anyway. Why install the 15.10 kernel in 15.04, which is almost EOL, when you are going to need to upgrade to 15.10 in a couple of weeks?

Anyway, good luck with it. Over and out. :)

Please feel free to update the topic title - the problem is unchanged with 15.10. None of the official kernels adequately support the T100 without patches. Linux 4.4-x is actually a regression for the T100-CHI.  (Which has nothing to do with Ubuntu.)

4.4.x in PPA does not  work well on the CHI.  G+ Ubuntu/T100 group hasn't posted a 4.4.0-T100 kernel yet but at least they understand the platform.  But they are not a customer service organization.  That blame belongs to ASUS and the way they snub Linux. </rant>  The G+ group can at best only provide self-service patches for building your own kernel.

---

### Post by bartonprime on 2016-04-17
Hey guys, Recently picked up a T300 Chi, loaded it up with Ubuntu 15.10 (since upgraded to 16.04 beta) , i found that by installing the gnome desktop and using its Bluetooth manager i could add the Bluetooth keyboard dock first go (touchpad also works but no gestures). I had the same issue a couple months back when i installed ubuntu on my Mac. Everything else worked out of the box so to speak, except for auto-rotation which I am yet to fix, was wondering if anyone had any success with Magick Rotation or with Autorotate by Karol Krizka? any help or direction would be greatly appreciated.[COLOR=#545454][FONT=arial][/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-04-17
*Thread closed.*

Back to sleep. This thread was about 15.04, no longer supported.

@bartonprime: Posting on an old thread with a title that has nothing to do with your support request 20 posts deep does nothing for your chances of getting help. Suggest you post a new thread in the appropriate area with descriptive title. Good luck. ;)

---

