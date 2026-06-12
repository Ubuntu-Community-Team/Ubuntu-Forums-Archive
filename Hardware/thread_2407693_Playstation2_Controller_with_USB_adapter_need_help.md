---
title: "Playstation2 Controller with USB adapter need help getting additional buttons to work"
date: 2018-12-07
forum: Hardware
---

### Post by needsahelpa on 2018-12-07
Hi all

i tried and checked about a week now to get a PS2 controller working on my linux machine, hardware works fine, the adapter works with same controller on same machine with windows perfectly fine,
unfortunately the following buttons (Square, Circle,X) do not seem to exist in the driver or kernel driver or wherever that info should be available, all others seem to do something, even if i check with (cat /dev/input/eventX) all buttons give some output but not the mentioned ones the 3 ones seem dead and non existent. i found many guides talking about PS3 controller and it being about Bluetooth, but this is hardwired, with an adapter to USB,

i tried antimicro, says same i.e 13 buttons 3 buttons are missing same is in Jstest.
im running Lubuntu Linux 4.15.0-42-generic #45-Ubuntu SMP Thu Nov 15 19:32:57 UTC 2018 x86_64 x86_64 x86_64 GNU/Linu


i ran across this:
[http://domisan.sakura.ne.jp/article/psxpad/psxpad.html](http://domisan.sakura.ne.jp/article/psxpad/psxpad.html)

it seems a patch for raspi, altough i have no idea, if it is modifiable to work with amd/intel/64bit cpu, any help appreciated, have no experience in patching a kernel or compiling,
here is what i tried

patch -p1 -d /usr/src/linux-headers-4.15.0-42 < psxpad-spi_rp.patch

which gave me this 

|diff -uprN linux_org/arch/arm/boot/dts/bcm2708-rpi-0-w.dts linux_alt/arch/arm/boot/dts/bcm2708-rpi-0-w.dts
|--- linux_org/arch/arm/boot/dts/bcm2708-rpi-0-w.dts	2017-05-08 23:58:26.103387000 +0900
|+++ linux_alt/arch/arm/boot/dts/bcm2708-rpi-0-w.dts	2017-04-25 10:57:51.000000000 +0900

i assume the patch is for ARM cpu, and i am wondering if the file is modifiable to work with x86/64 architecture.

and yes i am possibly doing everything wrong, apologies in that case, any help appreciated.


please help and let me know what else info is needed.

thank you in advance.

---

### Post by slickymaster on 2018-12-07
Thread moved to **Hardware** for a better fit

---

### Post by needsahelpa on 2018-12-08
hrmm the biggest problem i seem to have is that there is alot of outdated information and it is for me personally impossible to find out which and what i should be looking for to get it running with Ubuntu 18.04 kernel 4.15.0-42, there is talk of SDL2 then there is talk of xboxdrvr, and i actually found that "/dev/usb/hiddev1" in my case, by doing "cat /dev/usb/hiddev1" does give me some output and does give me some output pushing X,Square and Circle, as well as all other buttons, so i thought id simply try to do "ln - n /dev/usb/hiddev1 /dev/input/js0" ofc that got me nothing at all, game controller was not recognized by SDL2, antimicro, Qjoypad, or jstest im ofc 100% sure im doing something wrong, but i might be on the right path to fix this issue??? any input apriciated

i also found this
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836335](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836335)

it apeares also to be a bug apparently, this person has exactly the same problem that i seem to have, but well it seems completely abandoned and never fixed. now im not sure if that is actually a fact or not and if there is a replacement for that or some other way to get this working. or if i should just forget about it and throw just my precious Playstation 2 controller into the landfill and contribute to the destruction of our planet further.

---

### Post by pqwoerituytrueiwoq on 2018-12-09
It should just work, you just need to configure inputs to do something with most software, raw input data can be accessed via [FONT=Courier New]/dev/input/js0[/FONT] the number will go up if multiple controllers are connected, so 4 controllers would use 0-3
here are the input maps for a PS3 controller, config data is from GUI called emulationstation
```

<inputConfig type="joystick" deviceName="Sony PLAYSTATION(R)3 Controller" deviceGUID="030000004c0500006802000011810000">
        <input name="a" type="button" id="0" value="1" /> <!-- X -->
        <input name="b" type="button" id="1" value="1" /> <!-- Circle -->
        <input name="down" type="button" id="14" value="1" />
        <input name="hotkeyenable" type="button" id="10" value="1" />  <!-- Playstation logo button -->
        <input name="left" type="button" id="15" value="1" />
        <input name="leftanalogdown" type="axis" id="1" value="1" />
        <input name="leftanalogleft" type="axis" id="0" value="-1" />
        <input name="leftanalogright" type="axis" id="0" value="1" />
        <input name="leftanalogup" type="axis" id="1" value="-1" />
        <input name="leftshoulder" type="button" id="4" value="1" />
        <input name="leftthumb" type="button" id="11" value="1" />
        <input name="lefttrigger" type="button" id="6" value="1" />
        <input name="right" type="button" id="16" value="1" />
        <input name="rightanalogdown" type="axis" id="4" value="1" />
        <input name="rightanalogleft" type="axis" id="3" value="-1" />
        <input name="rightanalogright" type="axis" id="3" value="1" />
        <input name="rightanalogup" type="axis" id="4" value="-1" />
        <input name="rightshoulder" type="button" id="5" value="1" />
        <input name="rightthumb" type="button" id="12" value="1" />
        <input name="select" type="button" id="8" value="1" />
        <input name="start" type="button" id="9" value="1" />
        <input name="up" type="button" id="13" value="1" />
        <input name="x" type="button" id="3" value="1" /> <!-- Square -->
        <input name="y" type="button" id="2" value="1" /> <!-- Triangle -->
</inputConfig>

```

[jstest]("apt:joystick") can show you if buttons are responding:
[FONT=courier new]jstest --event /dev/input/js0[/FONT]

have you verified that the buttons are not broken?  some times it only takes a little rubbing alcohol and a tooth brush to clean up a circuit board so it will work again, but be aware if something is really damaged and you want someone to fix it being able to see where the dirt was would have been helpful to them in figuring out what component need to be replaced

---

### Post by needsahelpa on 2018-12-09
thx for the reply, there is no change in the behaviour, the 3 buttons, square, cicrcle and X do not respond at all, all other buttons do.

---

### Post by deadflowr on 2018-12-09
What's the actual adapter?
There are like a dozen or more adapters.
what does it show in
```
lsusb
```

---

### Post by needsahelpa on 2018-12-09
here a more detailed output of "lsusb"
```
Bus 003 Device 011: ID 054c:0268 Sony Corp. Batoh Device / PlayStation 3 Controller
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x054c Sony Corp.
  idProduct          0x0268 Batoh Device / PlayStation 3 Controller
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     184
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
```

---

### Post by needsahelpa on 2018-12-14
Bump

---

### Post by needsahelpa on 2018-12-23
bump

---

### Post by needsahelpa on 2018-12-30
bump

---

### Post by quollmarten on 2019-01-23
Hello!
I just happened to get exactly such adapter from Aliexpress. I also bought a chinese PS2 controller in local store. Everything works fine on Windows (except **analog indicator** is always on no matter what). But pressing **square, O and X buttons **doesn't seem to be detected by Linux drivers.

```
sudo cat /dev/usb/hiddev1
```
Raw output shows that button presses definitely send signals. (device number may vary)

```
evtest /dev/input/event14
```
But pressing aformentioned buttons during evtest doesn't trigger any events (triangle and all the others work fine) (event number assigned to the gamepad may vary)

```

jstest /dev/input/js0 
Driver version is 2.1.0.
Joystick (Sony PLAYSTATION(R)3 Controller) has 6 axes (X, Y, Z, Rx, Ry, Rz)
and 13 buttons (BtnX, BtnTL, BtnTR, BtnTL2, BtnTR2, BtnSelect, BtnStart, BtnThumbL, BtnThumbR, (null), (null), (null), (null)).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2:-32767  3:     0  4:     0  5:-32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off
```

jstest doesn't even have those three buttons listed.


There's definitely something going on with the driver. Does anyone have any idea how to solve this? Thank you!

UPD: both jscal and jstest see 6 axes and 13 buttons, while there must be 6 axes and 16 buttons.

---

### Post by fabio.vix on 2019-03-28
Hello ! I do have exactly the same problem in Ubuntu 18.04 LTS:  the Square, Circle and Cross buttons are missing. 
I'm just using a PS2 joypad with a USB adaptor.  The other controls are all recognized on jstest.
My dmesg output:

```
[1335.375921] usb 2-6.1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1335.375925] usb 2-6.1.3: Product: PLAYSTATION(R)3 Controller
[ 1335.375929] usb 2-6.1.3: Manufacturer: Sony
[ 1335.384225] input: Sony PLAYSTATION(R)3 Controller Motion Sensors as /devices/pci0000:00/0000:00:14.0/usb2/2-6/2-6.1/2-6.1.3/2-6.1.3:1.0/0003:054C:0268.0007/input/input26
[ 1335.443247] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:14.0/usb2/2-6/2-6.1/2-6.1.3/2-6.1.3:1.0/0003:054C:0268.0007/input/input25
[ 1335.443592] sony 0003:054C:0268.0007: input,hiddev3,hidraw5: USB HID v81.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:14.0-6.1.3/input0
```

It's looks like a touble since 2012!! Any update on this?

---

### Post by m3fisto on 2019-09-26
I am facing the same problem with Raspberry pi Retropie 4.4, 4.5.1 and with Ubuntu 18.04 as well.
I have bought several ps2->USB adapters from various sellers and I have found 2 different boards with 2 different problems. The ones recognized as "PLAYSTATION(R)3 Controller" have the issue described here (missing 3 buttons)
The ones recognized as "USB GAMEPAD" work fine BUT ONLY FOR A FEW MINUTES. Then they start random ghost key presses and are inoperable until the linux is shutdown and the adapter is removed....
Any suggestion is more than welcome

---

### Post by Sliver X on 2019-10-09
I realize this is a fairly old thread, but I recently ran into this exact same issue myself. 

Since no resolution appears to have been found in any of the forum threads/etc I ran across researching a fix I wanted to post the method I used to resolve it: Hopefully those here and those in the future that stumble across this can get some use from it too.

I run a no-name Dualshock/Dualshock 2 to PS3 USB adapter, so my DS1 presents itself to the OS as a Dualshock 3. With Ubuntu 18.04 and 19.04, the adapter shows up as this under jstest (Abbreviated):

**Joystick (Sony PLAYSTATION(R)3 Controller) has 6 axes … and 13 buttons …**

Several buttons and the d-pad don't work and the axes are weird. It is utterly useless as a gamepad in this state.

However, I recently tried another distro that ships with an older kernel (antiX - Linux 4.9.16) and was amazed to see the adapter come up as a fully working device:

**Joystick (Sony PLAYSTATION(R)3 Controller) has 5 axes … and 19 buttons …**

I ended up digging into why this particular distro/kernel worked. Apparently it is due to changes made in the DS3 driver (sony-hid) around Linux 4.10 that broke a lot of third party adapters such as mine. So...

I downloaded Linux 4.9.196's sources and extracted them. Two files are of interest in here:

linux-source-4.9/drivers/hid/hid-sony.c
linux-source-4.9/drivers/hid/hid-ids.h

I then made a Makefile with the following:

[B]obj-m += hid-sony.o
 
all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
 
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean[/B]

I then threw all three into a subfolder named hid-sony (I did all this in /tmp: Wherever you want is fine).

In a root terminal at the folder above hid-sony (For me, /tmp), I ran the following:

[B]cd ./hid-sony

make

rmmod hid_sony
rm -f /lib/modules/$(uname -r)/kernel/drivers/hid/hid-sony.ko

cp ./hid-sony.ko /lib/modules/$(uname -r)/kernel/drivers/hid/
insmod /lib/modules/$(uname -r)/kernel/drivers/hid/hid-sony.ko 

make clean[/B]

This entirely replaces the existing driver module with the 4.9 version. After doing this, my gamepad is now fully functional  under Ubuntu 18.04.

I initially planned to build this as a separately named kernel object and to disable sony-hid and enable the new module on every boot but ultimately just decided to overwrite the newer module file and be done with it. 
So you may want to back up the original sony-hid.ko file or create a more elegant method of getting the 4.9 module into your OS install, as what I just showed *will* permanently replace whatever version came with your particular kernel.

I also did this on Ubuntu 19.04 AMD64 and it also worked as expected. Native Linux games, emulators and games under Wine utilize it with no issues whatsoever.

I’ll have to do this with every kernel update, but I can live with that. Hopefully anyone with a similar issue to mine will be helped by this.

(Note: You'll need your current kernel's headers and build-essential installed to make this work)

*edit* I've attached the driver source from Linux 4.9.196, the makefile and an installer script. I make absolutely no warranties that it won't make your system explode: Use at your own risk (And back up the original module file).

*edit2* I've updated the archive with another script that will handle this with DKMS, so you don't have to recompile on every kernel update.

---

### Post by norber-ok-gmail on 2019-11-06
Thanks
THANKS
T H A N K S

THANK YOU VERY MUCH !!!

Yo have SOLVED this problem !!
You are a monster master.

Thanks, thanks, thanks .... for ever.

---

### Post by pantalaimon2 on 2020-01-19
Great find!
Can you try the commits [between 4.9 and 4.10]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/log/drivers/hid/hid-sony.c?h=v4.10") to find the commit that broke this?
Would be great to get this fixed in newer Kernels again.

---

### Post by scshumat on 2020-05-13
I just bought a pair of these adapters from Amazon and ran into this same problem - the X, square, and circle buttons do not work in Linux.  I decided to do a little digging with usbhid-dump and discovered that the hardware is reporting a USB descriptor with only 13 buttons instead of the requisite 16.  I then created a Linux kernel patch that corrects the invalid descriptor and everything is working perfectly now on my system.  I submitted a patch to the Linux kernel mailing list so hopefully it will be accepted and will be fixed in an upcoming kernel release.

Here's a description of the patch: [https://lkml.org/lkml/2020/5/13/1323](https://lkml.org/lkml/2020/5/13/1323)

FYI - The kernel commit that breaks these adapters is e19a267b9987.  This commit removed a USB descriptor fix-up that masked this problem.

-Scott

---

### Post by skeetzoid on 2020-05-13
Thank you Sliver X for this solution!  My PS2 controller with USB adapter runs properly again on 18.04 with the circle, x, and square buttons.

[ATTACH=CONFIG]285860[/ATTACH]

---

### Post by mantoxpub on 2020-11-17
i've tried this patch with my [Dragon PS2 Controller to PS3-PC Converter Cable V2]("https://www.amazon.co.uk/Playstation-Controller-Adapter-PS2-PS3/dp/B001IKYMW8").
the X and square buttons are not working correctly, but the d-pad is not:
 it is mapped to buttons 17,18 and 19 which are inverted (stays pressed when released) and the axes 9,10,11 which have some weird ranges.

---

