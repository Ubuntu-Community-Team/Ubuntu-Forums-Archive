---
title: "Want to use my phone as storage device for ubuntu"
date: 2014-06-18
forum: Hardware
---

### Post by kelly4 on 2014-06-18
I thought this might be an better thread to ask a android question regarding ubuntu detecting my android gingerbread version 2.3.7

I would like some help getting my ZTE Concord phone to be detected by ubuntu 14.04 on my acer aspire one 255E

I would like to transfer files from phone to computer and vice versa

Phone charges but no detection of phone

Thank you kindly,

[-o

---

### Post by jeremy31 on 2014-06-18
It has been a while since I had a phone with gingerbread, but IIRC there were some USB options, like charge only that may prevent you from connecting with the usb cable but I do think the phone should give a notification when the cable is plugged in

---

### Post by lisati on 2014-06-18
> **jeremy31 said:**
> It has been a while since I had a phone with gingerbread, but IIRC there were some USB options, like charge only that may prevent you from connecting with the usb cable but I do think the phone should give a notification when the cable is plugged in

My experience with android devices has been similar, with a notification on the phone when the cable is plugged in, and the option to allow usb connections. My current main phone has android 2.3.6

---

### Post by kelly4 on 2014-06-19
> **jeremy31 said:**
> It has been a while since I had a phone with gingerbread, but IIRC there were some USB options, like charge only that may prevent you from connecting with the usb cable but I do think the phone should give a notification when the cable is plugged in

> **lisati said:**
> My experience with android devices has been similar, with a notification on the phone when the cable is plugged in, and the option to allow usb connections. My current main phone has android 2.3.6

Thanks for your comments

I would like to know where to start to solve this problem

Other phones  with other OS's work fine and detect microSD

Should I be looking for a driver or package type?

I looked in the android settings and saw nothing on to turn on MTP or otherwise

Is there an device setting in ubuntu that sets MTP protocol?

Thanks

:guitar:

---

### Post by jeremy31 on 2014-06-19
Have you enabled USB debugging on the phone and try more than just one USB cable/port

---

### Post by Mark Phelps on 2014-06-19
You only need to use MTP if your Android phone is running ICS or newer -- and that's because Google REMOVED the Mass Storage option from Android starting with that version.

With older versions, when you plug a USB cable, already connected to the PC, into the phone, you should get a screen opening on the phone with options.  Choose the Mass Storage option -- and the PC will mount the filesystems, one for the internal one to the phone, and a second (if you have a MicroSD card) for the SD card filesystem.

You might have to enable the USB Debugging option on  the phone if it's not presenting you a selection screen.

---

### Post by kelly4 on 2014-06-19
> **Mark Phelps said:**
> You only need to use MTP if your Android phone is running ICS or newer -- and that's because Google REMOVED the Mass Storage option from Android starting with that version.

With older versions, when you plug a USB cable, already connected to the PC, into the phone, you should get a screen opening on the phone with options.  Choose the Mass Storage option -- and the PC will mount the filesystems, one for the internal one to the phone, and a second (if you have a MicroSD card) for the SD card filesystem.

You might have to enable the USB Debugging option on  the phone if it's not presenting you a selection screen.

Hi, I do not get a screen with options

[Going to try this]("http://www.oneclickroot.com/enable-usb-debugging-for-android/")

Thanks

---

### Post by jeremy31 on 2014-06-19
[http://www.gleescape.com/posts/1793](http://www.gleescape.com/posts/1793) looks like it should work

---

### Post by kelly4 on 2014-06-19
> **jeremy31 said:**
> [http://www.gleescape.com/posts/1793](http://www.gleescape.com/posts/1793) looks like it should work

It didn't work, am trying [this]("http://forum.xda-developers.com/showthread.php?t=1800335") :o...lol

---

### Post by WinEunuchs2Unix on 2014-06-19
My LG c800q is running an older 2.3.6 gingerbread and when I plug it in the green robot pops up and clicking yes takes you to the file manager where all the SD Card music files shows up along with other folders I believe are Native to the phone's non-removable flash RAM. I concur with others that Ubuntu has no problem with older Android smartphones.

---

### Post by kelly4 on 2014-06-30
One last try to get some help with android concord zte gingerbread 2.3.7 to be detected by 14.04

Any help would be appreaciated

Thank you

):P

---

### Post by Vladlenin5000 on 2014-06-30
Have you tried another cable yet? Some cable are for charging only.

---

### Post by kelly4 on 2014-06-30
> **Vladlenin5000 said:**
> Have you tried another cable yet? Some cable are for charging only.

Same cable works on W7

:p

---

