---
title: "Bluetooth doesn't pick up devices"
date: 2011-10-22
forum: Hardware
---

### Post by campbelt on 2011-10-22
I have 64 bit 11.10 on an Asus UX31 (Zenbook).  As I can't use the built in touchpad I decided to get a Bluetooth mouse to use instead of a wired one (only 2 usb ports).

The problem is that when I scan for the mouse (MS Bluetooth Notebook Mouse 5000) nothing is recognized.  I have used both the Bluetooth manager and command line "hcitool scan".  The Bluetooth adapter is built-in and shows up in the app "Blue-who" as hci0(Zen-0) address 74:2F:CC:1E:C2 but no mouse.  It also failed to pick up a keyboard and a cellphone.

When I boot into Windows the mouse is detected and works.

I've tried to find an online answer without success.  Any help would be appreciated.

---

### Post by dFlyer on 2011-10-22
I wounder if it's like the winmodem it only works with windows. I haven't used windows in so long I just can't answer your question. I remember when only winmodems only worked in windows. If it's an ms bluetooth maybe it only works in windows. Have you tried additional drivers to see if it can find a driver?

---

### Post by campbelt on 2011-10-23
The mouse works on both Windows and OS-X.

No additional drivers show up as available to install.

---

### Post by campbelt on 2011-10-23
Bump

---

### Post by RR123RR on 2011-10-24
It seems to think it sees the device but, maybe since it's a BT4.0, it doesn't do anything...

dmesg
```
[    2.578197] Bluetooth: Core ver 2.16
[    2.578220] Bluetooth: HCI device and connection manager initialized
[    2.578222] Bluetooth: HCI socket layer initialized
[    2.578224] Bluetooth: L2CAP socket layer initialized
[    2.578266] Bluetooth: SCO socket layer initialized
[    2.581117] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    2.760484] Bluetooth: RFCOMM TTY layer initialized
[    2.760490] Bluetooth: RFCOMM socket layer initialized
[    2.760492] Bluetooth: RFCOMM ver 1.11
[    2.762814] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.762817] Bluetooth: BNEP filters: protocol multicast
```


lsusb -v
```

Bus 001 Device 005: ID 13d3:3375 IMC Networks 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x13d3 IMC Networks
  idProduct          0x3375 
  bcdDevice            0.01
  iManufacturer           1 Atheros Communications
  iProduct                2 Bluetooth USB Host Controller
  iSerial                 3 Alaska Day 2006
  bNumConfigurations      1

```

---

### Post by campbelt on 2011-10-24
My lsusb -v output looks like yours.  Are you able to detect and pair BT devices on your Zbook?

---

### Post by RR123RR on 2011-10-25
> **campbelt said:**
> My lsusb -v output looks like yours.  Are you able to detect and pair BT devices on your Zbook?

Nope, I didn't try the console tools but the GUI just scans in vain...

---

### Post by renselu on 2011-10-27
Subscribing to this thread, have the same problems with an Asus UX31.

---

### Post by lemsto on 2011-11-02
From BlueZ site, I understand that Bluetooth 4.0 isn't available yet :
[http://www.bluez.org/profiles/](http://www.bluez.org/profiles/)

_EDIT _: Please forget this post, this is a misreading ...

---

### Post by erandom on 2011-11-21
I believe I have a solution - I need the cooperation of a UX21/UX31 who still has Windows installed on their machine. See below for details.

This module may require loading a firmware first. There's a lengthy description posted to the linux-bluetooth list:
[http://thread.gmane.org/gmane.linux.bluez.kernel/18756](http://thread.gmane.org/gmane.linux.bluez.kernel/18756)

However, all firmwares I could have laid my hands on did not work. I need the following file from the Windows partition on a Zenbook:
C:\Windows\System32\drivers\AtherosBt.bin (should be 246,804 bytes).

This file should be copied to '/lib/firmware/ath3k-1.fw' (keep the original somewhere safe), then the steps described in this post should be followed:
[http://www.phlerion.com/blog/2011/02/04/bluetooth-for-exopc-in-ubuntu/](http://www.phlerion.com/blog/2011/02/04/bluetooth-for-exopc-in-ubuntu/)
The only difference is the device id: Rather than using "13d3 3304", "13d3 3375" should be used.

If you have the file, please post it somewhere so.

---

### Post by renselu on 2011-11-22
[http://uploading.com/files/m33ddffa/AtherosBt.rar/](http://uploading.com/files/m33ddffa/AtherosBt.rar/)

Please let us know if it worked :)

---

### Post by erandom on 2011-11-22
> **renselu said:**
> [http://uploading.com/files/m33ddffa/AtherosBt.rar/](http://uploading.com/files/m33ddffa/AtherosBt.rar/)

Please let us know if it worked :)
Unfortunately, it didn't. I get the same error (Bluetooth: Error in firmware loading err = -110,len = 0,size = 4096) that I'm getting with any other firmware.
Perhaps a different approach is needed for this module.

---

### Post by erandom on 2011-11-22
I'd like to test the hypothesis that this is, indeed, a firmware-related problem.
When Bluetooth is enabled on Windows and you boot into Linux, does Bluetooth work then?

---

### Post by erandom on 2011-11-22
To follow up, I've been able to get Bluetooth working.
The key piece of information is that the Bluetooth module is using the Atheros AR3012.

Currently there is one other device, documented in the kernel, that does this - usb id 0cf3:3004.

To get bluetooth working on the UX31, you have to get the bluetooth modules (ath3k, btusb) to treat it the same as the one mentioned above. This is done by editing btusb.c and ath3k.c and duplicating the lines related to mentioned device. The ath3k module is only needed to load the firmware - so the firmware files should exist under /lib/firmware/ar3k.

To get it working, apply the attached patches to ath3k.c, btusb.c under <kernel_source>/drivers/bluetooth, recompile and install the new modules (patches are against 3.1.1).

---

### Post by RR123RR on 2011-11-22
> **erandom said:**
> To follow up, I've been able to get Bluetooth working.
The key piece of information is that the Bluetooth module is using the Atheros AR3012.

Currently there is one other device, documented in the kernel, that does this - usb id 0cf3:3004.

To get bluetooth working on the UX31, you have to get the bluetooth modules (ath3k, btusb) to treat it the same as the one mentioned above. This is done by editing btusb.c and ath3k.c and duplicating the lines related to mentioned device. The ath3k module is only needed to load the firmware - so the firmware files should exist under /lib/firmware/ar3k.

To get it working, apply the attached patches to ath3k.c, btusb.c under <kernel_source>/drivers/bluetooth, recompile and install the new modules (patches are against 3.1.1).

Has this been submitted to the upstream kernel developper responsible for that driver?
So we could hope to get this in the next release... :-)

---

### Post by nomego on 2011-11-23
Great work!

Actually, I think fastest/best would probably be to send it to the LKML.

Just create a combined or two separate patches with diff -up, attach to a mail to [email]linux-kernel@vger.kernel.org[/email] containing a subject that starts with [PATCH].

I submitted a patch like this in 2009 and it got picked up by the tree maintainer immediately: [https://lkml.org/lkml/2009/2/23/189](https://lkml.org/lkml/2009/2/23/189)

---

### Post by erandom on 2011-11-23
I've submitted a patch upstream, you can track progress here:
[http://thread.gmane.org/gmane.linux.bluez.kernel/18801](http://thread.gmane.org/gmane.linux.bluez.kernel/18801)

---

### Post by Oblong_Cheese on 2011-11-23
Hey guys,

Just wanted to say thanks for the awesome work on this. \\:D/

---

### Post by Oblong_Cheese on 2011-12-08
> **erandom said:**
> To follow up, I've been able to get Bluetooth working.
The key piece of information is that the Bluetooth module is using the Atheros AR3012.

Currently there is one other device, documented in the kernel, that does this - usb id 0cf3:3004.

To get bluetooth working on the UX31, you have to get the bluetooth modules (ath3k, btusb) to treat it the same as the one mentioned above. This is done by editing btusb.c and ath3k.c and duplicating the lines related to mentioned device. The ath3k module is only needed to load the firmware - so the firmware files should exist under /lib/firmware/ar3k.

To get it working, apply the attached patches to ath3k.c, btusb.c under <kernel_source>/drivers/bluetooth, recompile and install the new modules (patches are against 3.1.1).

This might be a dumb question, but I do not have the files you mention under /drivers/bluetooth - how do I get them?

I have been Googling for 30 minutes. :(

---

### Post by wim.glenn on 2011-12-19
Hi there, I'd love to get Bluetooth working properly on my zenbook UX31E , but patching the kernel and stuff sounds like something I could screw up majorly - I've only been using linux for <1 year.  Could someone post a bit more idiot-proof instructions on how to do it pretty please?

p.s., my kernel version seems to be 3.0.0 , does that mean I can't use this fix (because patches are against 3.1.1)?

    wim@wim-ubuntu:~/Desktop$ uname -a
    Linux wim-ubuntu 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Blinkiz on 2011-12-22
Great work trying to get bluetooth to work. Keep up the good work!

---

### Post by armorbear on 2011-12-22
Are you able to detect and pair BT devices on your Zbook?

---

### Post by kebabroyal on 2011-12-25
The patch works OK, I've been able to pair with my Nexus S phone and use obexftp and tethering.

Great work. Does anybody know if this patch is going to make it for 3.2 ?

---

### Post by moulip on 2011-12-27
> **kebabroyal said:**
> The patch works OK, I've been able to pair with my Nexus S phone and use obexftp and tethering.

Great work. Does anybody know if this patch is going to make it for 3.2 ?

I have just patched a 3.2 kernel and I am currently compiling it.
I will let you know if it works.
You can't apply the diffs directly on the 3.2 sources since they don't come from the same trunK.

What I did, is that I opened ath3K.c and btusb.c in VI and corrected the lines by hand.

Theorically it should work since it works the same way (making the driver binding the right hex address).

---

### Post by Fryie on 2012-01-05
> **wim.glenn said:**
> Hi there, I'd love to get Bluetooth working properly on my zenbook UX31E , but patching the kernel and stuff sounds like something I could screw up majorly - I've only been using linux for <1 year.  Could someone post a bit more idiot-proof instructions on how to do it pretty please?

p.s., my kernel version seems to be 3.0.0 , does that mean I can't use this fix (because patches are against 3.1.1)?

    wim@wim-ubuntu:~/Desktop$ uname -a
    Linux wim-ubuntu 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Hi, I had the same problem as you had, and I was also afraid of doing something stupid.
Then I googled some stuff about kernel compiling and tried it out. Miraculously, it actually worked (at least, these past 5 minutes I haven't had any issues ... xD). So I might actually help you (if you still need it - if not, someone else might stumble upon this thread some day, as I did).

Now, I want to emphasize that I'm not taking any responsibility if anything goes wrong, so make sure to backup everything before trying. I also do not use Ubuntu itself, but Linux Mint (which is based on Ubuntu). This shouldn't matter, though.

I basically followed [this post](http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/), by and large, but made the job somewhat simpler for myself by not using git and by using the main flavour ("generic"), instead of a custom named one.

So here's the deal:
1. You'll need some tools to compile, I'm not sure if all of these are necessary, but here you go:
```
sudo su -
apt-get install fakeroot build-essential
apt-get install crash kexec-tools makedumpfile kernel-wedge
apt-get build-dep linux-image-$(uname -r)
apt-get install git libncurses5 libncurses5-dev libnewt-dev
exit
```

2. Create some directory somewhere where you'd like to store the source files you'll want to compile, I'm calling it "kernel". Cd into that directory and get the kernel sources via git. (There's also other ways to get the source, but I haven't tested these.)
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-oneiric.git  source
```
This downloads the sources from the official repository into a subfolder named "source" (or whatever you like). Again, cd into it.
(This is all assuming you need the Oneiric kernel, which is (I think) 3.0.0.14 - if not, you might have to try to get your sources elsewhere.)

3. Now, before compiling the source, you'll have to actually make the relevant changes. It's in two files (courtesy of the guy who [figured this out](http://www.spinics.net/lists/linux-bluetooth/msg19019.html))
- First edit the file drivers/bluetooth/ath3k.c:
Find the section beginning with ```
static struct usb_device_id ath3k_table[] = {
```In this section, you should see two lines that look like this:
```
/* Atheros AR3012 with sflash firmware*/
{ USB_DEVICE(0x0CF3, 0x3004) },
```
Add this following new line directly below:
```
{ USB_DEVICE(0x13d3, 0x3375) },
```
Then, in the same file, look for the section beginning with:
```
static struct usb_device_id ath3k_blist_tbl[] = {
```
There should be two lines that read like this:
```
/* Atheros AR3012 with sflash firmware*/
{ USB_DEVICE(0x0cf3, 0x3004), .driver_info = BTUSB_ATH3012 },
```
Again, add this line directly below:
```
{ USB_DEVICE(0x13d3, 0x3375), .driver_info = BTUSB_ATH3012 },
```
Save the file and exit.
- Now, open the file drivers/bluetooth/btusb.c. Here you'll have to make only one change. Look out for the section starting with:
```
static struct usb_device_id blacklist_table[] = {
```
Here find the lines that say:
```
/* Atheros 3012 with sflash firmware */
{ USB_DEVICE(0x0cf3, 0x3004), .driver_info = BTUSB_ATH3012 },
```
Add the following directly below:
```
{ USB_DEVICE(0x13d3, 0x3375), .driver_info = BTUSB_ATH3012 },
```
Again, save and exit.

You should now have made three insertions in two files that make sure the kernel recognizes the correct bluetooth device.
Before proceeding, check that you've made no mistakes here, of course.

3. Now you'll actually have to compile the source. This takes four commands (I think the first one is not necessary, but I'm not sure as I'm no expert in these matters, so since it doesn't hurt, just execute it anyway):
```
fakeroot debian/rules clean
skipabi=true skipmodule=true fakeroot debian/rules binary-indep
skipabi=true skipmodule=true fakeroot debian/rules binary-perarch
skipabi=true skipmodule=true fakeroot debian/rules binary-generic

```
The last command takes very long (perhaps 1 hour or more) to execute even on a fast processor, so be prepared. 
(If you've followed the post I linked to more closely and have created a custom flavour instead of modifying "generic" directly (I have no idea how you'd do so, though), the last command changes of course to "... binary-yourflavour")

4. When all that is done, the compiled kernel packages will be in the *parent* folder (the one above "source", that I called "kernel"). So make a "cd .." and install:
```
sudo dpkg -i linux-headers-3.0.0-14-generic_3.0.0-14.23_amd64.deb linux-headers-3.0.0-14_3.0.0-14.23_all.deb linux-image-3.0.0-14-generic_3.0.0-14.23_amd64.deb
```
(If you have another kernel version, you'll need to adjust the file names.)

5. Just for safety, update grub:
```
sudo update-grub
```

6. Now, reboot, and if you're as lucky as I am, nothing has changed except that your bluetooth device will now be recognized!

I'm sorry if I explained that perhaps too abundantly for some, but I'd best make sure, I would have appreciated such a detailed tutorial. :)

Regards,
Fryie

---

### Post by phler2 on 2012-01-10
Hi i tested this with kernel 3.2 rc7 and it works
my mouse is now recognized

thanks

i'm hopping that patch makes it soon in mainstream packages

---

### Post by jhgouveia on 2012-01-11
I followed Fryie's post step by step, changing just the way to get the source (I got it using apt-get, instead of git), and it worked perfectly! :)

Great job! Thanks a lot!

```

apt-get source linux-image-$(uname -r)

```

---

### Post by moulip on 2012-01-18
> **Fryie said:**
> Hi, I had the same problem as you had, and I was also afraid of doing something stupid.
Then I googled some stuff about kernel compiling and tried it out. Miraculously, it actually worked (at least, these past 5 minutes I haven't had any issues ... xD). So I might actually help you (if you still need it - if not, someone else might stumble upon this thread some day, as I did).

Now, I want to emphasize that I'm not taking any responsibility if anything goes wrong, so make sure to backup everything before trying. I also do not use Ubuntu itself, but Linux Mint (which is based on Ubuntu). This shouldn't matter, though.

I basically followed [this post](http://blog.avirtualhome.com/2011/10/28/how-to-compile-a-new-ubuntu-11-10-oneiric-kernel/), by and large, but made the job somewhat simpler for myself by not using git and by using the main flavour ("generic"), instead of a custom named one.

So here's the deal:
1. You'll need some tools to compile, I'm not sure if all of these are necessary, but here you go:
```
sudo su -
apt-get install fakeroot build-essential
apt-get install crash kexec-tools makedumpfile kernel-wedge
apt-get build-dep linux-image-$(uname -r)
apt-get install git libncurses5 libncurses5-dev libnewt-dev
exit
```

2. Create some directory somewhere where you'd like to store the source files you'll want to compile, I'm calling it "kernel". Cd into that directory and get the kernel sources via git. (There's also other ways to get the source, but I haven't tested these.)
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-oneiric.git  source
```
This downloads the sources from the official repository into a subfolder named "source" (or whatever you like). Again, cd into it.
(This is all assuming you need the Oneiric kernel, which is (I think) 3.0.0.14 - if not, you might have to try to get your sources elsewhere.)

3. Now, before compiling the source, you'll have to actually make the relevant changes. It's in two files (courtesy of the guy who [figured this out](http://www.spinics.net/lists/linux-bluetooth/msg19019.html))
- First edit the file drivers/bluetooth/ath3k.c:
Find the section beginning with ```
static struct usb_device_id ath3k_table[] = {
```In this section, you should see two lines that look like this:
```
/* Atheros AR3012 with sflash firmware*/
{ USB_DEVICE(0x0CF3, 0x3004) },
```
Add this following new line directly below:
```
{ USB_DEVICE(0x13d3, 0x3375) },
```
Then, in the same file, look for the section beginning with:
```
static struct usb_device_id ath3k_blist_tbl[] = {
```
There should be two lines that read like this:
```
/* Atheros AR3012 with sflash firmware*/
{ USB_DEVICE(0x0cf3, 0x3004), .driver_info = BTUSB_ATH3012 },
```
Again, add this line directly below:
```
{ USB_DEVICE(0x13d3, 0x3375), .driver_info = BTUSB_ATH3012 },
```
Save the file and exit.
- Now, open the file drivers/bluetooth/btusb.c. Here you'll have to make only one change. Look out for the section starting with:
```
static struct usb_device_id blacklist_table[] = {
```
Here find the lines that say:
```
/* Atheros 3012 with sflash firmware */
{ USB_DEVICE(0x0cf3, 0x3004), .driver_info = BTUSB_ATH3012 },
```
Add the following directly below:
```
{ USB_DEVICE(0x13d3, 0x3375), .driver_info = BTUSB_ATH3012 },
```
Again, save and exit.

You should now have made three insertions in two files that make sure the kernel recognizes the correct bluetooth device.
Before proceeding, check that you've made no mistakes here, of course.

3. Now you'll actually have to compile the source. This takes four commands (I think the first one is not necessary, but I'm not sure as I'm no expert in these matters, so since it doesn't hurt, just execute it anyway):
```
fakeroot debian/rules clean
skipabi=true skipmodule=true fakeroot debian/rules binary-indep
skipabi=true skipmodule=true fakeroot debian/rules binary-perarch
skipabi=true skipmodule=true fakeroot debian/rules binary-generic

```
The last command takes very long (perhaps 1 hour or more) to execute even on a fast processor, so be prepared. 
(If you've followed the post I linked to more closely and have created a custom flavour instead of modifying "generic" directly (I have no idea how you'd do so, though), the last command changes of course to "... binary-yourflavour")

4. When all that is done, the compiled kernel packages will be in the *parent* folder (the one above "source", that I called "kernel"). So make a "cd .." and install:
```
sudo dpkg -i linux-headers-3.0.0-14-generic_3.0.0-14.23_amd64.deb linux-headers-3.0.0-14_3.0.0-14.23_all.deb linux-image-3.0.0-14-generic_3.0.0-14.23_amd64.deb
```
(If you have another kernel version, you'll need to adjust the file names.)

5. Just for safety, update grub:
```
sudo update-grub
```

6. Now, reboot, and if you're as lucky as I am, nothing has changed except that your bluetooth device will now be recognized!

I'm sorry if I explained that perhaps too abundantly for some, but I'd best make sure, I would have appreciated such a detailed tutorial. :)

Regards,
Fryie

Tried to do the trick on Debian but no luck. The bluetooth icon does not appear any longer and hcitool keep telling " device not available"

---

### Post by HandleWithCare on 2012-01-19
Thanks for the help, I do run in a problem though. In the "skipabi=true skipmodule=true fakeroot debian/rules binary-generic" step, after half an hour or so it stops with the following:
```
make: *** [install-generic] Error 1
```

Unfortunately I closed terminal too early so I cannot tell you what was the last output before. I will try it again, but if anyone knows what might cause in the meanwhile I'd be very happy to hear.

UPDATE:
I did the simplest fix possible, just restarted all over again and now I do have bluetooth.One problem now is that I don't have sound anymore. Whether this was caused by the new kernel, I don't know. The audio device does come up in lspci, but on the hardware tab in sound settings there is nothing. Did anyone else have this problem?

UPDATE 2:
A new day, and now bluetooth has stopped working again. I've done no updates whatsoever.

---

### Post by moulip on 2012-01-22
For Debian users, I was finally successful il getting the Bluetooth working !
I have compiled a 3.2-rc7 and patched it the way indicated in this thread.
I have then installed the following package :
firmware-atheros

It all works ! I don't use the final 3.2.1 since it drains the battery much faster.

---

### Post by MrHara on 2012-01-30
Has anyone tested succesfully USB4.0 dongles (low power) on Ubuntu? if yes on which driver settings

---

