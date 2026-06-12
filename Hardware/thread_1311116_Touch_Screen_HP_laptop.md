---
title: "Touch Screen HP laptop"
date: 2009-11-02
forum: Hardware
---

### Post by myquidproquo on 2009-11-02
Hi, everyone.

I'm using Karmic on my new HP dv3-2250ep laptop. This laptop uses a Touch Screen, but I can't get it to work at all in Ubuntu.
I've been searching but it seems that there are multiple types of touch screen technology and I don't even know which one this laptop uses. 

Can you help me figuring out which hardware is it? Any command that would be helpful?

I don't know if this helps but in Win7 I can use my fingers (no need for pen) to use the touch screen. I also can use 2 fingers to make a zoom action, so I guess it is multi touch.

Thank you for the help.

---

### Post by Favux on 2009-11-04
Hi myquidproquo,

This thread would be a good place to post all the info. you've collected.  It sounds like it has two finger touch (at least) like the new Wacom Bamboo Pen & Touch tablets.  So I'd guess it uses the same touch screen technology.

---

### Post by nerdiest on 2009-11-21
Same problem here. I tried to install evtouch, but apparently the hp touchscreen is not evtouch-compatible. Do anyone has an idea what it should be?

---

### Post by Ayuthia on 2009-11-21
> **nerdiest said:**
> Same problem here. I tried to install evtouch, but apparently the hp touchscreen is not evtouch-compatible. Do anyone has an idea what it should be?

It depends on the digitizer that is installed on the HP laptop.  The dv3, TX2000 series use the Wacom kernel module and the Wacom driver.  The tx2 series uses the hid-ntrig kernel module but is currently using the Wacom driver also.  The HP desktops have a NextWindow screen and uses evtouch if I recall correctly.

So if you can let us know which model HP touchscreen you have, we can help point you in a direction.

---

### Post by nerdiest on 2009-11-21
I have a dv3 laptop. I tried to look at [http://www.wacom.com/downloads/drivers.php](http://www.wacom.com/downloads/drivers.php) for a driver, but I didn't find a file for TX2000, as you tell me the hardware is called. I'll greatly appreciate any direction you can give me.

Thank you for your help!

---

### Post by Favux on 2009-11-21
Hi nerdiest,

Not a problem, but let's be sure we know what you have.  On the bottom of the laptop on the backplate should be the model number.  Could you list it (them) exactly.  We don't want to steer you to the wrong place.  It's just you said brand new and the TX2000 has been out for about a year and a half.

Also in a terminal enter (copy and paste):
```
more /proc/bus/input/devices
(and/or)
grep -i name /proc/bus/input/devices
```

---

### Post by nerdiest on 2009-11-21
Hi again,

what I have on the bottom of my laptop is HP Pavilion dv3-2230ef. I don't see a specific model number for the touchscreen.

the output of the two commands is:

> more /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=20000 0 20 0 0 0 0 500f 2100003 3803078 f900d401 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/device:08/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0003 Vendor=045e Product=008c Version=0111
N: Name="Microsoft Microsoft Wireless Optical Mouse® 1.0A"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=1c3
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="ST LIS3LV02DL Accelerometer"
P: Phys=lis3lv02d/input0
S: Sysfs=/devices/platform/lis3lv02d/input/input8
U: Uniq=
H: Handlers=event8 js0 
B: EV=9
B: ABS=7

I: Bus=0003 Vendor=064e Product=a102 Version=0341
N: Name="HP Webcam"
P: Phys=usb-0000:00:1d.7-5/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0001 Vendor=111d Product=7608 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input11
U: Uniq=
H: Handlers=mouse2 event11 
B: EV=b
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic at Ext Front Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HP Out at Ext Front Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
U: Uniq=
H: Handlers=event13 
B: EV=21
B: SW=4



> 
grep -i name /proc/bus/input/devices

N: Name="Power Button"
N: Name="Power Button"
N: Name="Lid Switch"
N: Name="Sleep Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="Microsoft Microsoft Wireless Optical Mouse® 1.0A"
N: Name="ST LIS3LV02DL Accelerometer"
N: Name="HP Webcam"
N: Name="HDA Digital PCBeep"
N: Name="SynPS/2 Synaptics TouchPad"
N: Name="HDA Intel Mic at Ext Front Jack"
N: Name="HDA Intel HP Out at Ext Front Jack"



---

### Post by Favux on 2009-11-21
Hi nerdiest,

Thank you for the output.  I found it on French websites and it does look brand new.  Did you just buy it?  Is it suppose to have a multi-touch touch screen?  It doesn't look like it has a swivel hinge to convert it into a tablet pc.  Or does it?

Wacom is not showing up on the output.  It may be because it is so new that the Karmic default linuxwacom drivers do not support it yet.  Check in Synaptic Package manager and see if both packages are installed:  wacom-tools & xserver-xorg-input-wacom

We also need to take a look at your lshal.  In a terminal enter:
```
lshal>nerdiest_lshal.txt
```
Then right click on it and compress it using Create Archive.  Then attach it to your next post using Manage Attachments.

I'm sorry it is taking so long to figure out what touch screen you have.

---

### Post by nerdiest on 2009-11-21
I myself am sorry that I'm taking so much of your time! 10x a lot :)

The file is here: [http://314c.com/nerdiest_lshal.txt.tar.gz](http://314c.com/nerdiest_lshal.txt.tar.gz)

Yes, it's a brand new computer: I bought it today and it toke me a lot of time putting the correct video card drivers (to enable compiz) and the same for the sound card. But now all these just work perfectly (but no, it doesn't turn into tablet).

---

### Post by Favux on 2009-11-21
Hi nerdiest,

Great, I know what it is and how to get it to work!  I thought I did but I had to be sure that it wasn't the E3 or something.  It's the new Wacom multi-touch screen and we've been calling it the E2.
```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'  (string)
  info.product = 'ISD-V4'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial'  (string)
  info.vendor = 'Wacom Co., Ltd'  (string)
  linux.device_file = '/dev/bus/usb/008/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2'  (string)
  usb_device.bus_number = 8  (0x8)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 3329  (0xd01)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'ISD-V4'  (string)
  usb_device.product_id = 226  (0xe2)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0'  (string)
  usb.bus_number = 8  (0x8)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 3329  (0xd01)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 226  (0xe2)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 1.1 (1.1) (double)
```
We just set up the first one about a week ago.  Here is the [thread]("http://ubuntuforums.org/showthread.php?t=1314869").  Basically because it is so new you have to use the newest developmental linuxwacom driver which is 0.8.5-4.  New multi-touch gestures were just added to 5-4.  You'll need to compile it and a .fdi for it.  I can write a new .fdi for you now.

So look through the thread and see what you need to do.  It looks more complicated than it is because there is a lot of explanation.  But actually not that many steps.  Ask if you have questions.

---

### Post by edkwok on 2009-11-21
Hi FAVUX,

   I have a similar problem with my touch screen, can you take a look at my /proc/??/??/??

Background:
   I have installed Ubuntu 9.04 from a CD to a Samsung Q1Ultra (aka UMPC).  The initial MINI Root boot up from the CD and the pressure mouse integrated into the system work, but after a hardware scan and try to do the hard drive install, I lost the mouse.  So, my work around is to install Ubuntu 9.04 using text mode and apt-get x-windows and KDE desktop package.  I have to use a USB mouse.  But if I can get the touch screen going, than I can work and troubleshoot a little better, because the system is not 100% working right yet.  In the back of my Samsung Q1Ultra doesn't have any info on what mode of the touch screen.  Here is the file I capture.  Please take a look at it and let me know if you can tell me what else need to be loaded to make the touch screen work for me....thanks.

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name=&#8221;Power Button (FF)&#8221;
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0
B: EV=3
B: Key=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name=&#8221;Power Button (CM)&#8221;
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=3
B: Key=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name=&#8221;Sleep Button (CM)&#8221;
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E/input/input2
U: Uniq=
H: Handlers=kbd event2
B: EV=3
B: Key=4000 0 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name=&#8221;Macintosh mouse button emulation&#8221;
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name=&#8221;AT Translated Set 2 keyboard&#8221;
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c016 Version=0110
N: Name=&#8221;Logitech Optical USB Mouse&#8221;
P: Phys=usb-0000:00:1d.01/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event5
B: EV=17
B: Key=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=0eef Product=0001 Version=0112
N: Name=&#8221;Touchkit Touch&#8221;
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input6
U: Uniq=
H: Handlers=mouse2 event6
B: EV=1b
B: Key=401 0 30000 0 0 0 0 0 0 0 0
B: ABS=f
B: MSC=10

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name=&#8221;PC Speaker&#8221;
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input7
U: Uniq=
H: Handlers=kbd event7
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name=&#8221;Video Bus&#8221;
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input8
U: Uniq=
H: Handlers=kbd event8
B: EV=3
B: Key=3f000b 0 0 0 0 0 0 0

---

### Post by edkwok on 2009-11-21
Favux, please read this message, not sure why it posted this way....

---

### Post by Favux on 2009-11-21
Hi edkwok,

Did you read my [reply]("http://ubuntuforums.org/showpost.php?p=8358833&postcount=2") on your thread?  We should continue on that thread because you have a different machine.  I'll need to see at least the lshal.

---

### Post by nerdiest on 2009-11-24
Hi again Favux. 

I downloaded and compiled the last beta of linuxwacom and tried to configure my touchscreen, but unfortunately I don't get something. I attach you an archive with my lshal, fdi file and xorg.conf. Can you take a look at them?

---

### Post by Favux on 2009-11-24
Hi nerdiest,

I think it's the .fdi you are using.  It's not quite right.  You did change 'if1' to 'if0' for touch but you should delete the 'if0' with the stylus and eraser.  Which is why HAL isn't being configured.

Would you do me a favor and try the [new generic .fdi here]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579")?  It should work for you, and hopefully most everyone.  Just replace the current 10-linuxwacom.fdi with it.

---

### Post by nerdiest on 2009-11-24
Hmm, no, it doesn't work for me: I've just copied your fdi file to/usr/share/hal/fdi/policy/20thirdparty and reboot. Maybe I'm missing some other point?

---

### Post by Favux on 2009-11-24
Hi nerdiest,

Well I hope its not the .fdi.  It's worked for another E2.

Are you sure you compiled and installed linuxwacom 0.8.5-4 and not 0.8.4-4?

Is the wacom.ko auto-loading?:
```
lsmod | grep wacom
```
Should return output with wacom in it.

---

### Post by nerdiest on 2009-11-24
Hi again Favux,

I've just checked the file I downloaded &#8722;*it's 0.8.5-4.

About *lsmod | grep wacom*: nope, it returns nothing. In my /etc/modules file I have tried putting simply wacom.ko, but also putting the whole path to it.

---

### Post by Favux on 2009-11-24
Hi nerdiest,

That's strange.  Does wacom.ko exist?
```
modinfo -n wacom
```

---

### Post by nerdiest on 2009-11-25
yes, *modinfo -n wacom* gives:

/lib/modules/2.6.31-14-generic/kernel/drivers/input/tablet/wacom.ko

---

### Post by Favux on 2009-11-25
Hi nerdiest,

There weren't any compile errors you noticed were there?

When you copied to wacom.ko into place you use this command:
```
sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
correct?

---

### Post by Favux on 2009-11-25
Hi nerdiest,

Let's try the stripped down basic .fdi for the E2 and see if it works.  As you know it goes to "/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi".
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">touch</merge>
	<merge key="info.product" type="string">touch</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
It's possible something in the compile didn't go right.  Some folks in Karmic say they need to add:
```
apt-get install xserver-xorg-input-all
```
after the purge line.  I'm not sure about that.  It may be a new dependency?

The other thought is that you have another wacom.fdi accidentally installed.  That will mess it up for you too.

---

### Post by nerdiest on 2009-11-25
Hi Favux,

I tried to install the driver on a clean install of karmic, but it still doesn't work. What I did is:
```

> wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.5-4.tar.bz2
> sudo apt-get update
> sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
> sudo apt-get upgrade
> wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
> sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
> cd linuxwacom-0.8.5-4/
> ./configure --enable-wacom --prefix=/usr > configure_nerdiest.txt
> make > make_nerdiest.txt
> sudo make install > makeinstall_nerdiest.txt
> libtool --finish /usr/local/lib/TkXInput
> libtool --finish /usr/local/lib
> locate wacom.ko

```
The last gave:/lib/modules/2.6.31-14-generic/kernel/drivers/hid/hid-wacom.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/input/tablet/wacom.ko

```

> modinfo -n wacom 
```

/lib/modules/2.6.31-14-generic/kernel/drivers/input/tablet/wacom.ko

```

> modinfo -d wacom

```
USB Wacom Graphire and Wacom Intuos tablet driver
USB Wacom Graphire and Wacom Intuos tablet driver

```
> gksudo gedit /etc/modules
```

and I added 'wacom' at the bottom

```
> sudo reboot
```

```
sudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
```

And I loaded the short version of your .fdi.

```
> sudo reboot
> wacomcpl 
```

I try to start wacomcpl. When I start it, I see a panel on the left "Select the Device" with no devices listed. When I tried to install xserver-xorg-input-all as you adviced me, I've got a message that the package is already installed. What's bothering me is that there is nothing about the touchscreen in the /etc/X11/xorg.conf. Should I put something or should it be there only by virtue of the compilation/installation process? I attach you an archive of files that I generated during the installation.

Cheers,

---

### Post by Favux on 2009-11-25
Hi nerdiest,

With Jaunty and Karmic you don't need any Wacom stuff in xorg.conf.  You didn't do:
```
sudo apt-get install libhal-dev
```
So hal-setup-wacom wasn't built.  That probably doesn't matter.  You also didn't do the purge lines, which may matter.  A version conflict could cause the symptoms you have.

My main concern is you didn't show yourself doing the wacom.ko copy command:
```
sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
You definitely need the wacom.ko you compiled in place.

---

### Post by i_ReEm on 2009-12-04
Hi,
I have HP dv3-2270ev and I think it's very similar to nerdiest laptop.
I was following you step by step but I downloaded linuxwacom-0.8.5-5 ..
I haven't edited the .fdi file yet, should I add the tags that Favux posted to the original file or create a new one with that?
Thanks

---

### Post by Favux on 2009-12-04
Hi i_ReEm,

Welcome to Ubuntu Forums!

Make a back up of the default 10-linuxwacom.fdi (assuming you're in Karmic).

Then replace it with the .fdi you want to use, still named 10-linuxwacom.fdi.  You want to use only one wacom.fdi at a time.

---

### Post by i_ReEm on 2009-12-05
Hi Favux,
It might be my first post here because I always find the solution before I need to say any word ;)
I'm using Ubuntu 9.10
Here's my current 10-linuxwacom.fdi: "I might have changed with it a little bit in the last few days! I really can't remember!!"
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- this is probably a bit imprecise -->
<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains_outof="Wacom">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
	<append key="wacom.types" type="strlist">cursor</append>
	<append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
	<append key="info.capabilities" type="strlist">input</append>
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
	<merge key="input.device" type="copy_property">serial.device</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
	  <!-- Serial tablets with touch capabilities -->
	  <append key="wacom.types" type="strlist">touch</append>
	</match>
        <match key="@info.parent:pnp.id" contains_outof="WACf008">
          <!-- Serial tablets that operate at higher baud rate -->
          <merge key="input.x11_options.BaudRate" type="string">38400</merge>
       </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
	  <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	  <append key="wacom.types" type="strlist">eraser</append>
	  <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>

```
I really don't know if I should replace it all with what you have written above!!
Thanks in advance

---

### Post by Favux on 2009-12-05
Hi i_ReEm,

Sure, why not.  The only part of the .fdi that applies to a usb wacom digitizer like you have is:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- this is probably a bit imprecise -->
<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains_outof="Wacom">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
	<append key="wacom.types" type="strlist">cursor</append>
	<append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
</deviceinfo>

```
And notice you don't have a stylus, eraser, cursor (a Wacom mouse), or pad (buttons on a Wacom tablet).  But you do have touch which isn't even mentioned!

---

### Post by i_ReEm on 2009-12-05
I changed 10-linuxwacom.fdi to this:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">touch</merge>
	<merge key="info.product" type="string">touch</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```
but nothing happened!
should I add this <device> tag to the original .fdi? or edit something there!!
what should I expect to happen now?

---

### Post by Favux on 2009-12-05
Hi i_ReEm,

Did you reboot?  If you now only have one 10-linuxwacom.fdi and the contents are as above your touch should now be working.  Since it isn't we have to now figure out why it isn't.

In a terminal enter:
```
xinput --list
```
and let's look at the output.  Also let's look at your Xorg.0.log located in "/var/log/".  Given that you have compiled and installed linuxwacom 0.8.5-5 to see if the linuxwacom usb kernel driver/module is loading enter:
```
lsmod | grep wacom
```

 We'll also want to look at your lshal, so in a terminal:
```
lshal>lshal.txt
```
That will place a file called lshal.txt in your "/home/yourusername/" directory.  Right click on it and compress it with Create Archive and attach it to your next post with Manage Attachments.

---

### Post by i_ReEm on 2009-12-05
Yes I rebooted.
The attached files are the output of : xinput --list and lshal
the output of lsmod | grep wacom is:
```

wacom                  27860  0 

```

---

### Post by Favux on 2009-12-05
Hi i_ReEm,

Good, the kernel module is auto-loading.  Both the xinput and lshal show the Synaptic Touchpad driver is grabbing your Wacom touchpad.  The lshal shows:
```
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'  (string)
  input.product = 'Wacom ISDv4 E2'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_options.Type = 'touch'  (string)
  linux.device_file = '/dev/input/event9'  (string)
```
So we need to fix your Synaptic .fdi.  See [post #22]("http://ubuntuforums.org/showpost.php?p=8372380&postcount=22") in this thread.  Hopefully that will do it for you.

---

### Post by i_ReEm on 2009-12-05
I did that too and rebooted again but nothing happened :(

---

### Post by Favux on 2009-12-05
Well let's look at your Xorg.0.log then.  That should have worked, darn.

---

### Post by i_ReEm on 2009-12-05
and how is that done?

---

### Post by Favux on 2009-12-05
Hi i_ReEm,

Well I guess there's a few ways.  Navigate to it in Places (Nautilus) and double click on it.  That will open it in Text Editor (gedit).  Right click on it and choose select all.  Place it in (paste) a New file/tab in gedit.  Save it as say i_ReEm_Xorg.0.log.txt to your Desktop.  Then right click on the new file on your desktop and compress it with Create Archive.  Then attach to your next post with Manage Attachments.

---

### Post by i_ReEm on 2009-12-05
Here's my Xorg.0.log file

---

### Post by Favux on 2009-12-05
Hi i_ReEm,

Well the good news is the Synaptic .fdi change seems to have worked:
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) touch: always reports core events
(**) touch device is /dev/input/event9
(**) touch is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) touch: serial speed 9600
(II) XINPUT: Adding extended input device "touch" (type: Wacom Touch)
(**) Option "Device" "/dev/input/event9"
touch Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=2985 maxY=1687 maxZ=255 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "touch" top X=0 top Y=0 bottom X=29750 bottom Y=16770 resol X=10126 resol Y=10100
```
I don't know why it is saying:
```
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=2985 maxY=1687 maxZ=255 resX=1016 resY=1016  tilt=enabled
```
The 0.8.5 series linuxwacom should recognize your tablet.  That's why we're using it.  Is there a bug in 0.8.5-5 that accidentally dropped the E2?  Or some problem with your compile?

Anyway let's try in a terminal:
```
xsetwacom set touch touch on
```
and see if that turns touch on for you.  And if that doesn't work maybe:
```
xsetwacom set touch Gesture on
```

---

### Post by i_ReEm on 2009-12-17
I tried that but it didn't work :(
(when I tried the last 2 commands a few days ago then rebooted nothing happened, but today I tried them and I got the following error:

Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'touch'

)

---

### Post by Favux on 2009-12-17
Hi i_ReEm,

Did you get a kernel update recently?  That breaks the linuxwacom compile and you have to redo it.  Linuxwacom is up to 0.8.5-7 now.  I suggest you compile and install the new version using the [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Then let's see where you are.  Remember to back up any wacom.fdi you want to keep because the HOW TO will probably remove it.

---

### Post by ChadiM on 2009-12-30
Hi Favux,

Thank you for your cooperation and for helping us solve this issue.

I have the same laptop as i_ReEm, but in my case,
```
lsmod | grep wacom
```

does not show anything** like the author of this thread :/

And the term "Wacom" is not in the XOrg.0.log file.

**
Edit: It now shows wacom 22052 (I added wacom to /etc/modules)

What's the next step now? :-)

---

### Post by Favux on 2009-12-30
Hi ChadiM,

Welcome to Ubuntu forums!

OK, did you compile linuxwacom 0.5.8-8?  If so then you should just need a .fdi.  The rc2 .fdi is attached to the bottom of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") along with instructions in Section 2 b).

Hope this helps.

---

### Post by ChadiM on 2009-12-30
Hi,

I already compiled and installed the newest beta of linuxwacom and replaced the fdi with yours, but it still doesn't work.

---

### Post by Favux on 2009-12-30
Hi ChadiM,

OK, so you have the usb wacom.ko loading so there should be usb communication and you see it in dmesg.  I assume "xinput --list" and "xsetwacom list" don't show your tablet.

We'll have to look at your lshal and then maybe your Xorg.0.log.  For the lshal in a terminal:
```
lshal>ChadiM_lshal.txt
```
Right click on it and compress it with Create Archive.  Attach it to your next post with Manage Attachments.

---

### Post by ChadiM on 2009-12-31
I attached xinput --list and lshal and the Xorg.0.log.

xsetwacom list does not show anything.

---

### Post by Favux on 2009-12-31
Hi ChadiM,

The lshal looks OK, but the Xorg.0.log shows that the Synaptic Touchpad .fdi tries to grab your touchscreen but then drops it.  Then wacom tries to get it and also rejects it.  Which is why it doesn't show up in xinput.

Maybe the "fixes" since 0.8.5-4 for the E2 and other things have actually broken things?

Let's try to clear out one variable by fixing the Synaptic .fdi so it isn't so grabby.  See [post #22]("http://ubuntuforums.org/showpost.php?p=8372380&postcount=22").

Then if it isn't working the Xorg.0.log again.

---

### Post by ChadiM on 2009-12-31
It works!!!! Thank you very much :D

EDIT: .. but there are some tricks that were nice on windows 7 like scrolling by dragging white space in a page instead of using the scroll bar, because the laptop is multi-touch and does not include a stylus for precise selection and the scroll bar is  very small. But if it's not possible, that's ok, amazing job so far. Thank you again :)

---

### Post by Favux on 2009-12-31
Hi ChadiM,

Outstanding!  You're welcome.

---

### Post by ChadiM on 2010-01-04
Here are some points I would like to know more about:

[LIST]
[*]After suspending, touch fails. I must reboot again to work.
[*]linuxwacom-0.8.5-9 is available; should I upgrade?
[*]What about right clicking? In windows, right clicking is done by a long press.
[/LIST]

---

### Post by Favux on 2010-01-04
Hi ChadiM,

> After suspending, touch fails. I must reboot again to work.
The 0.8.5 series is suppose to support that:  "Support suspend/resume for kernel 2.6.26 and later." in the release notes.  So I don't know what to say.  Have you tried restarting X instead of rebooting?
> linuxwacom-0.8.5-9 is available; should I upgrade?
Not sure how much changed for your tablet.  But probably worth a try.  Maybe the kernel changes mentioned improved suspend/resume.
> What about right clicking? In windows, right clicking is done by a long press.
That, like the touch gestures, would be a feature request you would make at the LWP site.  Remember it's still early days for support for your multi-touch screen.

---

### Post by ChadiM on 2010-02-22
Hi Favux,

I upgraded to linuxwacom-0.8.5-10. Still have the suspend/hibernate problem. Is there a workaround? It is so annoying :/

Thank you.

---

### Post by Favux on 2010-02-22
Hi ChadiM,

You could try the work a round the TX2500's use.  They add "i8042.reset" (without the quotes of course) to the kernel boot line.  Instructions on this [thread]("http://ubuntuforums.org/showthread.php?t=1217745").

Touch is coming along.  Between Jason and Chris, provided it gets in, 0.8.5-11 should have some improvements for you.  Due out in two to three weeks.

---

### Post by ChadiM on 2010-02-22
Hello Favux,

This workaround did not work, unfortunately (yes, I did not forget to update-grub). But I can wait a few weeks, sure. :)

Thank you for the efforts.

---

### Post by Tameem on 2010-04-04
Favux, many thanks for your help and for fdi file in your other post,  [http://ubuntuforums.org/showpost.php?p=8367378&postcount=579](http://ubuntuforums.org/showpost.php?p=8367378&postcount=579).

I would like to share with you my feed back:
- Hardware: HP Pavilion tx2550ee
- OS: Linux Mint 8, running from 8G USB memory stick
- wacom input driver 0.8.4.1-Oubuntu4 was installed during Mint 8 installation on USB stick 
- Stylus worked fine out of the box, I didn't need to calibrate it
- Touch did not work at all
- I installed wacom-tools 0.8.4.1-Oubuntu4 and wacom control panel didn't show any device to select
- I replaced 10-linuxwacom.fdi with Favux new-generic rc2 10-linuxqacom.fdi, and it worked fine and when running wacom control panel I could see touch, stylus, pad and eraser
- After resuming from suspend touch and stylus are working normally, hibernate does not work, I think because Mint is running from USB stick

Now I need to figure out how to auto-rotate the display or at least activate rotate button like the way in Win7 instead of going through display menu to rotate.

Thanks

---

### Post by mcoleman44 on 2010-04-05
Do you still need help with auto rotation or did you figure it out?

---

### Post by Tameem on 2010-04-06
Sure I do, any help is appreciated

Currently, I can rotate the display through display preferences from control center but cursor of either mouse, touch and stylus does not rotate with the display

thanks

---

### Post by mcoleman44 on 2010-04-06
Do you use compiz?

---

### Post by mcoleman44 on 2010-04-06
Im going to pretend that you do seeing as you most likely are.
Here is a script to get you started. 

```
gksudo gedit /home/your username/Rotation

``````
rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal)
#   Compiz doesnt support rotation yet, 
#   so we have to turn it off before rotation
    metacity --replace &
    sleep 3s
#   (sleep 3 seconds) 
#   gives Compiz time to switch to  metacity
#    -rotate to the left 
    xrandr -o left 
    xsetwacom set stylus rotate CCW 
    xsetwacom set touch rotate CCW 
    xsetwacom set mttouch rotate CCW
#   Turns Compiz back on after rotate 
    compiz --replace &
    ;; 
    left) 
    metacity --replace &
    sleep 3s
#   (sleep 3 seconds) 
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set stylus rotate HALF 
    xsetwacom set touch rotate HALF 
    xsetwacom set mttouch rotate HALF
    compiz --replace & 
    ;; 
    inverted) 
    metacity --replace &
    sleep 3s
#    -rotate to the right 
    xrandr -o right 
    xsetwacom set stylus rotate  CW 
    xsetwacom set touch rotate CW 
    xsetwacom set mttouch rotate CW
    compiz --replace & 
    ;; 
    right) 
    metacity --replace &
    sleep 3
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set stylus rotate NONE 
    xsetwacom set touch rotate NONE 
    xsetwacom set mttouch rotate NONE 
    compiz --replace & 
    ;; 
esac



```
```
sudo chmod +x /home/your username/Rotation
```
Im assuming you are right handed so this script will rotate the orientation to the right and upside down.

Now you need to assign the Rotation file to a key of your choice.

---

### Post by Tameem on 2010-04-06
mcoleman44, thanks a lot

it worked like a charm. However, command: sudo chmod +x /home/my username/Rotation[FONT=monospace]
did not work and instead I used: [/FONT]./home/my username/Rotation

[FONT=monospace]then I assigned Rotation file to a key, now I can rotate my display to any orientation by one press of kay from my keyboard.

once again thanks.

[/FONT]

---

### Post by i_ReEm on 2010-05-23
Hi,
I upgraded to 10.04 and now the touch screen works here :)

---

### Post by ChadiM on 2010-05-23
> **i_ReEm said:**
> Hi,
I upgraded to 10.04 and now the touch screen works here :)

It does, but it lacks multi-touch features for my capacitive screen :/

Windows Seven is wayyy ahead in supporting touch screens in general; first thing I miss is kinetic scrolling! Which is much easier than using the scrollbar because touch isn't very easy on the borders. Hope you ubuntu guys can do something to beat them :)

I used to be able to scroll a page using multitouch on karmic with linuxwacom, now multitouch scrolling is not working on a stock lucid (I did a clean install of lucid).

---

### Post by Favux on 2010-05-23
Hi ChadiM,

There is a new gesture support patch that was submitted to xf86-input-wacom.  As soon as it is fixed up and committed you should be able to clone the git repostitory to get the functionality.

---

### Post by ChadiM on 2010-05-23
> **Favux said:**
> Hi ChadiM,

There is a new gesture support patch that was submitted to xf86-input-wacom.  As soon as it is fixed up and committed you should be able to clone the git repostitory to get the functionality.

Great! But I don't understand the "clone the git repostitory" part.

---

### Post by Favux on 2010-05-23
Read Lucid near the top of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") and then Appendix 5.  The patch is moving slower than I thought it would.  I figured it would be comitted by now.

---

