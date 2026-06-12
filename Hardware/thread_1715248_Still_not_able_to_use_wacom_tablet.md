---
title: "Still not able to use wacom tablet"
date: 2011-03-26
forum: Hardware
---

### Post by ticktoast on 2011-03-26
It's been About 3 months since I got a new Bamboo Pen & Touch
and I have been completely unsuccessful in trying to get it to work

every time I try to reinstall the packages, I get the same error:

```
morgan@Morgan:~$ sudo add-apt-repository ppa:irie/wacom
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 09E51E202436DC9BE08378AA46830400C4A100CF
gpg: requesting key C4A100CF from hkp server keyserver.ubuntu.com
gpg: key C4A100CF: public key "Launchpad PPA for Irie's Elisp" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
morgan@Morgan:~$ sudo apt-get install wacom-dkms xserver-xorg-input-wacom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  uno-libs3 ure xfonts-mathml
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  wacom-dkms xserver-xorg-input-wacom
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/560kB of archives.
After this operation, 2,474kB of additional disk space will be used.
Selecting previously deselected package wacom-dkms.
(Reading database ... 361442 files and directories currently installed.)
Unpacking wacom-dkms (from .../wacom-dkms_0.8.10.2-1ubuntu2_all.deb) ...
Selecting previously deselected package xserver-xorg-input-wacom.
Unpacking xserver-xorg-input-wacom (from .../xserver-xorg-input-wacom_1%3a0.10.11-0ubuntu8_i386.deb) ...
Processing triggers for man-db ...
Setting up wacom-dkms (0.8.10.2-1ubuntu2) ...
Loading new wacom-0.8.10.2 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.37-020637-generic
Building for architecture i686
Building initial module for 2.6.37-020637-generic

Error! Bad return status for module build on kernel: 2.6.37-020637-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/wacom/0.8.10.2/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/wacom-dkms.0.crash'
dpkg: error processing wacom-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up xserver-xorg-input-wacom (1:0.10.11-0ubuntu8) ...
Errors were encountered while processing:
 wacom-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```also, the error continues to show even when I download completely unrelated things. It will come up with a window saying: 
E: wacom-dkms: subprocess installed post-installation script returned error exit status 10

So, that's basically it. Any help at all would be great, as I spent quite a bit of money on the tablet... and it's basically been a waste since I cannot use it... yikes...

---

### Post by Favux on 2011-03-26
Hi ticktoast,

IRIE's PPA is for Maverick, which is the 2.6.35 kernel.  You have a 2.6.37 kernel which is why the dkms won't build.

I sort of thought the 2.6.37 kernel would support your BambooPT out of the box.  It sounds like you have one of the 5 new models.  Let's figure out which one by entering in a terminal:
```
lsusb
```
and finding the product ID.

I think the most recent input-wacom's support kernel 2.6.37 if your model is not supported by the native 2.6.37 wacom.ko kernel module.  Although it may actually support support your tablet and your problem is with the Wacom X driver xf86-input-wacom not being recent enough.  Check in Synaptic Package Manager for the version number, it's the xserver-xorg-input-wacom package.

---

### Post by ticktoast on 2011-03-26
Thanks so much for getting back to me!
Well, that seems to make sense. But I think that's the second PPA I've tried using... But I'm not sure.. I'm afraid I have a terrible memory ahaha

The driver version from Synaptic is 1:0.10.11-0ubuntu8
And the product ID is 056a:00d6

---

### Post by Favux on 2011-03-26
I'm a little surprised Ubuntu Studio Maverick is using the 2.6.37 kernel and xf86-input-wacom-0.10-11!

OK, xf86-input-wacom-0.10-11 supports all 5 new models, and you have one of them.  Thinking about it I guess it's possible 2.6.37 doesn't have the 0xd6 or 0xd7 in it.  The first patch I submitted to linux-input had the other 3 models but I didn't submit those two originally because I didn't have a tested-by for them.  By the way IRIE is the tested-by on the 0xd8.  We worked on it together.

So the problem may be the wacom.ko (the usb kernel driver/module) with 2.6.37 doesn't have your model.  If so we can try getting the wacom.ko from input-wacom-0.10.11 which does have your model.  I'm not 100% sure it compiles on 2.6.37 though.  What is your exact kernel, in other words what is the output of:
```
uname -r
```
in a terminal?

---

### Post by ticktoast on 2011-03-26
Uh.. The kernel is 2.6.37-020637-generic

---

### Post by Favux on 2011-03-26
Alright, so nothing tricky then, the generic kernel header should be good.  For some reason Ubuntu Studios can cause problems with compiling wacom.

So go to the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") and do the alternate Section 1 to get the input-wacom wacom.ko.  Hopefully it will compile on 2.6.37 and get your tablet working.

If you can uninstall the PPA's especially the wacom dkms stuff first.  That can interfere with a new wacom.ko.

Does IRIE's PPA use input-wacom?

---

### Post by ticktoast on 2011-03-26
Goodness! It responded for the first time ever~ 
Thank you so much!

However, it* is* showing some... issues, so to speak
Every so often (which is very often in my case) the cursor will slowly drift to the top left corner of the desktop, and won't respond

I think I recall reading somewhere that a lot of people were having this issue. Do you know what I could do to maybe fix it?

(And yes, I believe it does)

---

### Post by Favux on 2011-03-26
Great!  Good work.

That's what I thought.  So the problem is he just hasn't packaged the PPA for Natty yet.  Assuming the Natty kernel 2.6.38 would also work with 2.6.37.

> Every so often (which is very often in my case) the cursor will slowly drift to the top left corner of the desktop, and won't respond
The pointer arrow shooting to the left upper corner usually indicates that the X driver isn't working.  And usually it's all or nothing.  So it's weird it seems to be partially working for a while.

Let's look at the output of:
```
xinput list
```
and
```
xsetwacom list
```

---

### Post by ticktoast on 2011-03-26
Okay. 

xinput list gave me this...
```
morgan@Morgan:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Pen stylus           id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Finger touch         id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Pen eraser           id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Finger pad           id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; UVC Camera (046d:080f)                      id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```and with xsetwacom list, I got this back..
```
morgan@Morgan:~$ xsetwacom list
Wacom BambooPT 2FG 4x5 Pen stylus    id: 9    type: STYLUS    
Wacom BambooPT 2FG 4x5 Finger touch    id: 10    type: TOUCH     
Wacom BambooPT 2FG 4x5 Pen eraser    id: 13    type: ERASER    
Wacom BambooPT 2FG 4x5 Finger pad    id: 14    type: PAD 
```

---

### Post by Favux on 2011-03-26
That looks good.  And the xsetwacom output indicates the input tools/tablet is on the wacom X driver.

Does anything reproducible precede the loss of the pointer arrow tracking?

---

### Post by ticktoast on 2011-03-26
Ahhh.. It seems the problem only occurs when I use touch rather than the pen
If my wrist brushes the pad, it jumps. Or if I just use my fingers at all.

The pen seems to be working fine, though

---

### Post by Favux on 2011-03-26
OK, that may be a problem with the X driver or it could be that the MT (multi-touch) code in input-wacom doesn't quite work correctly with the 2.6.37 kernel.  As you know touch should be turned off automatically when the stylus is in proximity to the tablet.

You can use the toggle touch script on the [Bamboo Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") to turn touch off when using the pen.  Part V. and the script is attached to the bottom of the first post.

---

### Post by ticktoast on 2011-03-27
Hmmm... It seems to be working now~ Thank you!

One last question..
I'm trying to get the pressure sensitivity to work in some of my graphics programs, but I'm having a bit of trouble..
When I do what the manual says to do, I see very little difference. Is there a reason for this that you know of...?

---

### Post by Favux on 2011-03-27
Good!

It should work as long as you configure the extended input devices in Gimp or Inkscape or the equivalent.  See the screenshots near the bottom of the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

You can check what the pressure curve is currently set to by entering:
```
xsetwacom get "Wacom BambooPT 2FG 4x5 Pen stylus" PressureCurve
```
and the same for the eraser.

---

