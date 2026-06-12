---
title: "Installing Wacom5 on Oneiric"
date: 2012-03-27
forum: Hardware
---

### Post by hozho on 2012-03-27
Howdy,

I have looked through these forums and do not find out how to get Ubuntu to recognize there is a new Wacom5 plugged in, even after rebooting.

I have tried many sites and spent a few days on it. Most bring me back to [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page) where I am told to use the drivers in the distribution, but cannot find them. The Wacom gui in System does not recognize there is a tablet plugged in.

Also, if I get Ubuntu to find the tablet, I would not know how many buttons I have or what things should be set to. I have never used a Wacom tablet!

/etc/lsb-release contains...

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

xinput --list gives me...

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G500                               id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G500                               id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

In page 131 of a thread here called "**HOW TO:  Install a LinuxWacom Kernel Driver for Tablet PC's",** someone had a conflict and ran "locate wacom.ko" which gives me...

/lib/modules/2.6.35-28-generic-pae/kernel/drivers/hid/hid-wacom.ko
/lib/modules/2.6.35-28-generic-pae/kernel/drivers/input/tablet/wacom.ko
/lib/modules/2.6.38-12-generic-pae/kernel/drivers/hid/hid-wacom.ko
/lib/modules/2.6.38-12-generic-pae/kernel/drivers/input/tablet/wacom.ko
/lib/modules/3.0.0-12-generic-pae/kernel/drivers/hid/hid-wacom.ko
/lib/modules/3.0.0-12-generic-pae/kernel/drivers/input/tablet/wacom.ko
/lib/modules/3.0.0-14-generic-pae/kernel/drivers/hid/hid-wacom.ko
/lib/modules/3.0.0-14-generic-pae/kernel/drivers/input/tablet/wacom.ko
/lib/modules/3.0.0-16-generic-pae/kernel/drivers/hid/hid-wacom.ko
/lib/modules/3.0.0-16-generic-pae/kernel/drivers/input/tablet/wacom.ko

Does anyone know why Ubuntu does not see the tablet after multiple reboots?

Thanks,
   -- Hoz

---

### Post by Favux on 2012-03-27
Hi Hoz,

Welcome to Ubuntu forums!

The Intuos5's haven't been added to the kernel driver wacom.ko or the X driver xf86-input-wacom yet.  That's the reason you don't see it, it isn't in the kernel.

Jason has submitted patches for it and so they will likely be supported in the 3.4 kernel.  In the meantime you can apply the patches yourself to get kernel support.  I would probably check first if the patches apply to input-wacom, if not then patch the kernel.  Instructions for cloning input-wacom are in appendix 1 of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  An example of applying a patch is in appendix 2.  Instructions for patching the Ubuntu kernel are in appendix 1 of the [linux wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  And the kernel patches are on [linuxwacom-devel]("http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_b4f3Ls_wRfMJUDz8tt8m-PSefUYV2Zg0w1ansL7VMOwQ%40mail.gmail.com&forum_name=linuxwacom-devel").  If you have touch on your Intuos5 be sure to use the v2 of patch 4/4.

For xf86-input-wacom the patch is also on [linuxwacom-devel]("http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_bGNAUfF4jbnQ__QybOsx_4EUB_igpSO6AZL1_8zW21TA%40mail.gmail.com&forum_name=linuxwacom-devel").  Instructions for compiling it are on part II. of the BambooPT HOW TO.

The LWP site you link to is the mediawiki.  Although if you link through Get the Drivers you can get to the files the main site with the files tab is here:  [http://sourceforge.net/projects/linuxwacom/?source=directory](http://sourceforge.net/projects/linuxwacom/?source=directory)

---

### Post by hozho on 2012-03-27
Thank you, Favux.

I certainly gave it my best. I have never really successfully compiled anything from instructions like these, and this was no exception!

"./configure --prefix=/usr"  gives me an error that "No package 'libudev' found", and so "make" tells me "make: *** No targets specified and no makefule found. Stop."

No instructions on getting files, configuring, and making them have ever worked for me :-(.

I tried harder than any of the other things I have unsuccessfully tried to make/compile.  I did try "sudo apt-get install libudev" but it could not find it. Then I checked the Ubuntu Software Center and that says it is installed, so I don't know what I'm doing wrong :-(.

So I am at a loss. Thank you so much for all the information though! 

   -- Hoz

---

### Post by Favux on 2012-03-27
Hi Hoz,

Sounds like you have "issues" with compiling.  That's understandable as it can be very frustrating if the problem isn't obvious.

So you didn't have any problem making patches from the links I gave you and they applied succesfully?

I'm assuming you started first on the kernel?  Not sure about libudev but often when it says it is missing a library it means the development version.  So "libudev"  may be "libudev-dev".

We could sort of go in reverse order and do xf86-input-wacom first since that only has the one patch, most likely uses the current dependencies, and so should be easier to do.


Attached is the patch I get.  Do you have the same?

---

### Post by hozho on 2012-03-28
Thanks, Favux!

No, what I got from both places was xf86-input-wacom-0.14.0.tar.bz2 . I tried to follow the instructions to compile it.

Is the patch what you mean by 'coming in backwards'? I'm afraid I don't see instructions for what to do with a '.patch' file :-(.

I will look some more!

Thanks,
   -- Hoz

---

### Post by Favux on 2012-03-28
There's two drivers you need to patch.  The kernel driver (wacom.ko) and the X driver xf86-input-wacom.

The command in appendix 2 shows you how to apply a patch.  Assuming you've changed directory into the downloaded xf86-input-wacom folder it looks something like:
```
patch -p1 < path-to-patch/name-of-patch.patch
```
So in this case:
```
patch -p1 < path-to-patch/xf86-input-wacom-Add-support-for-the-Intuos5.patch
```
You can look at the source code in the two files the patch changes:
```
 src/wcmUSB.c            |    7 +++++++
 src/wcmValidateDevice.c |    5 +++++
 2 files changed, 12 insertions(+), 0 deletions(-)
```
And see the difference before and after you apply the patch.

---

### Post by hozho on 2012-03-29
Thank you, Favux!

I was in roman numeral II on the page and not Appendix 2! Anyway, having found that now I still do not see the file you gave me.

I ran the patch you attached to your last message using your directions in that message and it said...

patching file src/wcmUSB.c
patching file src/wcmValidateDevice.c

I did not know how to check changes for the 7+++ and 5+++ stuff, but it looks like they were patched :-).

Sorry to be so lost. I certainly appreciate this!

Thanks,
   -- Hoz

---

### Post by Favux on 2012-03-29
You could just look at the files in gedit, but you don't need to, I was just sayin'.   Looks like the patch applied succesfully.  When it doesn't it'll tell you.  It will say things like hunk #1 (or whatever) failed and it will save rejects in a .rej file.

I assume you then went on to compile and install the patched xf86-input-wacom and that all went OK.

If so the next step is to get a working kernel driver for the Intuos5.  I'll pull out the four kernel patches and see if they apply to input-wacom.  That would be nice if they do and make things easier.

---

### Post by Favux on 2012-03-29
Well crud, that could have gone better.

The patches do not apply to input-wacom's 2.6.38 folder where the wacom.ko for Oneiric's 3.0 kernel gets compiled.  Alright so too much change between 2.6.38 and patches for the 3.4 kernel.  So then I tried to apply them to Oneiric's 3.0 kernel directly.  That went better with most of the first (stylus) patch being applied but a couple hunks failed.  Same for the second (ExpressKey) and fourth (touch) patch.  I didn't check if I could manually fix the failed hunks but that might be possible.  Then make new patches from that, but since I don't have an Intuos5 to test with...

So that leaves Precise.  I think Beta 2 is out today and the patches are most likely to apply to its 3.2 kernel.  Maybe even patch 3 because I think the sysfs for the LEDs might be in 3.2.

Actually using the Ubuntu kernel source code isn't really any harder than using input-wacom.  The kernel just takes longer to download.  You don't compile the kernel, just the wacom.ko from it as with input-wacom.  Appendix 1 on the [Linux Wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") has the instructions.

If someone is brave enough to venture into Precise:
The appendix 1 instructions assume you are working on your Desktop so download the patches onto it and remove them from their uncompressed folder or change the paths below.  Once it is downloaded change directory into the kernel source code folder 3.2.0 at the point the instructions tell you to patch.
```
patch -p1 < ~/Desktop/input-wacom-Intuos5-basic-support.patch
patch -p1 < ~/Desktop/input-wacom-Intuos5-Touch-Ring-ExpressKey-support.patch
patch -p1 < ~/Desktop/input-wacom-Intous5-Touch-Ring-LED-support.patch
patch -p1 < ~/Desktop/input-wacom-Intuos5-multitouch-sensor-support.patch

```
Then just proceed with the instructions.


Eventually at some point Jason will probably backport Intuos5 support to input-wacom.

---

### Post by Stolea on 2012-04-21
Silly question:
does this method apply to Lucid 10.04 with all the up-to-date patches too?

---

### Post by Favux on 2012-04-21
Hi Stolea,

No, but you are in luck.  Jason backported the Intuos5 support to input-wacom about a week ago.  So you should now be able to get a wacom.ko that supports the Intuos5 by cloning the input-wacom git repository.  See appendix 1 on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

The patch for xf86-input-wacom has been commited to the xf86-input-wacom repository so you would want to clone it too.  Part II. on the HOW TO.

Good luck.  Let me know if you get it working.

---

### Post by leptogenesis on 2012-04-21
Hey Favux,

I have an Intuos5 and followed the instructions in the above post, and...now it seems the wacom kernel module is no longer loading.  i.e. "lsmod | grep wacom" returns nothing.  I've installed the newest xf86-input-wacom from git and input-wacom, and I can see that /lib/modules/3.0.0-17-generic/kernel/drivers/input/tablet/wacom.ko matches what I compiled from the git repo.  I've run depmod -a and rebooted.  unfortunately I'm not so familiar with installing kernel modules...any idea what I"m doing wrong?

---

### Post by Favux on 2012-04-21
Hi leptogenesis,

Usually
> I've run depmod -a and rebooted.
gets the newly compiled and copied into place wacom.ko to auto-load.  But on some systems for whatever reason it doesn't.  You can "force" wacom.ko to auto-load by adding ***wacom*** to the list in /etc/modules.
```
gksudo gedit /etc/modules
```
Just add it, Save, and reboot.  Should now show up in *lsmod*.

---

### Post by Stolea on 2012-04-26
Thanks for the help. It worked a treat.

---

### Post by Favux on 2012-04-26
Great!  :)

Yours may be the first Intuos5 set up in Lucid I've seen reported!

---

### Post by Stolea on 2012-04-26
I use a VMware installation under Lucid to run Win7. I have to use Photoshop which is what the Intuos5 gets used with.
In native Lucid I can get Intuos to function like a mouse, but why would I. I have tried it in Gimp and the pop-up screen that shows the buttons and controls does not show on the screen, in fact none of the buttons seems to work.
But in the Vmware\Win7 setup everything works fine.

---

### Post by Favux on 2012-04-26
No one has written pop up software to control the buttons for an Intuos5 yet that I am aware of.  I do have a touch toggle script with notification that will kind of give you that for at least the touch on/off button.

You can configure the buttons with an xsetwacom script.  That's described here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)  Which is one of the HOWTO's on the Linux Wacom Project's mediawiki HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)  And there are some sample xsetwacom scripts attached to post #2 here:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

In Precise the GNOME Wacom Graphics Tablet applet in System Settings may allow you to configure the buttons.  I don't know.  I do know the Intuos5 is in libwacom so there's a chance.  It doesn't yet work for my BambooPT though.

The stylus and eraser work in Gimp when you configure the extended input devices, correct?

---

### Post by prokoudine on 2012-04-27
> **Favux said:**
> Hi Hoz,

Welcome to Ubuntu forums!

The Intuos5's haven't been added to the kernel driver wacom.ko or the X driver xf86-input-wacom yet. 

It now has. Check the most recent update of the linuxwacom project from 2 days ago.

---

### Post by Favux on 2012-04-27
Hi prokoudine,

Correct, Jason has now added Intuos5 support to the input-wacom git repository and it is in his release of the input-wacom-0.13.0 tar on 4-24-12.  And it will be in xf86-input-wacom-0.15.0 which is about to be released as the 0.14.99 tar with it is out.

---

### Post by Stolea on 2012-05-01
Haven't had the chance to play around with the xf86 module, but I just discovered that the wireless option doesn't work with Linux either (at least not with my set-up). My normal bluetooth dongle that normally finds any blootooth device can't find the tablet and the dongle that comes with the kit can't see it or any other blootooth device. Works fine in native Windoze7.
I guess its not a biggie but bloody annoying nonetheless. 
Will have a look at the xf86 module when I find a moment to play around with it.

---

### Post by Favux on 2012-05-01
Przemo Firszt just recently finished submitting the Bluetooth support for the Intuos4 to the kernel.

But I wonder if the Intuos5 is using the same wireless kit that the third generation BambooPT's are using.  Chris Bagwell posted a test version on his github site about 4 months ago.  But it was in the input-wacom 2.6.38 folder, if I recall correctly, which won't help you in Lucid.  The details are at the top of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") in the Call for Testers.

At least one BambooPT user reported that it was working for his wireless.  I don't know where Chris is at with it.

---

### Post by leptogenesis on 2012-05-14
Hmm....adding the line to /etc/modules made the module load, but the intuos5 still isn't recognized.  I had tried a few other things to install this, and I'm wondering if perhaps there's conflicting versions of wacom.ko.  

```

me@laptop:~$ sudo find / -name "wacom.ko"
/var/lib/dkms/wacom/0.12.1/3.0.0-19-generic/x86_64/module/wacom.ko
/var/lib/dkms/wacom/0.12.1/3.0.0-17-generic/x86_64/module/wacom.ko
/var/lib/dkms/wacom/0.12.1/build/wacom.ko
/lib/modules/3.0.0-12-generic/kernel/drivers/input/tablet/wacom.ko
/lib/modules/3.0.0-19-generic/updates/dkms/wacom.ko
/lib/modules/3.0.0-19-generic/kernel/drivers/input/tablet/wacom.ko
/lib/modules/3.0.0-16-generic/kernel/drivers/input/tablet/wacom.ko
/lib/modules/3.0.0-17-generic/updates/dkms/wacom.ko
/lib/modules/3.0.0-17-generic/kernel/drivers/input/tablet/wacom.ko
/lib/modules/3.0.0-15-generic/kernel/drivers/input/tablet/wacom.ko
/lib/modules/3.0.0-14-generic/kernel/drivers/input/tablet/wacom.ko

```

uname -r returns 3.0.0-19-generic so I'm guessing only the things that contain 3.0.0.19 matter.  The files in /var/lib/dkms/wacom/0.12.1/3.0.0-19-generic/x86_64/module/wacom.ko and /lib/modules/3.0.0-19-generic/updates/dkms/wacom.ko are the same file, but /lib/modules/3.0.0-19-generic/kernel/drivers/input/tablet/wacom.ko is different from both of them; /lib/modules/3.0.0-19-generic/kernel/drivers/input/tablet/wacom.ko is in fact the same as the wacom.ko that I'm supposed to be installing.  Any idea what I should do?

---

### Post by Favux on 2012-05-14
Yes, you want to remove the PPA that installed the dkms (dynamic kernel module support) wacom.ko.  The dkms impelementation of that wacom.ko is likely blocking the one you are trying to use.  Hopefully when the PPA is removed it will take its dkms stuff with it.  Look in /usr/src for the original dkms folder, it should be removed too when the PPA is.

---

### Post by leptogenesis on 2012-05-14
That did it--intuos5 works now!  Thanks so much!

---

