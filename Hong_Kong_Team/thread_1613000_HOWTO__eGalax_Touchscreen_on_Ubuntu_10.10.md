---
title: "HOWTO : eGalax Touchscreen on Ubuntu 10.10"
date: 2010-11-03
forum: Hong Kong Team
---

### Post by samiux on 2010-11-03
The following tutorial is about how to make eGalax Touchscreen working on Ubuntu 10.10.

[Here you are ...]("http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html")

Samiux

---

### Post by dirkbo on 2010-11-19
Thank you, that works perfectly :D

---

### Post by mising on 2010-11-19
Unfortunately, it still does not work for me.
I have a HP TX1220us, and my lsusb output shows the same info as yours. When I touch my screen with the stylus, the cursor jumps up to the top left corner, and will not move.  I cannot finish the calibration because I cannot touch the cross-hairs. This is the same behavior I have with a fresh install of 10.10.
Any ideas? Any configs or output you would need to see?
Thank you

---

### Post by samiux on 2010-11-19
> **mising said:**
> Unfortunately, it still does not work for me.
I have a HP TX1220us, and my lsusb output shows the same info as yours. When I touch my screen with the stylus, the cursor jumps up to the top left corner, and will not move.  I cannot finish the calibration because I cannot touch the cross-hairs. This is the same behavior I have with a fresh install of 10.10.
Any ideas? Any configs or output you would need to see?
Thank you

Did you complete Step 4 to 6?

---

### Post by mising on 2010-11-19
Actually after a little more poking around, I found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625511](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625511)

Basically, there are some extra entries in the kernel that confuse
the touchscreen and have been fixed in the 2.6.37rc1 kernel.  
I updated my kernel to 2.6.37rc2 and voila! touch screen works, 
but not very accurate.  So after performing your steps again, 
I just have to work on tweaking the calibration.  Its great in the center, 
but off by about half an inch at the edges.  
Overall, YAY!
Thanks again

---

### Post by samiux on 2010-11-19
> **mising said:**
> Actually after a little more poking around, I found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625511](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625511)

Basically, there are some extra entries in the kernel that confuse
the touchscreen and have been fixed in the 2.6.37rc1 kernel.  
I updated my kernel to 2.6.37rc2 and voila! touch screen works, 
but not very accurate.  So after performing your steps again, 
I just have to work on tweaking the calibration.  Its great in the center, 
but off by about half an inch at the edges.  
Overall, YAY!
Thanks again

Thanks for your information.

However, mine (Gigabyte TouchNote T1028X) is working fine with my settings.

---

### Post by mising on 2010-11-19
Calibrated!
Had to paste the results from xinput_calibrator into /etc/X11/xorg.conf also.

Know how to activate right-click with stylus?

Thanks again for the great tutorial!

---

### Post by samiux on 2010-11-19
> **mising said:**
> Calibrated!
Had to paste the results from xinput_calibrator into /etc/X11/xorg.conf also.

Know how to activate right-click with stylus?

Thanks again for the great tutorial!

Pointed the stylus to the target and right-click the mouse pad at the same time.

---

### Post by TemplarKnight on 2010-11-20
This almost works for me with my Lilliput EBY-701 touchscreen.
BUT...
I've followed exactly the wiki instructions and the device is identified. The pointer moves when I touch the screen, however not where I'm pointing. Its seems totally miscalibrated and can't see any improvement when using the output from xinput_calibrator (don't even know if the points it's telling me are correct).

Here is lsusb for the device:
```
Bus 002 Device 011: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
```

Here is /var/log/Xorg.0.log when I connect the device:

```
[   921.769] (II) config/udev: Adding input device eGalax Inc. Touch (/dev/input/mouse1)
[   921.769] (II) No input driver/identifier specified (ignoring)
[   921.769] (II) config/udev: Adding input device eGalax Inc. Touch (/dev/input/event5)
[   921.769] (**) eGalax Inc. Touch: Applying InputClass "evdev pointer catchall"
[   921.769] (**) eGalax Inc. Touch: always reports core events
[   921.769] (**) eGalax Inc. Touch: Device: "/dev/input/event5"
[   921.776] (II) eGalax Inc. Touch: Found 3 mouse buttons
[   921.776] (II) eGalax Inc. Touch: Found absolute axes
[   921.776] (II) evdev-grail: failed to open grail, no gesture support
[   921.776] (II) eGalax Inc. Touch: Found x and y absolute axes
[   921.776] (II) eGalax Inc. Touch: Configuring as mouse
[   921.776] (**) eGalax Inc. Touch: YAxisMapping: buttons 4 and 5
[   921.776] (**) eGalax Inc. Touch: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   921.776] (II) XINPUT: Adding extended input device "eGalax Inc. Touch" (type: MOUSE)
[   921.776] (II) eGalax Inc. Touch: initialized for absolute axes.
[   921.777] (II) config/udev: Adding input device eGalax Inc. Touch (/dev/input/mouse2)
[   921.777] (II) No input driver/identifier specified (ignoring)
[   921.777] (II) config/udev: Adding input device eGalax Inc. Touch (/dev/input/js1)
[   921.777] (II) No input driver/identifier specified (ignoring)
[   921.777] (II) config/udev: Adding input device eGalax Inc. Touch (/dev/input/event6)
[   921.777] (**) eGalax Inc. Touch: Applying InputClass "evdev tablet catchall"
[   921.777] (**) eGalax Inc. Touch: always reports core events
[   921.777] (**) eGalax Inc. Touch: Device: "/dev/input/event6"
[   921.788] (II) eGalax Inc. Touch: Found absolute axes
[   921.788] (II) evdev-grail: failed to open grail, no gesture support
[   921.788] (II) eGalax Inc. Touch: Found x and y absolute axes
[   921.788] (II) eGalax Inc. Touch: Found absolute tablet.
[   921.788] (II) eGalax Inc. Touch: Configuring as tablet
[   921.788] (**) eGalax Inc. Touch: YAxisMapping: buttons 4 and 5
[   921.788] (**) eGalax Inc. Touch: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   921.788] (II) XINPUT: Adding extended input device "eGalax Inc. Touch" (type: TABLET)
[   921.788] (II) eGalax Inc. Touch: initialized for absolute axes.
```

Any help please?

PS.
I've also tried the official eGalax drivers from: [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)
to no avail (used to work until Xorg 1.8, for 1.9 they don't have the module compiled :( )

---

### Post by TemplarKnight on 2010-11-20
Got it calibrated using /etc/X11/xorg.conf.d/ instead of /usr/lib/X11/xorg.conf.d/!!

Now on to find a way for right click!

---

### Post by samiux on 2010-11-21
> **TemplarKnight said:**
> Got it calibrated using /etc/X11/xorg.conf.d/ instead of /usr/lib/X11/xorg.conf.d/!!

Now on to find a way for right click!

That's strange!  Anyway, I am glad to hear that your hardware is working fine.

---

### Post by viktorh on 2011-01-02
Hi,

first - good job, thank you.

Anyway, my issue seems to be little different - my eGalax Touch screen is connected via PS/2 interface (Umid mbook SE aka Unkyo BX407A4). I followed your steps carrefully, but no success.

Do you have any idea how to modify your "howto?

---

### Post by samiux on 2011-01-04
> **viktorh said:**
> Hi,

first - good job, thank you.

Anyway, my issue seems to be little different - my eGalax Touch screen is connected via PS/2 interface (Umid mbook SE aka Unkyo BX407A4). I followed your steps carrefully, but no success.

Do you have any idea how to modify your "howto?

Sorry, I have no idea for PS/2 interface.

---

### Post by Non.Cents on 2011-01-06
samiux, I have a different device than you, a dell duo instead of a Gigabyte TouchNote T1028X, but i was hoping either you could help me or point me in the right direction. Your tutorial worked well for me for single touch, but i am not able to make multi touch work on my device. It is within the capabilities of the device (works in windows), i just cant seem to make it work. Do you have any ideas? :confused:

---

### Post by samiux on 2011-01-06
> **Non.Cents said:**
> samiux, I have a different device than you, a dell duo instead of a Gigabyte TouchNote T1028X, but i was hoping either you could help me or point me in the right direction. Your tutorial worked well for me for single touch, but i am not able to make multi touch work on my device. It is within the capabilities of the device (works in windows), i just cant seem to make it work. Do you have any ideas? :confused:

I have no device with multi-touch feature.  I heard that utouch, which is mentioned at Step 7 on my tutorial, is working for multi-touch.  I think you can try it.  Or, combine with the previous Steps, maybe.

---

### Post by Non.Cents on 2011-01-07
Bummer. I did indeed install utouch, the problem is that the second poc is not even recognized, it does nothing at all so i need more than just the gestures. Thanks anyways, and thanks for the single touch answer.

---

### Post by AcKyL on 2011-03-13
I've been poking around alot with this issue and the touchscreen. And got the solution of a big mix of everything. :)

I have an external touchscreen (noname cr*p) running on a sh*tty HP laptop that's about 7 years old. But it got its purpose in life :)

I tried out the TouchKit software first off, 'cause i've been running it in LinuxICE before. No luck. Found out that i got the error msg "unable to enumerate usb device on port X". I tried every solution on the web, taking advice on that it's the motherboard that can't deliver enough power (tried with a usb hubb with external power supply with no luck), killing the echi_hcd drivers, etc, but found that it was just a bad USB cable...
Anyway, the touchscreen didn't work. The pointer jumped to the top left corner every time i touched the screen. So i searched the web and found, among other, this forum thread.
Tried the solution according to the description, but failed.
Then i installed the kernel 2.6.37-rc1, and it started to work! Great...was my first thought. Then i noticed i had no network connection. I searched the web about it, found nothing good of use, 'cause b44 and b43 driver has issues by default. Tried reinstalling the kernel, with no sucess. Tried installing 2.6.37-rc2 with no sucess. Poked around a bit and found that it turned out that the drivers (b44 and b43) for my ethernet and wireless card was blacklisted by default. Fixed that by commenting them out.
Then i had the issue with calibrating the screen. It worked like a charm once i ran xinput_calibration, but went back to default after every reboot. Moved the xorg.conf.d folder to /etc/X11 instead of /usr/lib/X11 with no luck. I created the file 99-calibration.conf (something like that) according to the instructions from xinput_calibration, rebooted and ended up with a black screen once X should start. Responded to ctrl+alt+del with no hesitation though.
Then I had the issue with GRUB2 not responding to my SHIFT input, so i couldn't get into recovery mode... 1 second from the push of the reinstall the whole OS, I came up with one solution. When you interrupt the boot (just shutting the computer down, pulling the plugg or whatever) GRUB2 shows you the GrubMenu by default! Perfect! :) So i entered the shell from recoverymode, removed the 90-cali* file from xorg.conf.d and rebooted. Sucess!
Read the thread here once again and noticed mising's reply about putting the calibration info in /etc/X11/xorg.conf file instead of the seperate one. What do you know...It worked like a charm :)

Hope this helps someone else that has these issues. Took me a whole day to get this fixed... :)

Summary what i should do for the next reinstall on the computer:
- Install Ubuntu Netbook Edition
- Get Linux Kernel 2.6.37-rc1
- Comment out the network drivers in the blacklist (/etc/modprobe.d/blacklist-bcm43.conf)
- Follow the instructions from [Samiux]("http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html")
- Run xinput_calibration and put the calibration settings in /etc/X11/xorg.conf
- Live long and pass on your knowledge for others ):P

//AcKyL

---

### Post by gb1138 on 2011-04-04
Hello,
I have followed the steps to 6.  I get the below errors on step 5 and 6.

 laptop ~ $ sudo dpkg -i xinput-calibrator_0.7.5-1ubuntu1_i386.deb
(Reading database ... 54527 files and directories currently installed.)
Preparing to replace xinput-calibrator 0.7.5-1ubuntu1 (using xinput-calibrator_0.7.5-1ubuntu1_i386.deb) ...
Unpacking replacement xinput-calibrator ...
dpkg: dependency problems prevent configuration of xinput-calibrator:
 xinput-calibrator depends on libcairomm-1.0-1 (>= 1.6.4); however:
  Package libcairomm-1.0-1 is not installed.
 xinput-calibrator depends on libglibmm-2.4-1c2a (>= 2.24.0); however:
  Package libglibmm-2.4-1c2a is not installed.
 xinput-calibrator depends on libgtkmm-2.4-1c2a (>= 1:2.20.0); however:
  Package libgtkmm-2.4-1c2a is not installed.
dpkg: error processing xinput-calibrator (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Errors were encountered while processing:
 xinput-calibrator

-laptop ~ $ xinput_calibrator
xinput_calibrator: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory


I have an Asus eeepc 4g with the very latest Peppermint Linux.  Any help would be wonderful :)..

Thanks,
gb1138

---

### Post by peterpall on 2011-07-03
The above error messages indicate that some of the packages your linux knows about have version numbers that indicate that they are mutually incompatible to each other. Normally this happens only on development versions of a linux when new versions of some packages have already been uploaded while other packages still need the old ones.

Try to do a 
sudo apt-get update
and repeat the step that output the dependency error messages. Chances are high that the problem is already fixed by now. And if that is true the above command fixes the problem by automatically downloading a new package list.

---

