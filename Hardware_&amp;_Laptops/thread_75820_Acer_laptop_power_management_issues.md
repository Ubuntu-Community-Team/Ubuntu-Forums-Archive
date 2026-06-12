---
title: "Acer laptop power management issues"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by beercz on 2005-10-14
Acer laptops and power management -  14 Minutes Ago
Hello everyone

This is a follow up to a couple of threads and a bug report regarding power management and acer laptops.

First of all I initiated a thread in the development forum for Breezy regarding this issue. See [http://ubuntuforums.org/showthread.php?t=68630](http://ubuntuforums.org/showthread.php?t=68630).

Another thread also discusses wifi issues which is relatated to the power management issue. See [http://ubuntuforums.org/showthread.php?t=60484](http://ubuntuforums.org/showthread.php?t=60484) (particulary pages 2, 5 and 6).

I also reported a bug - see [http://bugzilla.ubuntu.com/show_bug.cgi?id=16863](http://bugzilla.ubuntu.com/show_bug.cgi?id=16863)

This page also gave me some help (especially in terms of getting the iasl compiler): [https://wiki.ubuntu.com/ACPIBattery](https://wiki.ubuntu.com/ACPIBattery)

Right, so pulling all this information together, I have managed to do the following:

I am now running Breezy using kernel 2.6.12-9-386 **without** the "acpi=off" boot parameter, previously without this parameter the machine hung using this kernel (see above bug report). I have my wireless networking OK, but my synaptics mouse pad still does not work, neither does my battery monitor or my power management.

Incidentally I have the hot keys working OK (and have done for some time), see [http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)

My laptop is an Acer Travelmate 3201 XCi.

To get the kernel 2.6.12-9-386 without using the "acpi=off" boot parameter I did the following:

I made a new directory and installed the iasl compiler, see [https://wiki.ubuntu.com/ACPIBattery](https://wiki.ubuntu.com/ACPIBattery) and look in the section "Obtaining Intel's iasl compiler".

Then I took a backup of menu.lst (from /boot/grub/menu.lst)

I then obtained the kernel using synaptic (linux-image-2.6.12-9-386) using synaptic. When it was installed and configured I edited menu.lst (the original copy in /boot/grub - not the backup!!) and added the "acpi=off" boot parameter to the following line:

kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash

So it looks like:

kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro acpi=off quiet splash

After saving and the file (menu.lst) I rebooted to the new kernel (I was previously using kernel 2.6.10-5-386).

Then I ran a *root* terminal, switched to directory I previously created (for iasl), and ran the following commands:
[B]
cat /proc/acpi/sdst > dsdt.aml
./iasl -d dsdt.aml # creates a new file - dsdt.asl
./iasl -tc dsdt.dsl # creates a new file - DSDT.aml
cp DSDT.aml /etc/mkinitramfs
dpkg-reconfigure linux-image-$(uname -r)[/B]

uname -r gives the currently running kernel version, hence the need to install the new kernel and add "acpi=off" boot parameter.

Rebooted to test (sucessfully)

Finally edited /boot/grub/menu.lst to add my Windoze partition to the boot menu - it was removed by the dpkg-reconfigure command.

Hope this is helpful to others, and that it sparks more discussion and help.

I would love to get power management and my synaptics mouse pad working correctly.

I will update this forum as and when I make some progress.

Ian

---

### Post by JazzCrazed on 2005-10-18
Thanks for this, beercz... I did follow these steps almost exactly, per [this thread]("http://http://ubuntuforums.org/showthread.php?t=60484"). Although I didn't get 2.6.12-9 via synaptic... It apparently was installed automatically by Ubuntu's update function.

I still get the hangup on loading ACPI modules - despite multiple do-overs of creating DSDT.aml and reconfiguring the kernel. I might try it again, for old time's sake, just to make sure I did it right.

Though I'm almost ashamed to admit that I bit the bullet and ordered an [Intel 2915 mini pci adapter]("http://www.newegg.com/Product/Product.asp?Item=N82E16833106219&ATT=Network+Wireless+Ada&CMP=OTC-yah00TT"). My primary motivation was future-proofing, and the need for WPA (following the wpa-supplicant+ndiswrapper howtos in this forum so far have not worked for me).

Thanks again!

---

### Post by JazzCrazed on 2005-10-20
OK...Drudging this thread back up, because I'm frustrated with my Acer.

On my Acer Aspire 3002LCi, I'm currently booted into kernel 2.6.12-9-386 using "ACPI=off".

I've run through most of these steps before, but I'm starting anew because I'm sure I must have missed something.

Which means that to start I'm trying to install acerhk. I've downloaded version 0.5.28 from the linked website above, extracted, and tried to make it. Here's what happens:

```
make -C /usr/src/linux-headers-2.6.12-9-386/ SUBDIRS=/home/jazzcrazed/Desktop/DOWNLOADS/BIOS, DRIVERS, AND FIRMWARE/acerhk-0.5.28 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** No rule to make target `DRIVERS,'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [acerhk.ko] Error 2

```

This "no rule to make target" error thing has really been getting on my nerves lately.

I've made sure that I've installed linux-headers-2.6.12-9-386 - and in fact I have nearly ever linux-headers package available in synaptic installed. I've also edited the Makefile to point specifically to my kernel version's headers. No dice with that - still getting the same error.

Googling around, I ran into the suggestion to run "make clean" - which I did, to no avail... Running make shortly thereafter gleans the same error.

This does *not* seem to be an isolated error to acerhk... I'm also trying to compile some drivers I downloaded for my Intel wireless card, that generates the very same error.

Any help with this problem is much, *much* appreciated!!

---

### Post by skirkpatrick on 2005-10-20
[QUOTE=JazzCrazed]
```
make -C /usr/src/linux-headers-2.6.12-9-386/ SUBDIRS=/home/jazzcrazed/Desktop/DOWNLOADS/BIOS, DRIVERS, AND FIRMWARE/acerhk-0.5.28 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** No rule to make target `DRIVERS,'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [acerhk.ko] Error 2

```[/QUOTE]

Damn, I don't know why I didn't notice your problem before!  What you need to do is expand the acerhk tarball (**tar -zxvf acerhk-0.5.27.tgz**) and change to the acerhk-0.5.27 directory and follow the rest of the instructions in the INSTALL file.  That's all I did.  The -C option for make causes it to change to the indicated directory before it starts performing the make.  The other problem you have is caused by Windows convincing people that it's okay to use spaces in directory names.  In Linux, never use spaces, use underscores or something else.  As soon as make sees " DRIVERS," it assumes it's another target to build, not part of the directory name.

---

### Post by JazzCrazed on 2005-10-21
Wow. #-o #-o #-o 

Lesson learned. :D Not on my laptop atm, but I'll try it again shortly.

Thanks a million, skirkpatrick!

---

### Post by dailer on 2005-10-21
acerhk is in breezy!
```
sudo modprobe acerhk
```
or if you want to make it permanent
```
sudo echo acerhk >> /etc/modules
```

---

### Post by JazzCrazed on 2005-10-21
Well damn, I didn't know that, dailer. Oh well... I successfully compiled per skirkpatrick after renaming the folder it resided in without spaces.

The rest of the steps seemed to work - although, if acerhk was already in breezy, then I'm not the wiser. The buttons work, and I never tried them before. I never use special buttons, anyway... I only installed them in hopes that it helps out ACPI.

Since now you told me that they were already in Breezy, then maybe they won't make a difference after all.

I'll keep you posted... Thanks all!

---

### Post by JazzCrazed on 2005-10-21
FYI, I noticed that if I boot into 2.6.12-9-386 with "ACPI=off" in menu.lst, the folder **/proc/acpi** does not even exist! I'm not booted in to 2.6.12-8, which seems to load acpi just fine, and the folder *does* exist.

I guess I need to do the whole thing in 12-8-386, and just make sure to copy the file to the appropriate kernel folder before reconfiguring my kernel with it.

Be back after I try all that...

---

### Post by skirkpatrick on 2005-10-21
acerhk may be in Breezy but that doesn't mean that it installed by default.  Also, if you use acerhk from the repositories, you should automatically get a new version every time you upgrade your kernel (remember, you compiled it with kernel headers so it needs to match your kernel).

And I'm not sure if acerhk helps with ACPI, I needed it to turn the wifi radio on.

---

### Post by Tiede on 2006-02-01
[RESOLVED] I followed the instruction in the [ Battery Wiki ](https://wiki.ubuntu.com/ACPIBattery) and did not notice any change. My battery still says 0% charged no matter what I do.

Some (ir)relevant info:
I chose the DSDT for an Acer Aspire 3003 WLMi since there was none for my Acer Aspire 3003 WLCi, and it seems like someone used it ok.
I did not get any ResourceSource string is missing error and went on right ahead with compiling.
I put the DSDT.aml in both /etc/imknitrd/DSDT and /etc/mkinitramfs/DSDT.aml
because I forgot that in breezy, the location changed to mkinitramfs, but I don't think this maybe the problem.
Finally, I am using Dapper and not breezy.

Can any body help me figure out what to do next? Thanks in advance!

EDIT: I am sorry, it did work, the problem is that I thought the image ending with .acpi was the one in which the battery was fixed. I logged in using the original one, and it works. I think the wiki should be edited to put this precision before someone else gets confused over it :)

---

