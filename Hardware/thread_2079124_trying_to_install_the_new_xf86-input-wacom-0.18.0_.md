---
title: "trying to install the new xf86-input-wacom-0.18.0 returns an error"
date: 2012-11-01
forum: Hardware
---

### Post by BcRich on 2012-11-01
I'm trying to install the new xf86-input-wacom-0.18.0 driver from a tarball for my intuos 5 pen and touch wacom tablet but I get an error when I run make. I'm trying to install it on my Ubuntu 10.10 system.
when I run ./configure --prefix=/usr
I get no errors
the running make produces
```
make  all-recursive
make[1]: Entering directory `/home/lyndon/Downloads/xf86-input-wacom-0.18.0'
Making all in conf
make[2]: Entering directory `/home/lyndon/Downloads/xf86-input-wacom-0.18.0/conf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lyndon/Downloads/xf86-input-wacom-0.18.0/conf'
Making all in doc
make[2]: Entering directory `/home/lyndon/Downloads/xf86-input-wacom-0.18.0/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lyndon/Downloads/xf86-input-wacom-0.18.0/doc'
Making all in src
make[2]: Entering directory `/home/lyndon/Downloads/xf86-input-wacom-0.18.0/src'
  CC       xf86Wacom.lo
In file included from /usr/include/xorg/privates.h:151,
                 from /usr/include/xorg/cursor.h:54,
                 from /usr/include/xorg/scrnintstr.h:55,
                 from /usr/include/xorg/xf86str.h:39,
                 from /usr/include/xorg/xf86.h:44,
                 from ../src/xf86Wacom.h:33,
                 from ../src/xf86Wacom.c:46:
/usr/include/xorg/dix.h:520: warning: redundant redeclaration of 'ffs'
In file included from ../src/xf86Wacom.h:95,
                 from ../src/xf86Wacom.c:46:
../src/xf86WacomDefs.h:501: error: expected specifier-qualifier-list before 'ValuatorMask'
../src/xf86Wacom.c: In function 'wcmInitAxes':
../src/xf86Wacom.c:168: warning: declaration of 'index' shadows a global declaration
/usr/include/string.h:489: warning: shadowed declaration is here
../src/xf86Wacom.c:174: warning: passing argument 1 of 'XIGetKnownProperty' discards qualifiers from pointer target type
/usr/include/xorg/exevents.h:104: note: expected 'char *' but argument is of type 'const char *'
../src/xf86Wacom.c:187: warning: passing argument 1 of 'XIGetKnownProperty' discards qualifiers from pointer target type
/usr/include/xorg/exevents.h:104: note: expected 'char *' but argument is of type 'const char *'
../src/xf86Wacom.c:208: warning: passing argument 1 of 'XIGetKnownProperty' discards qualifiers from pointer target type
/usr/include/xorg/exevents.h:104: note: expected 'char *' but argument is of type 'const char *'
../src/xf86Wacom.c:225: warning: passing argument 1 of 'XIGetKnownProperty' discards qualifiers from pointer target type
/usr/include/xorg/exevents.h:104: note: expected 'char *' but argument is of type 'const char *'
../src/xf86Wacom.c:232: warning: passing argument 1 of 'XIGetKnownProperty' discards qualifiers from pointer target type
/usr/include/xorg/exevents.h:104: note: expected 'char *' but argument is of type 'const char *'
../src/xf86Wacom.c:254: warning: passing argument 1 of 'XIGetKnownProperty' discards qualifiers from pointer target type
/usr/include/xorg/exevents.h:104: note: expected 'char *' but argument is of type 'const char *'
../src/xf86Wacom.c:261: warning: passing argument 1 of 'XIGetKnownProperty' discards qualifiers from pointer target type
/usr/include/xorg/exevents.h:104: note: expected 'char *' but argument is of type 'const char *'
../src/xf86Wacom.c:283: warning: passing argument 1 of 'XIGetKnownProperty' discards qualifiers from pointer target type
/usr/include/xorg/exevents.h:104: note: expected 'char *' but argument is of type 'const char *'
../src/xf86Wacom.c:290: warning: passing argument 1 of 'XIGetKnownProperty' discards qualifiers from pointer target type
/usr/include/xorg/exevents.h:104: note: expected 'char *' but argument is of type 'const char *'
make[2]: *** [xf86Wacom.lo] Error 1
make[2]: Leaving directory `/home/lyndon/Downloads/xf86-input-wacom-0.18.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lyndon/Downloads/xf86-input-wacom-0.18.0'
make: *** [all] Error 2

```

---

### Post by Favux on 2012-11-01
Hi BcRich,

Is 0.18.0 the first time you see that?  Or is it the first time you've tried to upgrade the default Maverick xf86-input-wacom?

Let's confirm the Maverick environment.  Run in a terminal:
```
Xorg -version
```
and post the output.

---

### Post by BcRich on 2012-11-01
Hi Favux
Thanks again for your help!
Sorry I forgot to mention my Xorg version is greater than 1.7.
I get 
```
X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.35-32-generic #67-Ubuntu SMP Mon Mar 5 19:39:49 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-32-generic root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro quiet splash
Build Date: 20 October 2011  03:12:38PM
xorg-server 2:1.9.0-0ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```
> Is 0.18.0 the first time you see that? Or is it the first time you've tried to upgrade the default Maverick xf86-input-wacom? I have tried to upgrade previously with version xf86-input-wacom-0.17.99.1 (which I think might have been a release candidate for 0.18.0). But I got the same error i.e. I managed to get past ./configure (without any errors) but when I got to the make command I got the same error (something to do with a datatype that mismatched).
The reason I was trying to upgrade xf86-input-wacom was because touch and pen pressure is not working in ubuntu 10.10 for me :?

---

### Post by Favux on 2012-11-01
Hi again.  :)

> I have tried to upgrade previously with version xf86-input-wacom-0.17.99.1 (which I think might have been a release candidate for 0.18.0). But I got the same error
Yep.

> The reason I was trying to upgrade xf86-input-wacom was because touch and pen pressure is not working in ubuntu 10.10 for me.
Did you install input-wacom-0.14.0 or 0.14.0+ (i.e. clone input-wacom)?

---

### Post by BcRich on 2012-11-01
```
Did you install input-wacom-0.14.0 or 0.14.0+ (i.e. clone input-wacom)?
```
That's a good question, I just wish I could give you a more helpful answer than I'm not entirely sure.
I think I kinda had a panic attack when my tablet wasn't working in 10.10 and installed everything that would let me install it relating to wacom (including doctormo's PPA).
So it is possible that I did install (or at least try to install)input-wacom-0.14.0, is there someway of knowing for certain?
I've attached a jpg of what my current driver looks like in synaptic.
I'd be totally lost without your help, thank you times a million!

---

### Post by Favux on 2012-11-01
Alright.  [Martin Owen's PPA]("https://launchpad.net/~doctormo/+archive/wacom-plus/+packages") isn't really going to gain you anything as it is pretty dated.  I can't tell if it is just installing xf86-input-wacom (xserver-xorg-input-wacom) or also a wacom.ko (which is what input wacom would get you).  The 8 in the name seems to indicate that the PPA is at least installing the PPA's xf86-input-wacom.  So you want to remove that PPA first probably through Synaptic Package Manager and get back to the default xserver-xorg-input-wacom.  We definitely want any wacom.ko dkms the PPA might have installed removed because that will interfere with installing one from input-wacom.

Then to clone the input-wacom git repository follow appendix 1 on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by BcRich on 2012-11-01
Thanks for the reply, Favux :)
I removed the PPA
then uninstalled xserver-xorg-input-wacom
reloaded the packeges list and reinstalled xserver-xorg-input-wacom (i.e. post removal of doctormo's PPA). The version I currently have installed is the official Ubuntu version (as it has an Ubuntu icon next to it when viewed in synaptic) so the current list of files this has installed follows,
```
/.
/lib
/lib/udev
/lib/udev/rules.d
/lib/udev/rules.d/69-xserver-xorg-input-wacom.rules
/usr
/usr/bin
/usr/bin/isdv4-serial-debugger
/usr/bin/xsetwacom
/usr/include
/usr/include/xorg
/usr/include/xorg/Xwacom.h
/usr/include/xorg/isdv4.h
/usr/include/xorg/wacom-properties.h
/usr/lib
/usr/lib/pkgconfig
/usr/lib/pkgconfig/xorg-wacom.pc
/usr/lib/xorg
/usr/lib/xorg/modules
/usr/lib/xorg/modules/input
/usr/lib/xorg/modules/input/wacom_drv.so
/usr/share
/usr/share/X11
/usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/doc
/usr/share/doc/xserver-xorg-input-wacom
/usr/share/doc/xserver-xorg-input-wacom/changelog.Debian.gz
/usr/share/doc/xserver-xorg-input-wacom/copyright
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/xsetwacom.1.gz
/usr/share/man/man4
/usr/share/man/man4/wacom.4.gz

```

---

### Post by Favux on 2012-11-01
OK, lets assume a dkms wasn't installed.  So now clone input-wacom to get a wacom.ko (kernel driver) that supports your Intuos5.

---

### Post by BcRich on 2012-11-01
> **Favux said:**
> OK, lets assume a dkms wasn't installed.  So now clone input-wacom to get a wacom.ko (kernel driver) that supports your Intuos5.
lol your patience with me is unmatched, if this was a test you'd be a zen master! Thanks :)
I tried cloning input-wacom after installing input-wacom-0.13.0 and rebooting as per instructions (that part went fine) but once again when I get to make I got an error. So everything worked up to and including 
```
./autogen.sh --prefix=/usr
```
but when I tried make I got the following error 
```
make  all-recursive
make[1]: Entering directory `/home/lyndon/Desktop/xf86-input-wacom'
Making all in conf
make[2]: Entering directory `/home/lyndon/Desktop/xf86-input-wacom/conf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lyndon/Desktop/xf86-input-wacom/conf'
Making all in doc
make[2]: Entering directory `/home/lyndon/Desktop/xf86-input-wacom/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/lyndon/Desktop/xf86-input-wacom/doc'
Making all in src
make[2]: Entering directory `/home/lyndon/Desktop/xf86-input-wacom/src'
  CC     xf86Wacom.lo
In file included from ../src/xf86Wacom.h:95,
                 from ../src/xf86Wacom.c:46:
../src/xf86WacomDefs.h:501: error: expected specifier-qualifier-list before ‘ValuatorMask’
make[2]: *** [xf86Wacom.lo] Error 1
make[2]: Leaving directory `/home/lyndon/Desktop/xf86-input-wacom/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lyndon/Desktop/xf86-input-wacom'
make: *** [all] Error 2

```

---

### Post by Favux on 2012-11-01
That's the Wacom X driver xf86-input-wacom.  So that's basically the same as trying to compile the xf86-input-wacom-0.18.0 tar.  The kernel driver is in the input-wacom package.  Are you following the appendix 1 instructions to clone input-wacom?

---

### Post by BcRich on 2012-11-01
Oops, sorry my bad. I missed that part. ok so I'm back on track now, I cloned input-wacom and that didn't have any errors, rebooted. but the touch is still not working, was I supposed to clone it with this patch? 
```
patch -p1 < ~/Desktop/input-wacom-Backport-2nd-and-3rd-gen-Bamboo-support-to-2.6.30.patch
```

---

### Post by Favux on 2012-11-01
No you're good.  That patch is no longer needed and the instructions for that are outdated.  Sorry I should have mentioned that.  Because of the 7 day edit limit on posts since late June tutorial authors can't update their HOW TOs.

OK now that you have a working wacom.ko installed you need a X driver that supports the Intuos5.  Let's try compiling xf86-input-wacom-0.17.0 and see if that avoids the error messages.  So just follow the instructions for compiling the xf86-input-wacom tar in part II but change the number (0.15.0) to 0.17.0 everytime the number appears.

---

### Post by BcRich on 2012-11-01
when I try to patch input-wacom I get the following errors
```
patching file 2.6.30/wacom_sys.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #2 succeeded at 161 (offset 18 lines).
Hunk #3 succeeded at 316 (offset 14 lines).
patching file 2.6.30/wacom_wac.c
Hunk #1 FAILED at 197.
Hunk #2 FAILED at 337.
Hunk #3 FAILED at 1130.
Hunk #4 FAILED at 1318.
Hunk #5 FAILED at 1507.
5 out of 5 hunks FAILED -- saving rejects to file 2.6.30/wacom_wac.c.rej
patching file 2.6.30/wacom_wac.h
Hunk #1 FAILED at 22.
1 out of 1 hunk FAILED -- saving rejects to file 2.6.30/wacom_wac.h.rej

```
is that normal?

Edit: Ok missed your last post. but it should be fine cause I didn't get as far as trying to install the patched version. In other words I've still got the unpatched input-wacom installed.

---

### Post by Favux on 2012-11-01
I'm sorry.  Why are you trying to patch input-wacom?  And with what patch?  You said you've already compiled and installed the wacom.ko from input-wacom.  So we should be done with input-wacom.

---

### Post by BcRich on 2012-11-01
> **Favux said:**
> I'm sorry.  Why are you trying to patch input-wacom?  And with what patch?  You said you've already compiled and installed the wacom.ko from input-wacom.  So we should be done with input-wacom.
Yes, sorry you're right. There was no need to try that. I posted that before I read your reply to my previous post, but I didn't overwrite anything of the original input-wacom installation. so everything should be fine.
I managed to install xf86-input-wacom 0.17.0 without any errors, which is great news Thanks, Favux! But touch is still not working, synaptics (the default ubuntu version )is installed on my system will this effect it?

---

### Post by Favux on 2012-11-01
Shoot.  Should be working now.

Please post the outputs of **xinput list** and **xsetwacom list**.

And we might want to notify the Linux Wacom Project that xf86-input-wacom isn't building in Maverick.

---

### Post by BcRich on 2012-11-01
```
xinput list
```
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen stylus        	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Finger stylus     	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.0A	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen eraser        	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen cursor        	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Pen pad           	id=17	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Finger eraser     	id=18	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Finger cursor     	id=19	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch M Finger pad        	id=20	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; PWC snapshot button                     	id=8	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]

```
and xsetwacom list
```
Wacom Intuos5 touch M Pen stylus	id: 9	type: STYLUS    
Wacom Intuos5 touch M Finger stylus	id: 10	type: STYLUS    
Wacom Intuos5 touch M Pen eraser	id: 15	type: ERASER    
Wacom Intuos5 touch M Pen cursor	id: 16	type: CURSOR    
Wacom Intuos5 touch M Pen pad   	id: 17	type: PAD       
Wacom Intuos5 touch M Finger eraser	id: 18	type: ERASER    
Wacom Intuos5 touch M Finger cursor	id: 19	type: CURSOR    
Wacom Intuos5 touch M Finger pad	id: 20	type: PAD   
```
So I guess I'll have to wait for an update.
Any idea who I should report it to?

---

### Post by Favux on 2012-11-01
Does the pen give you pressure now?

The output shows the tablet is being recognized.  I haven't seen it for the Intuos5 before, I think.  And having stylus, eraser, cursor, and pad appended to Finger is weird.  I think it should just be appending touch to Finger.  Anyway not seeing touch explains why there is no touch I suppose.

Try rebooting a couple of times and see if it is still the same.  Still no touch?

---

### Post by BcRich on 2012-11-01
Thanks Favux, I've give it a try :)
For now, the pen pressure does not work and the eraser works like a pen (in other words instead of erasing it draws). However the two barrel buttons work middle mouse and right click.

---

### Post by Favux on 2012-11-01
Is it Gimp or Inkscape you are not seeing pressure?  Some programs like Gimp require you to configure the extended input device preferences. Do you know how to do that?  Whereas a program like MyPaint should have pressure off the bat.

Also if touch doesn't kick in try running these commands:
```
xsetwacom set "Wacom Intuos5 touch M Finger touch" Touch on

xsetwacom set "Wacom Intuos5 touch M Finger touch" Gesture on
```
Or maybe use stylus instead of touch?  Or maybe just "Wacom Intuos5 touch M Finger"?

---

### Post by BcRich on 2012-11-01
hi Favux 
All of the different combinations for activating touch basically returned a cannot find device error eg
```
Cannot find device 'Wacom Intuos5 touch M Finger touch'.

```
I'm using myPaint to test pressure sensitivity, yea I know about that issue with the Gimp needing to be setup for tablet usage thanks for mentioning it anyway. You're help has been most sincerely appreciated :)

---

### Post by BcRich on 2012-11-01
this command just worked without an error. but touch is still not working.
```
xsetwacom set "Wacom Intuos5 touch M Finger stylus" Touch on
```

---

### Post by Favux on 2012-11-01
Alright, so touch isn't working.  I think it is suppose to with input-wacom for the Intuos5, even though the mult-touch headers aren't available for the 2.6.35 kernel.  Input-wacom should be taking care of that is my understanding.

Where you report is to the linuxwacom-discuss mailing list:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

You'd want to include the output of **Xorg -version** along with the information that you cloned input-wacom.  Tell them xf86-input-wacom-0.17.0 compiles but not xf86-input-wacom-0.18.0.  And give the make output for that where you get the errors.  And show them the ouput of **xinput list** and **xsetwacom list** for 0.17.0.

Also you should retry xf86-input-wacom-0.18.0 and confirm you get those same errors in the make output.

---

### Post by BcRich on 2012-11-02
Thanks Favux, I'll do all of that. You've been super helpful as always I can't thank you enough! Once I've retested with 0.18.0 I'll post my results here, and follow up with contacting Linux-wacom if it still doesn't work.

---

