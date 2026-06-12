---
title: "Surface Pro 3 Support"
date: 2014-06-24
forum: Hardware
---

### Post by bowmessage on 2014-06-24
Hey all,

Figured I would kick off a Surface Pro 3 thread. Running an i5 128gb model with a type cover keyboard. So far the only issue preventing me form using Ubuntu as a daily driver is the lack of keyboard support for the type cover. The trackpad on the type cover works well, so that's a start.

I wonder if anyone knows how to modify the patch provided at [http://linux-kernel.2935.n7.nabble.com/PATCH-Add-HID-s-to-hid-microsoft-driver-of-Surface-Type-Touch-Cover-2-to-fix-bug-td790242.html](http://linux-kernel.2935.n7.nabble.com/PATCH-Add-HID-s-to-hid-microsoft-driver-of-Surface-Type-Touch-Cover-2-to-fix-bug-td790242.html) to support the new type cover.

Thanks for any help anyone provides, and I'll be looking into compiling my own kernel in the coming week. Good luck everyone!

Edit: Also thought I should note that I used the most recent patched kernel listed in this thread about type covers for the 1st and 2nd models ([http://ubuntuforums.org/showthread.php?t=2183946&page=13](http://ubuntuforums.org/showthread.php?t=2183946&page=13)) with no luck.

Edit 2: Just installed a bunch of updates from my Windows partition. One of them overwrote my bootloader and I had to boot from my Ubuntu USB installer and run boot-repair to reinstall GRUB. I also noticed that the updates must have changed the firmware of the type cover: the trackpad has stopped working. Now only the pen or an external mouse will work as a pointing device.

Edit 3: Turns out I was wrong about the trackpad no longer working. It just seems to not work on some boots. More research required...

---

### Post by DiThi on 2014-06-26
Hello, can you copy the output of [FONT=Courier New]lsusb[/FONT] with the keyboard on and off? Wait for a minute or reboot after removing the keyboard and before typing [FONT=Courier New]lsusb[/FONT] again.

Thank you.

---

### Post by bowmessage on 2014-06-27
I will definitely do that DiThi, thanks for your offer to help. I have already scraped the device ID and written the patch but I have had trouble building because my partition was too small to complete the build, resulting in loads of weirdness that occurs with a full hard drive. Lessons learned. 

I will post the device ID as soon as possible. I have a busy day today so may have to be tomorrow. Thanks again.

---

### Post by bowmessage on 2014-06-28
Hi DiThi. Just got my lsusb dumps, thank you again for your help. Sorry I'm a kernel newb, I really appreciate the help.

[Type Cover 3 connected, as well as wireless keyboard / mouse dongle (0745)]
me@me-Surface-Pro-3:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 045e:07bf Microsoft Corp. 
Bus 001 Device 004: ID 045e:07be Microsoft Corp. 
Bus 001 Device 003: ID 045e:07dc Microsoft Corp. 
Bus 001 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[Type Cover 3 removed]
me@me-Surface-Pro-3:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 045e:07bf Microsoft Corp. 
Bus 001 Device 004: ID 045e:07be Microsoft Corp. 
Bus 001 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Hope this is enough info, looks like the type cover is 07dc. Thanks so much!

---

### Post by Vladlenin5000 on 2014-06-28
So, this is the one: ```
Bus 001 Device 003: ID [COLOR=#ff0000]045e:07dc[/COLOR] Microsoft Corp.
```

---

### Post by alicia4542 on 2014-06-28
I just release a new patched Linux kernel version **3.13.0-30.54** for Surface Pro, tested and working on my Surface Pro 2 with Type Cover 2.

Download: [http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz](http://www.mediafire.com/download/v3gau148akhop6p/linux-3.13.0-30.54-surfacepro.tgz)

Built with patch: [http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz](http://www.mediafire.com/download/2ua8gyvqt3o3ua4/linux-source-3.13.0-surfacepro2-fix.tgz)

I would appreciate if any Surface Pro 3 could please test this kernel on their devices, and report back if it works or not, since I am not lucky enough yet to own one.

It would be best to combine all Surface Pro patches together, and have a single "patched" Linux kernel release for all Surface Pro versions and all covers.

---

### Post by bowmessage on 2014-06-29
I'll give it a go alicia, I already tried another kernel version for the SP2 with no luck, but I'll let you know! Thanks so much!

EDIT: running it currently. Unfortunately the type cover 3 is not working (well the trackpad still works, but no keyboard). Wifi seems different but still works, usually better and sometimes worse than running a normal kernel. Also, my CPU seems to get better utilized as I can switch workspaces much faster (normal kernel seems to have trouble with the high resolution). Watching the CPU temperatures, the fan duty cycles seem to better tuned and keep the surface cooler as well. Also, the 2nd button on the pen now works as middle click. Thanks alicia!

---

### Post by alicia4542 on 2014-06-29
> **bowmessage said:**
> I'll give it a go alicia, I already tried another kernel version for the SP2 with no luck, but I'll let you know! Thanks so much!
EDIT: running it currently. Unfortunately the type cover 3 is not working (well the trackpad still works, but no keyboard). Wifi seems different but still works, usually better and sometimes worse than running a normal kernel. Also, my CPU seems to get better utilized as I can switch workspaces much faster (normal kernel seems to have trouble with the high resolution). Watching the CPU temperatures, the fan duty cycles seem to better tuned and keep the surface cooler as well. Also, the 2nd button on the pen now works as middle click. Thanks alicia!
Thank you for testing my modified kernel.

I just noticed that Type Cover 3 support was missing in the kernel.  I have just added it to my Surface Pro patch, and built a new kernel.

Download: [http://www.mediafire.com/download/ovxfo4lbq22dxia/linux-3.13.0-30.54-surfacepro3.tgz](http://www.mediafire.com/download/ovxfo4lbq22dxia/linux-3.13.0-30.54-surfacepro3.tgz)

**Forgot to mention, that since the package name and version is the same, you will need to uninstall my previous kernel, if you previously installed it, before installing this new kernel!**
dpkg -r linux-cloud-tools-3.13.0-30-surfacepro linux-headers-3.13.0-30-surfacepro linux-image-3.13.0-30-surfacepro linux-tools-3.13.0-30-surfacepro

Please let me know if it works with your Type Cover 3.  If anyone has a Touch Cover 3, and can do a "lsusb", and post the output, I will try to add support for it as well.

On a side note, I am working for unified support (with common kernel and patch) for all Surface Pro versions and accessories, so I think it makes sense to merge this thread into with the older established Surface Pro thread: [http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946).

---

### Post by bowmessage on 2014-06-29
Wow!! That was so fast, thanks so much! It works! Unfortunately it's stopped the trackpad working, but it's definitely a huge step in the right direction. I'll post any of my future findings in that thread which you linked. Also might be headed to a Microsoft Store tomorrow, I'll see if I can grab a USB Device ID from a type cover if I can find one.

---

### Post by alicia4542 on 2014-06-29
> **bowmessage said:**
> Wow!! That was so fast, thanks so much! It works! Unfortunately it's stopped the trackpad working, but it's definitely a huge step in the right direction. I'll post any of my future findings in that thread which you linked. Also might be headed to a Microsoft Store tomorrow, I'll see if I can grab a USB Device ID from a type cover if I can find one.
Thank you for also quickly testing...

Hmm, so with this newer kernel, the type cover 3 keyboard works, but its trackpad does not work anymore.  Sorry about that.

I will need to examine the source to see why, and get back to you.

To help troubleshoot, could you please run this command and post the output?
**dmesg | grep -i 045e**

Please let me know if you find any other issues with the newer kernel.

I will be happy to post my modified patch, once we get it fully working with the Type Cover 3.

---

### Post by bowmessage on 2014-06-30
Here's the output:
> 
me@me-Surface-Pro-3:~$ dmesg | grep -i 045e
[    1.531060] usb 1-3: New USB device found, idVendor=045e, idProduct=07dc
[    1.539663] hid-generic 0003:045E:07DC.0001: input,hiddev0,hidraw0: USB HID v1.11 Keyboard [Microsoft Surface Type Cover] on usb-0000:00:14.0-3/input0
[    1.714748] usb 1-7: New USB device found, idVendor=045e, idProduct=07be
[    1.898833] usb 1-8: New USB device found, idVendor=045e, idProduct=07bf


Also worth mentioning that while the trackpad does not work for moving the mouse around but I can manage to right click sometimes. Thanks again.

---

### Post by javispedro2 on 2014-07-03
Do you dualboot?
If so, have you tested whether it is the case that the trackpad doesn't work if you reboot from Windows into Ubuntu, but it works if you poweroff first and then directly boot into Ubuntu?

That's the case at least with the SFPro2. I have a small utility that is able to reset the trackpad from Linux and "fix it", which I'm willing to share it if this proves to be the problem.

---

### Post by bowmessage on 2014-07-03
> **javispedro2 said:**
> Do you dualboot?
If so, have you tested whether it is the case that the trackpad doesn't work if you reboot from Windows into Ubuntu, but it works if you poweroff first and then directly boot into Ubuntu?

That's the case at least with the SFPro2. I have a small utility that is able to reset the trackpad from Linux and "fix it", which I'm willing to share it if this proves to be the problem.

Interesting! Unfortunately that's not the case, I just tested a cold boot into Ubuntu. I'd still be interested in the utility however, if you wouldn't mind sharing!

---

### Post by rmcrowley2000 on 2014-07-04
I came across this thread when trying to get Ubuntu working on my Surface Pro 3 as well.  I would be happy to test out any newer kernels (or other utilities) as they are made.

I am testing the newest kernel in this thread right now, and it is working decently from a cold boot.  It does not work well from a restart, and it works quite poorly when restarting from Windows.  Oddly enough, the two other kernels I tested work best when restarted from Windows.  Results are below.  Let me know if you need any information or testing.
[B]
From COLD BOOT[/B]
Surface pro kernel:
What works: Keyboard (great), wifi, touchpad clicks (left and right), pen (hovering and tapping), the second pen button, touchscreen (multitouch) [Pen and touch screen take quite a while to start up (close to a minute), but they do start.]
What doesn't: Touchpad movement and scrolling, other pen buttons

Comparison to current kernel (3.13.0-30):
What works: wifi
What doesn't: touchpad, keyboard, pen, touchscreen

Comparison to old kernel (3.13.0-24):
What works: wifi, touchscreen (multitouch), pen (hovering and tapping), the second pen button
What doesn't: touchpad, keyboard, other pen buttons[B]

From RESTART (Ubuntu)[/B], differences from cold boot highlighted

Surface pro kernel:
What works: Keyboard (great), wifi, touchpad clicks (left and right)
What doesn't: Touchpad movement and scrolling, *pen*, *touchscreen*

Comparison to current kernel (3.13.0-30):
What works: wifi
What doesn't: touchpad, keyboard, pen, touchscreen

Comparison to old kernel (3.13.0-24):
What works: wifi, touchscreen (multitouch), pen (hovering and tapping), the second pen button
What doesn't: touchpad, keyboard, other pen buttons
[B]
Reboot from WINDOWS[/B], differences from cold boot highlighted

Surface pro kernel:
What works: Keyboard (great), wifi, touchpad *taps* (left and right)
What doesn't: Touchpad movement and scrolling *and clicks*, *pen*, *touchscreen* 

Comparison to current kernel (3.13.0-30):
What works: wifi, *touchpad*,* touchscreen (multitouch)*, *pen (hovering and tapping)*, *the second pen button*
What doesn't: keyboard, other pen buttons

Comparison to old kernel (3.13.0-24): [note that a bunch of errors are thrown at boot]
What works: *touchpad*, wifi, touchscreen (multitouch), pen (hovering and tapping), the second pen button
What doesn't: keyboard, other pen buttons

---

### Post by javispedro2 on 2014-07-05
> **bowmessage said:**
> I'd still be interested in the utility however, if you wouldn't mind sharing!

[Here it is]("https://gitorious.org/javispedro-desktop-misc/hidptp"), but I'm not certain if it will work "as is" on the Surface 3. Since they removed Wacom, the HID reports may have changed, and in the current version I'm just hardcoding the report numbers from the Surface Pro 2.

In any case, it is probably not the same issue if touchpad works after a reboot from Windows.

---

### Post by ghaspias2 on 2014-07-05
Hi,

I have been  testing Ubuntu 14.10 (Utopic), Gnome edition, on my Surface Pro 3. I just want to report here that besides already reported issues, while using the live image I have a few other hardware issues:
- Bluetooth is not detected at all
- None of the webcams are detected
- power consumption seems to be much higher than under windows

Correction:
After several tests with powertop, the estimated battery life seems in line with the windows 8 to 9 hours of normal use.

---

### Post by OG_KORYONE on 2014-07-11
[COLOR=#000000][FONT=Arial]Hi.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I run Arch and stumbled across this thread.   I have the keyboard and mouse working together.  It's kinda hacky, but it works.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]For the kernel, I am using this:[/FONT][/COLOR]

```
[COLOR=#000000][FONT=Arial]diff --git a/drivers/hid/hid-ids.h b/drivers/hid/hid-ids.h[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]index 6d00bb9..2fd9d6d 100644[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]--- a/drivers/hid/hid-ids.h[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]+++ b/drivers/hid/hid-ids.h[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]@@ -637,6 +637,7 @@[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] #define USB_DEVICE_ID_MS_SURFACE_PRO_2   0x0799[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] #define USB_DEVICE_ID_MS_TOUCH_COVER_2   0x07a7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] #define USB_DEVICE_ID_MS_TYPE_COVER_2    0x07a9[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]+#define USB_DEVICE_ID_MS_TYPE_COVER_3    0x07dc[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial] #define USB_VENDOR_ID_MOJO             0x8282[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] #define USB_DEVICE_ID_RETRO_ADAPTER    0x3201[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]diff --git a/drivers/hid/hid-microsoft.c b/drivers/hid/hid-microsoft.c[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]index 8ba17a9..a932cbd 100644[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]--- a/drivers/hid/hid-microsoft.c[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]+++ b/drivers/hid/hid-microsoft.c[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]@@ -274,6 +274,8 @@ static const struct hid_device_id ms_devices[] = {[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]                .driver_data = MS_NOGET },[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]        { HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_COMFORT_MOUSE_4500)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]                .driver_data = MS_DUPLICATE_USAGES },[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]+       { HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_TYPE_COVER_3),[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]+                .driver_data = 0 },[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]        { HID_BLUETOOTH_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_PRESENTER_8K_[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]                .driver_data = MS_PRESENTER },[/FONT][/COLOR]
```



[COLOR=#000000][FONT=Arial]This is derived from [https://bugzilla.kernel.org/show_bug.cgi?id=64811](https://bugzilla.kernel.org/show_bug.cgi?id=64811)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]There is also [https://github.com/torvalds/linux/commit/00478ee8984a80e531ed491eede0459eae07396d](https://github.com/torvalds/linux/commit/00478ee8984a80e531ed491eede0459eae07396d), but I could only reproduce the quirk on the surface pro 3 once. [/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]To get the keyboard and touchpad working together, you can hack your evdev config by specifying the vendor and use the option "IgnoreAbsoluteAxes" option.[/FONT][/COLOR]
```

Section "InputClass"
        Identifier "Surface Pro 3 cover"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "vendor" "045e"
        Option "product" "07dc"
        Option "IgnoreAbsoluteAxes" "True"
EndSection

```

---

### Post by rubiojr2 on 2014-07-23
Patched kernel and uploading pre-built binaries right now, in case anyone is interested: [https://github.com/rubiojr/surface3-kernel](https://github.com/rubiojr/surface3-kernel)

---

### Post by anchoo2kewl-gmail on 2014-07-28
Hello Alicia,

Thank you for all your effort on getting drivers function on the surface pro. I bought a SP3 a yesterday and tried installing Ubuntu 14.04. The type cover doesn't work as pointed out. I downloaded [http://www.mediafire.com/download/ov...urfacepro3.tgz]("http://www.mediafire.com/download/ovxfo4lbq22dxia/linux-3.13.0-30.54-surfacepro3.tgz") and installed all 4 packages. Unfortunately the keyboard doesn't work at all. Interestingly, the trackpad works sometimes and at other times it doesn't. Finally, after installing your packages, my wi-fi stopped working. Hence I ran the command to remove the previously installed packages. The wi-fi started working after that.

---

### Post by ghaspias2 on 2014-08-03
Just to add to my previous post:
I just tested the pen pressure support and it works perfectly on MyPaint (using ubuntu gnome utopic alpha2 live image, cold boot on a surface pro 3).

---

### Post by moootech on 2014-08-29
Thanks everyone. Just to confirm that everything is working fine now - touchpad and keyboard. I had to install and use the 3.16.xx kernel and add the following code to /usr/share/X11/xorg.conf.d/10-evdev.conf.

```

Section "InputClass"
        Identifier "Surface Pro 3 cover"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "vendor" "045e"
        Option "product" "07dc"
        Option "IgnoreAbsoluteAxes" "True"
EndSection
```

---

### Post by ROVguy on 2014-09-06
> **alicia4542 said:**
> 
Download: [http://www.mediafire.com/download/ovxfo4lbq22dxia/linux-3.13.0-30.54-surfacepro3.tgz](http://www.mediafire.com/download/ovxfo4lbq22dxia/linux-3.13.0-30.54-surfacepro3.tgz)


Any chance there is a newer version of this kernel? I recently purchased the SurfPro 3 and want to spend more time learning Ubuntu and all that it has to offer but at the moment I need to connect a mouse and keyboard through a hub which is annoying and defeats the purpose of the tablet. I tried this kernel but it has no effect on my system.

Greatly apreciate any help you guys can give.

---

### Post by bill_dika on 2014-09-07
Hi OG_KORYONE

I also use arch but am not too sophisticated in dealing with the kernel. How so I go about getting the patch above into my arch kernel?

Any help would be much appreciated.

Thank you.

bill dika

---

### Post by zaileion on 2014-09-18
I just purchased a surface pro 3 last week and followed your instructions to the letter.  Everything went fine including kernel upgrade but nothing has changed for me.  The Bluetooth doesn't work nor does the keyboard/touch pad.  I hope there is a fix for this soon I bought the surface pro 3 with every intention on dual booting.  Does anyone have any updated suggestions or idead?

---

### Post by ColdFusionEESG on 2014-10-03
Hi All,

Looks like some good progress on hardware support - good job to those working on that end!!

I have some questions about what works with what in terms of desktop vs tablet.....if this is the wrong thread admins...plz feel free to move....this seemed like a good spot as the folks in the thread seem to be on the ball ;-)

So I get that Ubuntu can replace Windows on the desktop side (I should mention I typically run Ubuntu as my main OS and then Win 7 in Virtualbox - looking to do the same on the SP3), but I am not clear at all how Ubuntu would work on the tablet side.  By that I mean what would be the tablet OS and what "app store" would I be getting mobile apps from?  On the tablet/smartphone side I have been an Android guy and have never experiences the iOS side of things....nor what Microsoft has to offer....so just not sure how that part works on the SP3.  I susopect part of my lack of understanding is that I am not super clear where desktop and tablet boundaries are in Win 8.1.....or if there really are any...sounds as though it's all in one and not desktop mode vs tablet mode.

My fears are that by installing Ubuntu I am wrecking the typically "tablet" features - touchscreen....mobile apps

Any advice is very very welcome ;-)

Thanks for reading

Cheers

---

### Post by ghaspias2 on 2014-10-04
The same way Windows 8 attempts to be both a tablet OS and a desktop OS, so does Ubuntu. Latest editions have support for touch, and have interfaces designed to work on touch devices. So, you just use your desktop os, in tablet mode, the same way you would use a tablet os. Of course not all applications are tablet-oriented, but in the software store you will find apps suitable for a touch-based use. You could select different desktop environments (Gnome 3 is nice for touch devices) according to the type of use at each moment. Maybe even have two different sessions, and just switch between them according to whether you have the keyboard attached or not. This might require some tweaking, but you will get support from the community.
On a different approach, there is Ubuntu phone and specific apps, but I think these target much smaller devices, and I think it runs under emulation on a Intel-based device (I think Ubuntu phone software is for ARM devices only).

---

### Post by ColdFusionEESG on 2014-10-04
Thanks ghaspias2!

OK...clearly I am a bit out of "touch" (pardon the pun) with the touch progress made in Ubuntu....still on a good old fashioned laptop without touch screen ;-)

So fair enough....that will take care of the touch side of things - awesome.  Great idea to have multilpe sessions for various uses and flavours!

I'm still a little unsure where the mobile apps come from (I'm, thinking traditional Android/Apple mobile apps for phones/tablets....but do get the ARM vs Intel issue).  You mentioned the "software store" and I'm wondering what you mean?  Do you mean the Ubuntu software center? or was that a generic term to mean any of the various "app" stores?  Does Ubuntu software center have mobile apps? If so would they work on an Intel processor?

I guess a big part of my confusion is I assume Microsoft has an "app store" and maybe they don't? or theirs is for Intel and ARM based devices?  If they do and I go to Ubuntu then I potentially lose access to a bunch of apps meant for the device - not sure if that would be good or bad ;-)

Am I kidding myself that this can truly be a desktop and a tablet? or is it more desktop with touch screen and some touch enabled software?

Thanks again!

---

### Post by dominik95-8 on 2014-10-27
Hi guys, 

just to let you know that following the steps here : [http://winaero.com/blog/how-to-install-linux-on-surface-pro-3/](http://winaero.com/blog/how-to-install-linux-on-surface-pro-3/)  ,   

I  got the bluetooth to work and the wifi to run flawlessly (kernel is  3.16 from 14.10 default linux-source with the patch to get the touchpad  behaves as a mouse). 

     When I installed the distribution with  the 14.10 install cd, and when I run the "try ubuntu" from this same  cd, the touchpad is working as a touchpad (i.e. multipoint is working as  expected to scroll internet pages), 
so here are my question : 
- can someone point me to the right direction in order to get the touchpad to work as a touchpad not as a mouse ? 

      Regards,       Dom

---

### Post by ehime on 2014-11-01
> **bill_dika said:**
> Hi OG_KORYONE

I also use arch but am not too sophisticated in dealing with the kernel. How so I go about getting the patch above into my arch kernel?

Any help would be much appreciated.

Thank you.

bill dika

Late response but just saw this, here's how you (generically) can path your kernel

[http://www.linuxdocs.org/HOWTOs/Kernel-HOWTO-6.html](http://www.linuxdocs.org/HOWTOs/Kernel-HOWTO-6.html)

---

### Post by ashok6 on 2014-11-30
Sorry if this is answered elsewhere, but how is suspend/resume support on the Surface Pro 3?

---

### Post by jesper8 on 2014-11-30
Hi,

I just bought my Surface Pro 3 a couple of days ago, and I'm currently trying to find information about how to install linux on it. I tried following this guide ([http://winaero.com/blog/how-to-install-linux-on-surface-pro-3/](http://winaero.com/blog/how-to-install-linux-on-surface-pro-3/)), but only got as far as trying to boot debian using Advanced Startup, but that only booted me into windows. Trying again, the option "Debian" was now named "USB Drive", and didn't work. I then went on to try an install Ubuntu, but got stuck at exactly the same point. I believe I have installed it correctly, but I can't boot it.

My questions: how do I fix the above problem (boot ubuntu on my Surface Pro), where can I best gather information about linux (or more specifically ubuntu) on the Surface Pro 3, and what is the currently best way to install Ubuntu on the Surface Pro 3?

Sorry about the number of questions, and thanks on beforehand!

---

### Post by vaab2 on 2014-12-28
If this enables the touchpad of the Type Cover to be recognise as a pointer device, it doesn't seem to help it being recognise as a... touchpad.
Thus, this prevents the multi-touch gestures to work. Or did I miss something ?

Any suggestions to have the touchpad recognised as a touchpad and not a mouse pointer?

---

### Post by dominik95-8 on 2015-01-05
> **jesper8 said:**
> Hi,

I believe I have installed it correctly, but I can't boot it.



I think I was having the same problem, here is the way I solve my boot problem : [http://ubuntuforums.org/showthread.php?t=2249898](http://ubuntuforums.org/showthread.php?t=2249898) step 6 and 7. I did solve this by entering the surface bios and changing 
the way the boot was working (yes, this does sound weird but it's true).

My /etc/grub.d/40_custom looks like that :
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 8" {
    insmod part_gpt
    insmod fat
    insmod search_fs_uuid
    insmod chain
    search --fs-uuid --no-floppy --set=root XXXX-XXXX
    chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
} 

```

The XXXX-XXXX is the id of my "system" partition showing up with 
```
sudo blkid
```
here is a part of the result of the command :
```
/dev/sda2: LABEL="SYSTEM" UUID="XXXX-XXXX" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="xxxxxxxxxxxxxxxxxxxxxxxxxx"
```

regards,
  Dominique

---

### Post by Knightwise on 2015-02-18
Hey guys,

Running ubuntu 14.04 on my Surface pro one here. Everything (mostly) worked out of the box aside from a few tweaks.
- Type cover 2 keyboard : Works out of the box. Sometimes at bootup it doesn't connect but a quick reboot fixes that. Function buttons, backlight , touchpad : Everything works.
- I've disabled power management on my wifi card to increase my wifi speeds, that helps a lot : [http://ubuntuguide.net/speed-up-wireless-ubuntu-1404](http://ubuntuguide.net/speed-up-wireless-ubuntu-1404)

I only have 2 problems : When I try to suspend the Surface , it just wakes up again. Hibernate is not enabled by default in Ubuntu 14.04 so I would also love to get that working (i've got a 4 gig Swap drive); 

Question : Does anybody have any experience with getting suspend-resume and hibernate working on the Surface pro 1.

---

### Post by bogdan17 on 2015-02-19
> **alicia4542 said:**
> Thank you for testing my modified kernel.

I just noticed that Type Cover 3 support was missing in the kernel. I have just added it to my Surface Pro patch, and built a new kernel.

Download: [http://www.mediafire.com/download/ovxfo4lbq22dxia/linux-3.13.0-30.54-surfacepro3.tgz](http://www.mediafire.com/download/ovxfo4lbq22dxia/linux-3.13.0-30.54-surfacepro3.tgz)

**Forgot to mention, that since the package name and version is the same, you will need to uninstall my previous kernel, if you previously installed it, before installing this new kernel!**
dpkg -r linux-cloud-tools-3.13.0-30-surfacepro linux-headers-3.13.0-30-surfacepro linux-image-3.13.0-30-surfacepro linux-tools-3.13.0-30-surfacepro

Please let me know if it works with your Type Cover 3. If anyone has a Touch Cover 3, and can do a "lsusb", and post the output, I will try to add support for it as well.

On a side note, I am working for unified support (with common kernel and patch) for all Surface Pro versions and accessories, so I think it makes sense to merge this thread into with the older established Surface Pro thread: [http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946).


I am wondering how hard will be to compile this driver into a kext file to be compatible with Mac Os Yosemite? I know I am off topic but it seems you guys are way far ahead than Hacintosh enthusiasts. It seems we are so stack at getting the type cover and mouse pad working in Yosemite Surface Pro 3      :-)

---

### Post by gunksta on 2015-03-19
Good thread. Just installed Vivid onto a brand new i7 version of the Surface Pro 3. Most hardware worked out of the box. After following some of the advice / links here, I was able to get a few more things working. The lack of an operational webcam is really my biggest problem at this point. The trackpad support isn't very good, but it does work (with a tweak or two).

For grins and giggles, I'm setting up a GitHub repo to track my installation and setup.
[URL="https://github.com/Choens/install-optimus"]
https://github.com/Choens/install-optimus[/URL]

My documentation is very much a work in progress. I will add more to it in the coming days as I learn more about the hardware.

---

### Post by Claritux on 2015-03-28
I have posted a kernel at Reddit with links to patches that fixes webcams and multitouch on the trackpad among others:
[http://www.reddit.com/r/SurfaceLinux/comments/30hg2w/sp3_kernel_40rc4_debs_with_patches_for_camera/](http://www.reddit.com/r/SurfaceLinux/comments/30hg2w/sp3_kernel_40rc4_debs_with_patches_for_camera/)
Automatic screen rotation can be achieved using scripts from here:
[https://github.com/AykoPoel/surface3-scripts](https://github.com/AykoPoel/surface3-scripts)

---

### Post by dominik95-8 on 2015-05-08
Hi guys, 

just to let you know that I upgraded to vivid 15.04 : in the end everything is working almost fine (rotation,multitouch,camera,suspend). The wifi is not always on at the first start but suspending/resuming the SP3 does it for me. 

Thank you gunksta and Claritux for your links.

Thank you

---

### Post by Wrkcncanter on 2015-05-11
> **dominik95-8 said:**
> Hi guys, 

just to let you know that I upgraded to vivid 15.04 : in the end everything is working almost fine (rotation,multitouch,camera,suspend). The wifi is not always on at the first start but suspending/resuming the SP3 does it for me. 

Thank you gunksta and Claritux for your links.

Thank you

I am thinking about purchasing a Surface Pro 3 with the type cover. I've read through this thread and I'd like to know from your experience -- what do you have to do after installing vivid 15.04 to get everything working? (e.g. are the webcam fix and auto-rotate scripts still necessary?)

Thanks!

EDIT: Did you install 15.04 and then compile your own kernel like they do here? [http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all](http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all)

---

### Post by dominik95-8 on 2015-05-13
> **Wrkcncanter said:**
> I am thinking about purchasing a Surface Pro 3 with the type cover. I've read through this thread and I'd like to know from your experience -- what do you have to do after installing vivid 15.04 to get everything working? (e.g. are the webcam fix and auto-rotate scripts still necessary?)

Thanks!

EDIT: Did you install 15.04 and then compile your own kernel like they do here? [http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all](http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all)

Hi Wrkcncanter,

I upgraded from 14.10 to 15.04 but I guess that installing will be the same. 
I was surprised that I had nothing to do to get the basic stuffs working (keyboard+touchpad) with the 3.19.0-16-generic.efi.signed kernel that comes with the install. 

I recompiled a 4.X kernel with the patches to get the suspend/resume function + the buttons (volume button+power button) + the multitouch + camera. 
I don't know if the camera patch is still needed (the patch just adds the vendor number and the product number to the kernel so it could be integrated to main stream easily but I did not check).
I think the scripts are necessary for the screen rotation. I did not look at making it started at boot time (a script in /etc/xdg/autostart/ will probably be enough).

I found in both cases (3.19 and the compiled 4.X kernel) that the wifi is not stable. Even with the firmware to get the bluetooth working git clone git://git.marvell.com/mwifiex-firmware.git, mkdir -p /lib/firmware/mrvl/, cp mwifiex-firmware/mrvl/* /lib/firmware/mrvl/.

To build the 4.X kernel, I followed a mix of those urls :
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
[https://github.com/rubiojr/surface3-kernel](https://github.com/rubiojr/surface3-kernel)
[http://www.reddit.com/r/SurfaceLinux/comments/30hg2w/sp3_kernel_40rc4_debs_with_patches_for_camera/](http://www.reddit.com/r/SurfaceLinux/comments/30hg2w/sp3_kernel_40rc4_debs_with_patches_for_camera/) <- for the patches, if you are not so easy compiling the kernel, there are links to precompiled kernels

The autorotate is working with the previously mentionned script : [https://github.com/AykoPoel/surface3-scripts](https://github.com/AykoPoel/surface3-scripts)


To note that the only glitches I had installing the 14.10 were to display grub at boot time (see step 6, 7 from [http://ubuntuforums.org/showthread.php?t=2249898](http://ubuntuforums.org/showthread.php?t=2249898) if it happens to you) and to disable the windows bitlocker, to resize the ssd as I wanted (I re-enabled bitlocker afterwards) :
/dev/sda1       2048    739327    737280   360M Windows recovery environment
/dev/sda2     739328   1148927    409600   200M EFI System
/dev/sda3    1148928   1411071    262144   128M Microsoft reserved
/dev/sda4    1411072 209537023 208125952  99,2G Microsoft basic data
/dev/sda5  489058304 500117503  11059200   5,3G Windows recovery environment
/dev/sda6  258689024 259080191    391168   191M Linux filesystem
/dev/sda7  259080192 267079679   7999488   3,8G Linux swap
/dev/sda8  267079680 489058303 221978624 105,9G Linux filesystem

++dom

---

### Post by ronald-p on 2015-07-15
> **dominik95-8 said:**
> 
I found in both cases (3.19 and the compiled 4.X kernel) that the wifi is not stable. Even with the firmware to get the bluetooth working git clone git://git.marvell.com/mwifiex-firmware.git, mkdir -p /lib/firmware/mrvl/, cp mwifiex-firmware/mrvl/* /lib/firmware/mrvl/.



My wifi was unusable until I disabled power management. You may want to give that a try.

```
sudo iwconfig mlan0 power off
```

---

### Post by dominik95-8 on 2015-07-15
> **ronald-p said:**
> My wifi was unusable until I disabled power management. You may want to give that a try.

```
sudo iwconfig mlan0 power off
```

Thank you for the tip ronald-p, I'm giving it a try right now.

++dom

---

### Post by backl_ash on 2015-07-16
I just installed 15.04 and everything worked right out of the box except the keys on my type cover. The touchpad works fine, with gestures and everything. But I'm currently typing on a USB keyboard. Any advice?

---

### Post by dominik95-8 on 2015-07-16
> **backl_ash said:**
> I just installed 15.04 and everything worked right out of the box except the keys on my type cover. The touchpad works fine, with gestures and everything. But I'm currently typing on a USB keyboard. Any advice?

It happens time to time (mostly when I restart from windows to Linux without shuting down). 

Try to remove / replug the keyboard, if it does not work try to shutdown (not to restart, really shutdown) and launch ubuntu again.

---

### Post by backl_ash on 2015-07-16
So I did all of that to no avail and now I'm having bigger problems.
copypasta from other help requests:


[LIST]
[*]I installed Ubuntu on an external HD, made the main partition 150g, and the swap 2g.
[*]The type cover touch pad worked, but the keyboard didn't.
[*]Rebooted to go back to Windows and it kept trying to launch Ubuntu.
[*]I hard reset and that sent me to the grub rescue. Googled, got it to start a live version from USB, repaired the boot loader. Rebooted. Grub rescue.
[*]Power cycled, it let me chose the Windows Boot Manager, got into Windows. YAY
[*]Rebooted... it still tries to launch Ubuntu even with the HD unplugged...
[/LIST]

---

### Post by dominik95-8 on 2015-07-17
> **backl_ash said:**
> So I did all of that to no avail and now I'm having bigger problems.
copypasta from other help requests:


[LIST]
[*]I installed Ubuntu on an external HD, made the main partition 150g, and the swap 2g. 
[*]The type cover touch pad worked, but the keyboard didn't. 
[*]Rebooted to go back to Windows and it kept trying to launch Ubuntu. 
[*]I hard reset and that sent me to the grub rescue. Googled,  got it to start a live version from USB, repaired the boot loader.  Rebooted. Grub rescue. 
[*]Power cycled, it let me chose the Windows Boot Manager, got into Windows. YAY 
[*]Rebooted... it still tries to launch Ubuntu even with the HD unplugged... 
[/LIST]


Hi backl_ash, 

Before you start, be aware that modifying any grub configuration requires you to be carreful as it can alter the boot of your system.

1) Where did you install the bootloader ? Installing it on a removable device is a bad idea, better setting an active partition on a drive that stays attached to the SP3 (e.g. some sdaX partition). Also, you must have your /boot partition available any time you boot because it contains the grub config files and the kernel, so it must also be on the same 

2) It sounds like the windows partition is not part of the grub.conf file. Here is a quote of a post about my grub.cfg file :

> **dominik95-8 said:**
> I think I was having the same problem, here is the way I solve my boot problem : [http://ubuntuforums.org/showthread.php?t=2249898](http://ubuntuforums.org/showthread.php?t=2249898) step 6 and 7. I did solve this by entering the surface bios and changing 
the way the boot was working (yes, this does sound weird but it's true).

My /etc/grub.d/40_custom looks like that :
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 8" {
    insmod part_gpt
    insmod fat
    insmod search_fs_uuid
    insmod chain
    search --fs-uuid --no-floppy --set=root XXXX-XXXX
    chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
} 

```

The XXXX-XXXX is the id of my "system" partition showing up with 
```
sudo blkid
```
here is a part of the result of the command :
```
/dev/sda2: LABEL="SYSTEM" UUID="XXXX-XXXX" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="xxxxxxxxxxxxxxxxxxxxxxxxxx"
```

regards,
  Dominique

You can modify the default partition to boot in, look at the grub-install command to see how and where the grub boot loader is installed.
You need to install your grub partition on an active partition.

I hope it will help you. 

Regards,

---

### Post by dominik95-8 on 2016-01-07
Hi,
After a Surface Pro 3 disaster (the machine won't boot correctly even in windows or from usb, random freezes at boot, random pixel on screen,.. ), I got a new one from Microsoft support (3 weeks before the warranty ended :popcorn:).

For now, I installed ubuntu 15.10 on a SD card. I have a problem and a question.

* My problem is that the wifi is not working :
- neither with the default 4.2.x kernel and the default firmware
- nor with the default 4.2.x kernel and the firmware from git://git.marvell.com/mwifiex-firmware.git
- nor with linux-headers-4.3.3-040303_4.3.3-040303.201512150130_all.deb  linux-headers-4.3.3-040303-generic_4.3.3-040303.201512150130_amd64.deb  linux-image-4.3.3-040303-generic_4.3.3-040303.201512150130_amd64.deb mainstream kernel and the default firmware
- nor with the 4.3 mainstream kernel and the firmware from git://git.marvell.com/mwifiex-firmware.git
The kernel log shows :
```

mwifiex_pcie 0000:01:00.0: Incompatible network settings
mwifiex_pcie 0000:01:00.0: info: association to bssid MASKED failed
mwifiex_pcie 0000:01:00.0: info: trying to associate to 'MASKED' bssid MASKED
mwifiex_pcie 0000:01:00.0: info: mwifiex_is_network_compatible: failed: wpa_ie=0xdd wpa2_ie=0x0 WEP=d    WPA=d WPA2=d EncMode=0xfac04 privacy=0x1
mwifiex_pcie 0000:01:00.0: Incompatible network settings
mwifiex_pcie 0000:01:00.0: info: association to bssid MASKED failed
mwifiex_pcie 0000:01:00.0: info: trying to associate to 'MASKED' bssid MASKED
mwifiex_pcie 0000:01:00.0: info: mwifiex_is_network_compatible: failed: wpa_ie=0xdd wpa2_ie=0x0 WEP=d    WPA=d WPA2=d EncMode=0xfac04 privacy=0x1
mwifiex_pcie 0000:01:00.0: Incompatible network settings
mwifiex_pcie 0000:01:00.0: info: association to bssid MASKED failed
IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready

```

I googled "mwifiex_pcie 0000:01:00.0: Incompatible network settings" without success. 
I need to add that I had also this problem with 14.10 and 4.2 kernel but not with 3.19 if I remember well with the previous surface.

Do you have any idea of the problem ?


* My question(s) is (are) about the EFI boot process. 
I first installed the sd card without a EFI partition but I was just not glade to have the grub minimal bash-like prompt when removing the sdcard. I needed to enter "exit" + press enter each time I boot the device in order to boot into windows.
Is there a way to prevent this prompt from appearing when the linux sd card is missing ?

Then I decided to try the installation with an EFI partition on the sd card. When the secure boot is turned on, I got a "invalid signature" at the boot (even if I copied the file from the surface EFI partition to the sd card EFI partition). I thought that just copying the files won't modify the signatures. Perhaps there are keys dependant on boot devices ...

Disabling the secure boot allows me to boot in ubuntu without problem. But is there a way to get the sdcard EFI partition to work with secure boot ?



Edit:Just to add that I am using a USB3 ethernet adapter and since I use kernel 4.3.3, it has worked every time (that was not the case previously) 


Thank you, 

 ++dom

---

### Post by dominik95-8 on 2016-01-18
> **dominik95-8 said:**
> 
* My problem is that the wifi is not working :
- neither with the default 4.2.x kernel and the default firmware
- nor with the default 4.2.x kernel and the firmware from git://git.marvell.com/mwifiex-firmware.git
- nor with linux-headers-4.3.3-040303_4.3.3-040303.201512150130_all.deb  linux-headers-4.3.3-040303-generic_4.3.3-040303.201512150130_amd64.deb  linux-image-4.3.3-040303-generic_4.3.3-040303.201512150130_amd64.deb mainstream kernel and the default firmware
- nor with the 4.3 mainstream kernel and the firmware from git://git.marvell.com/mwifiex-firmware.git
The kernel log shows :
```

mwifiex_pcie 0000:01:00.0: Incompatible network settings
mwifiex_pcie 0000:01:00.0: info: association to bssid MASKED failed
mwifiex_pcie 0000:01:00.0: info: trying to associate to 'MASKED' bssid MASKED
mwifiex_pcie 0000:01:00.0: info: mwifiex_is_network_compatible: failed: wpa_ie=0xdd wpa2_ie=0x0 WEP=d    WPA=d WPA2=d EncMode=0xfac04 privacy=0x1
mwifiex_pcie 0000:01:00.0: Incompatible network settings
mwifiex_pcie 0000:01:00.0: info: association to bssid MASKED failed
mwifiex_pcie 0000:01:00.0: info: trying to associate to 'MASKED' bssid MASKED
mwifiex_pcie 0000:01:00.0: info: mwifiex_is_network_compatible: failed: wpa_ie=0xdd wpa2_ie=0x0 WEP=d    WPA=d WPA2=d EncMode=0xfac04 privacy=0x1
mwifiex_pcie 0000:01:00.0: Incompatible network settings
mwifiex_pcie 0000:01:00.0: info: association to bssid MASKED failed
IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready

```

I googled "mwifiex_pcie 0000:01:00.0: Incompatible network settings" without success. 
I need to add that I had also this problem with 14.10 and 4.2 kernel but not with 3.19 if I remember well with the previous surface.

Do you have any idea of the problem ?


I solved this problem modifying the wifi parameter. I have a french isp (free). For people having the same problem, note that it is not enough to setup the wifi in the free web console, you need to log in the freebox web interface and change the protocol from wpa to wpa2.

My EFI question remains ...


Regards,
  Dominique

---

### Post by josie2 on 2017-01-04
> **alicia4542 said:**
> Thank you for also quickly testing...

Hmm, so with this newer kernel, the type cover 3 keyboard works, but its trackpad does not work anymore.  Sorry about that.

I will need to examine the source to see why, and get back to you.

To help troubleshoot, could you please run this command and post the output?
**dmesg | grep -i 045e**

Please let me know if you find any other issues with the newer kernel.

I will be happy to post my modified patch, once we get it fully working with the Type Cover 3.


[    2.202557] usb 1-3: New USB device found, idVendor=045e, idProduct=07dc
[    2.209875] input: Microsoft Surface Type Cover as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:045E:07DC.0001/input/input2
[    2.269141] microsoft 0003:045E:07DC.0001: input,hiddev0,hidraw0: USB HID v1.11 Keyboard [Microsoft Surface Type Cover] on usb-0000:00:14.0-3/input0
[    2.474687] usb 1-7: New USB device found, idVendor=045e, idProduct=07be
[    2.750753] usb 1-8: New USB device found, idVendor=045e, idProduct=07bf
[    7.959754] uvcvideo: Found UVC 1.50 device Microsoft LifeCam Front (045e:07be)
[    7.960246] uvcvideo: Found UVC 1.50 device Microsoft LifeCam Rear (045e:07bf)

---

### Post by josie2 on 2017-01-04
> **bowmessage said:**
> Hey all,

Figured I would kick off a Surface Pro 3 thread. Running an i5 128gb model with a type cover keyboard. So far the only issue preventing me form using Ubuntu as a daily driver is the lack of keyboard support for the type cover. The trackpad on the type cover works well, so that's a start.

I wonder if anyone knows how to modify the patch provided at [http://linux-kernel.2935.n7.nabble.com/PATCH-Add-HID-s-to-hid-microsoft-driver-of-Surface-Type-Touch-Cover-2-to-fix-bug-td790242.html](http://linux-kernel.2935.n7.nabble.com/PATCH-Add-HID-s-to-hid-microsoft-driver-of-Surface-Type-Touch-Cover-2-to-fix-bug-td790242.html) to support the new type cover.

Thanks for any help anyone provides, and I'll be looking into compiling my own kernel in the coming week. Good luck everyone!

Edit: Also thought I should note that I used the most recent patched kernel listed in this thread about type covers for the 1st and 2nd models ([http://ubuntuforums.org/showthread.php?t=2183946&page=13](http://ubuntuforums.org/showthread.php?t=2183946&page=13)) with no luck.

Edit 2: Just installed a bunch of updates from my Windows partition. One of them overwrote my bootloader and I had to boot from my Ubuntu USB installer and run boot-repair to reinstall GRUB. I also noticed that the updates must have changed the firmware of the type cover: the trackpad has stopped working. Now only the pen or an external mouse will work as a pointing device.

Edit 3: Turns out I was wrong about the trackpad no longer working. It just seems to not work on some boots. More research required...


I fixed the touchpad by adding the following lines to /usr/share/X11/xorg.conf.d/10-evdev.conf:
Section "InputClass"
    Identifier "Surface Pro 3 cover"
    MatchIsPointer "on"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    Option "vendor" "045e"
    Option "product" "07dc"
    Option "IgnoreAbsoluteAxes" "True"
EndSection
This fix was discussed at [https://github.com/nuclearsandwich/surface3-archlinux/issues/4](https://github.com/nuclearsandwich/surface3-archlinux/issues/4) and [http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all](http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all).
In my case, the type cover stopped working after upgrading to 15.10 because the upgrade overwrote /usr/share/X11/xorg.conf.d/10-evdev.conf.
I'm not sure whether this matters, but there are two type cover USB IDs, 0x07de and 0x07e2, as discussed at [https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/](https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/). Maybe this fix only works for one of the two IDs.

---

### Post by daraghfi on 2017-01-16
FWIW, I read somewhere that removing the synaptics package would enable the touchpad, and it worked.
However it does not support multi-touch, and directly contradicts 
[https://wiki.archlinux.org/index.php/Microsoft_Surface_Pro_3#Enabling_Touchpad](https://wiki.archlinux.org/index.php/Microsoft_Surface_Pro_3#Enabling_Touchpad) 

Cheers,

Daragh

> **josie2 said:**
> I fixed the touchpad by adding the following lines to /usr/share/X11/xorg.conf.d/10-evdev.conf:
Section "InputClass"
    Identifier "Surface Pro 3 cover"
    MatchIsPointer "on"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    Option "vendor" "045e"
    Option "product" "07dc"
    Option "IgnoreAbsoluteAxes" "True"
EndSection
This fix was discussed at [https://github.com/nuclearsandwich/surface3-archlinux/issues/4](https://github.com/nuclearsandwich/surface3-archlinux/issues/4) and [http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all](http://askubuntu.com/questions/620726/ubuntu-on-surface-pro-3-or-linux-at-all).
In my case, the type cover stopped working after upgrading to 15.10 because the upgrade overwrote /usr/share/X11/xorg.conf.d/10-evdev.conf.
I'm not sure whether this matters, but there are two type cover USB IDs, 0x07de and 0x07e2, as discussed at [https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/](https://www.reddit.com/r/SurfaceLinux/comments/3dzriz/info_surface_pro_3_patch_status/). Maybe this fix only works for one of the two IDs.

---

### Post by rlanders on 2017-02-12
> **daraghfi said:**
> FWIW, I read somewhere that removing the synaptics package would enable the touchpad, and it worked.
However it does not support multi-touch, and directly contradicts 
[https://wiki.archlinux.org/index.php/Microsoft_Surface_Pro_3#Enabling_Touchpad](https://wiki.archlinux.org/index.php/Microsoft_Surface_Pro_3#Enabling_Touchpad) 

Cheers,

Daragh

I was in the same boat, I tested this with several different type covers:

Try using this in your conf file
```

Section "InputClass"
	Identifier "Surface Pro 3 cover"
	MatchIsPointer "on"
	MatchDevicePath "/dev/input/event*"
	Driver "evdev"
	Option "vendor" "045e"
	Option "product" "07e2"
	Option "IgnoreAbsoluteAxes" "True"
EndSection

Section "InputClass"
        Identifier "Surface Pro 3 cover"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "vendor" "045e"
        Option "product" "07e4"
        Option "IgnoreAbsoluteAxes" "True"
EndSection

Section "InputClass"
        Identifier "Surface Pro 3 cover"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "vendor" "045e"
        Option "product" "07e8"
        Option "IgnoreAbsoluteAxes" "True"
EndSection

Section "InputClass"
        Identifier "Surface Pro 3 cover"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "vendor" "045e"
        Option "product" "07cd"
        Option "IgnoreAbsoluteAxes" "True"
EndSection

Section "InputClass"
        Identifier "Surface Pro 3 cover"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "vendor" "045e"
        Option "product" "07de"
        Option "IgnoreAbsoluteAxes" "True"
EndSection

```

---

### Post by mudguts2 on 2017-02-26
I just installed Ubuntu Studio 16.04 LTS onto my Surface Pro 3.  Not too many issues so far except for the camera.  I can't find an app that seems to make it work yet.  Maybe I'll try pidgeon or Skype to see if that opens it up.

---

