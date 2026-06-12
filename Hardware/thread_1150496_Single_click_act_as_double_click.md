---
title: "Single click act as double click"
date: 2009-05-06
forum: Hardware
---

### Post by didli on 2009-05-06
Hi everyone !
Since i upgraded from Intrepid to Jaunty, i got this annoying problem : my mouse's left-click act (quite often, but not all the time) as double-click. I checked everywhere i know but didn't find any clue to resolve this behavior (i found a similar problem in this forum, but it was a double entry problem for input device in xorg.conf, which is not my case).
So please what do you suggest ?
Is there anything i should try to understand and solve my mouse-gone-crazy problem ?
(something like a dpkg-reconfigure mouse ?)
Thanks in advance ;) 
I'm counting on you guys !

---

### Post by x33a on 2009-05-06
are you getting this problem with nautilus or in general?

because nautilus has an option to open files with a single click.

---

### Post by didli on 2009-05-06
General problem indeed. It could happen whenever or whatever i single-click. 
And it's getting quite annoying : tab unexpectedly closed in firefox (change the behavior to middle-click to close a tab), random maximized windows, words that can't be selected (double-click made me selecting entire sentence) etc etc etc

---

### Post by x33a on 2009-05-06
maybe its a problem with the mouse?

did you try the mouse somewhere else, or someone else's mouse on your pc?

---

### Post by didli on 2009-05-06
Yes i have tried this mouse on another PC (Win xp & Intrepid dualboot). Seems to work pefectly fine on both system. I didn't tried another mouse in the current PC as it is not really a mouse (a wacom tablet).

---

### Post by x33a on 2009-05-06
post your xorg.conf, maybe someone could help.

---

### Post by didli on 2009-05-06
Well, why not ?
Thing is, my xorg.conf is quite empty (ATI X800+Jaunty, so open source ati drivers) ... here it comes :
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```
Any suggestion ?

---

### Post by Favux on 2009-05-06
Hi didli,

Have you calibrated your tablet with "wacomcpl"?  Which tablet do you have?  Looking at the LWP HOW TO I see for stylus:
```
xsetwacom set Stylus button2 "dblclick 1"

```
And the same option is available in wacomcpl (which I installed in Preferences).  I don't know if it's available for a Wacom mouse (cursor) since I don't have one.

---

### Post by didli on 2009-05-06
Hi Favux !
There is a misunderstanding here : my current problem is **not** with a wacom tablet, but with the mouse I used since Hardy : [**i-rocks RF-7550A**]("http://www.i-rocksusa.com/products/RF-7550A.html"), a cordless optical mouse for notebooks. As i was asked to test another mouse in my current system, i talked about the wacom tablet, which is the only **another** available mouse i had right now, but the problem is not related to the tablet. Sorry for the misunderstanding.
So do you guys have an idea for a normal mouse gone crazy since Intrepid upgrade to Jaunty ? Where should I look ?

---

### Post by Favux on 2009-05-06
Hi didli,

Sorry, I should have read your posts more carefully.  If you can't configure it through mouse in Preferences, and there isn't anything in Synaptics to configure your mouse I guess you'll have to locate it's .fdi file and configure it through that.

Since it is cordless is it blue tooth?

---

### Post by didli on 2009-05-06
> **Favux said:**
> (...)I guess you'll have to locate it's .fdi file and configure it through that.
Since it is cordless is it blue tooth?
Hmm ... interesting, i don't know (yet) .fdi files but i'm gonna looking for it. 
i-rocks indicates "2.4GHz RF technology" : i guess it means it's radio technology (or something like that), the thing i'm pretty sure is that it's not bluetooth.
I will test and search for .fdi file right now.

---

### Post by Favux on 2009-05-06
Hi didli,

.fdi=device information file.  They started moving to them in Intrepid.

Usually in /usr/share/hal/fdi/.

---

### Post by didli on 2009-05-06
Ok, found it.
Did you see anything unusual ?
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.subsystem" string="usb_device">
      <match key="usb_device.vendor_id" int="0x046d"> <!-- Logitech, Inc. -->

        <!-- Receiver for MX1000 Laser -->
        <match key="usb_device.product_id" int="0xc50e">
          <merge key="info.product" type="string">MX1000 Laser Mouse</merge>
          <merge key="battery.type" type="string">mouse</merge>
          <merge key="battery.is_rechargeable" type="bool">true</merge>
	  <!-- proprietary properties defining the behavior -->
          <merge key="battery.csr.has_res" type="bool">false</merge>
          <merge key="battery.csr.has_sms" type="bool">false</merge>
          <merge key="battery.csr.is_dual" type="bool">false</merge>
        </match>

        <!-- Receiver for Cordless Click! -->
        <match key="usb_device.product_id" int="0xc510">
          <merge key="info.product" type="string">Cordless Click Mouse</merge>
          <merge key="battery.type" type="string">mouse</merge>
	  <!-- proprietary properties defining the behavior -->
          <merge key="battery.csr.has_res" type="bool">false</merge>
          <merge key="battery.csr.has_sms" type="bool">false</merge>
          <merge key="battery.csr.is_dual" type="bool">false</merge>
        </match>

	<!-- Receiver for Cordless Keyboard + Mouse combo -->
        <match key="usb_device.product_id" int_outof="0xc512;0xc505">
          <merge key="info.product" type="string">Cordless Keyboard+Mouse Receiver</merge>
          <merge key="battery.type" type="string">keyboard</merge>
	  <!-- proprietary properties defining the behavior -->
          <merge key="battery.csr.has_res" type="bool">false</merge>
          <merge key="battery.csr.has_sms" type="bool">false</merge>
          <merge key="battery.csr.is_dual" type="bool">false</merge>
        </match>

        <!-- Mouse Receiver -->
        <match key="usb_device.product_id" int="0xc501">
          <merge key="info.product" type="string">Mouse Receiver</merge>
          <merge key="battery.type" type="string">mouse</merge>
          <merge key="battery.is_rechargeable" type="bool">true</merge>
          <!-- proprietary properties defining the behavior -->
          <merge key="battery.csr.has_res" type="bool">false</merge>
          <merge key="battery.csr.has_sms" type="bool">false</merge>
          <merge key="battery.csr.is_dual" type="bool">false</merge>
        </match>

        <!-- Dual Receiver -->
        <match key="usb_device.product_id" int="0xc502">
          <merge key="info.product" type="string">Logitech Dual Receiver</merge>
          <merge key="battery.type" type="string">mouse</merge>
          <merge key="battery.is_rechargeable" type="bool">true</merge>
          <!-- proprietary properties defining the behavior -->
          <merge key="battery.csr.has_res" type="bool">false</merge>
          <merge key="battery.csr.has_sms" type="bool">false</merge>
          <merge key="battery.csr.is_dual" type="bool">true</merge>
        </match>

        <!-- Receiver for Cordless Freedom Optical -->
        <match key="usb_device.product_id" int="0xc504">
          <merge key="info.product" type="string">Cordless Freedom Optical Mouse</merge>
          <merge key="battery.type" type="string">mouse</merge>
          <merge key="battery.is_rechargeable" type="bool">true</merge>
          <!-- proprietary properties defining the behavior -->
          <merge key="battery.csr.has_res" type="bool">false</merge>
          <merge key="battery.csr.has_sms" type="bool">false</merge>
          <merge key="battery.csr.is_dual" type="bool">true</merge>
        </match>

        <!-- Receiver for MX700 Optical Mouse -->
        <match key="usb_device.product_id" int="0xc506">
          <merge key="info.product" type="string">MX700 Optical Mouse</merge>
          <merge key="battery.type" type="string">mouse</merge>
          <merge key="battery.is_rechargeable" type="bool">true</merge>
          <!-- proprietary properties defining the behavior -->
          <merge key="battery.csr.has_res" type="bool">false</merge>
          <merge key="battery.csr.has_sms" type="bool">true</merge>
          <merge key="battery.csr.is_dual" type="bool">false</merge>
        </match>

        <!-- Receiver for Cordless Optical TrackMan -->
        <match key="usb_device.product_id" int="0xc508">
          <merge key="info.product" type="string">Cordless Optical TrackMan</merge>
          <merge key="battery.type" type="string">mouse</merge>
          <merge key="battery.is_rechargeable" type="bool">true</merge>
          <!-- proprietary properties defining the behavior -->
          <merge key="battery.csr.has_res" type="bool">false</merge>
          <merge key="battery.csr.has_sms" type="bool">true</merge>
          <merge key="battery.csr.is_dual" type="bool">false</merge>
        </match>

        <!-- Receiver for Cordless Presenter -->
        <match key="usb_device.product_id" int="0xc702">
          <merge key="info.product" type="string">Cordless Presenter</merge>
          <merge key="battery.type" type="string">mouse</merge>
          <merge key="battery.is_rechargeable" type="bool">true</merge>
          <!-- proprietary properties defining the behavior -->
          <merge key="battery.csr.has_res" type="bool">false</merge>
          <merge key="battery.csr.has_sms" type="bool">false</merge>
          <merge key="battery.csr.is_dual" type="bool">false</merge>
        </match>

      </match>
    </match>
  </device>
</deviceinfo>

```
i don't really know what to do with it. Everything seems fine to me.
Is there any way to ensure my mouse is working correctly somewhere ? 
pfiouuu... how much I miss a magic command that will resolve this crazy stupid mouse behavior for this crazy stupid mouse.

---

### Post by Favux on 2009-05-06
Hi didli,

No, but then I don't know much about mouse .fdi's.  As you might have guessed I know a little about the wacom.fdi.  I don't see a header on a subsection with your mouses' name.  Do you?

To see how HAL sees your mouse:
```
lshal>lshal.txt
```
After it shows up on your desktop open up with text editor (gedit).  Big long output.  In there will be a least one section on your mouse.  You may be able to use search to make it easier.  Then compare that section to what you're seeing in the .fdi and see if there is a problem.

---

### Post by didli on 2009-05-06
Hmm ... Favux, i think you may have point to the right thing to do. I did lshal and i can see that :
```
udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  access_control.file = '/dev/input/event2'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.mouse', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input2/event2'  (string)
```
*"Macintosh mouse button emulation"* ? As far as i recall, mac mouse have only one button right ? Do you think this emulation has something to do with my problem ?

---

### Post by Favux on 2009-05-06
Maybe, but how sure are you that is your wireless mouse?  Shouldn't there be something that refers to wireless?  This may be your notebook mouse.  Do you have a synaptic pad or one of those eraser pointer things?

Notice in the mouse .fdi you showed that the .fdi file is for usb devices.  The first line picks up usb devices and the second uses a vendor id to focus on a specific device(s).  Think of it as crawling out on a tree until you have specified one branch (device).

The first line, udi, is unique device identifier.  So maybe there are other sections with the same or similar udi with the wireless stuff or this isn't it.

---

### Post by didli on 2009-05-06
No synaptic pad, as my current problem concerned my desktop PC.
Well i use a wireless notebook mouse with it, because i have small hands. This mouse has a small USB/Radio that connect it to the PC. I think it's kinda normal that it appears in USB devices, like this :
[disconnect & reconnect the mouse] then dmesg :
```
[11819.436995] usb 1-1.4: USB disconnect, address 8
[11820.676307] usb 1-1.4: new low speed USB device using ehci_hcd and address 9
[11820.782312] usb 1-1.4: configuration #1 chosen from 1 choice
[11820.843199] input:         USB Receiver as /devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1.4/1-1.4:1.0/input/input9
[11820.891975] generic-usb 0003:05AF:3062.0006: input,hiddev96,hidraw3: USB HID v1.10 Mouse [        USB Receiver] on usb-0000:00:02.2-1.4/input1
```

---

### Post by Favux on 2009-05-06
OK, that makes sense.  So then you want to find a vendor id like "0x046d" and see if a .fdi file uses it like the one you found.  If it is different you could try adding it to one of the mouse .fdi subsections.  Or if your mouse is handled by another .fdi see what's going on with that.  There should be a HAL section relating to the usb receiver for the mouse, correct?

---

### Post by didli on 2009-05-06
Correct, there is a hal section related to the usb receiver, like this :
**hal-device > /home/didli/Desktop/hal.txt :**
```
0: udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if0_logicaldev_input'
  info.capabilities = { 'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button' } (string list)
  info.callouts.add = { 'debian-setup-keyboard' } (string list)
  input.xkb.rules = 'evdev'  (string)
  input.device = '/dev/input/event5'  (string)
  input.product = '        USB Receiver'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1.4/1-1.4:1.0/input/input9/event5'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if0'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if0'  (string)
  info.subsystem = 'input'  (string)
  info.product = '        USB Receiver'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if0_logicaldev_input'  (string)
  info.addons.singleton = { 'hald-addon-input' } (string list)
  input.xkb.layout = 'fr'  (string)
  info.category = 'input'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.variant = 'oss'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  input.x11_driver = 'evdev'  (string)

1: udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if1_logicaldev_input'
  info.capabilities = { 'input', 'input.keys', 'input.mouse', 'button', 'access_control' } (string list)
  access_control.file = '/dev/input/event6'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = { 'debian-setup-keyboard', 'hal-acl-tool --add-device' } (string list)
  info.callouts.remove = { 'hal-acl-tool --remove-device' } (string list)
  input.xkb.rules = 'evdev'  (string)
  input.device = '/dev/input/event6'  (string)
  input.product = '        USB Receiver'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1.4/1-1.4:1.1/input/input10/event6'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if1'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if1'  (string)
  info.subsystem = 'input'  (string)
  info.product = '        USB Receiver'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if1_logicaldev_input'  (string)
  info.addons.singleton = { 'hald-addon-input' } (string list)
  input.xkb.layout = 'fr'  (string)
  info.category = 'input'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.variant = 'oss'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  input.x11_driver = 'evdev'  (string)

2: udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if1'
  usb.device_class = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.vendor_id = 1455  (0x5af)  (int)
  usb.product_id = 12386  (0x3062)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.device_revision_bcd = 1536  (0x600)  (int)
  usb.linux.device_number = 9  (0x9)  (int)
  usb.vendor = 'Jing-Mold Enterprise Co., Ltd'  (string)
  usb.num_ports = 0  (0x0)  (int)
  usb.version = 1.1  (double)
  usb.is_self_powered = false  (bool)
  usb.can_wake_up = true  (bool)
  info.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1.4/1-1.4:1.1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.speed = 1.5  (double)
  usb.interface.class = 3  (0x3)  (int)
  info.linux.driver = 'usbhid'  (string)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.interface.number = 1  (0x1)  (int)
  info.product = 'USB HID Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if1'  (string)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1.4/1-1.4:1.1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  linux.subsystem = 'usb'  (string)

3: udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if0'
  usb.device_class = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.vendor_id = 1455  (0x5af)  (int)
  usb.product_id = 12386  (0x3062)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.device_revision_bcd = 1536  (0x600)  (int)
  usb.linux.device_number = 9  (0x9)  (int)
  usb.vendor = 'Jing-Mold Enterprise Co., Ltd'  (string)
  usb.num_ports = 0  (0x0)  (int)
  usb.version = 1.1  (double)
  usb.is_self_powered = false  (bool)
  usb.can_wake_up = true  (bool)
  info.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1.4/1-1.4:1.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.speed = 1.5  (double)
  usb.interface.class = 3  (0x3)  (int)
  info.linux.driver = 'usbhid'  (string)
  usb.interface.protocol = 1  (0x1)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.interface.number = 0  (0x0)  (int)
  info.product = 'USB HID Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial_if0'  (string)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1.4/1-1.4:1.0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  linux.subsystem = 'usb'  (string)

4: udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial'
  linux.hotplug_type = 2  (0x2)  (int)
  linux.device_file = '/dev/bus/usb/001/009'  (string)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1.4'  (string)
  usb_device.num_configurations = 1  (0x1)  (int)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5af_3062_noserial'  (string)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.vendor_id = 1455  (0x5af)  (int)
  usb_device.product_id = 12386  (0x3062)  (int)
  info.subsystem = 'usb_device'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1.4'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5e3_608_noserial'  (string)
  info.linux.driver = 'usb'  (string)
  usb_device.product = 'USB Receiver'  (string)
  usb_device.device_revision_bcd = 1536  (0x600)  (int)
  usb_device.vendor = 'Jing-Mold Enterprise Co., Ltd'  (string)
  info.product = 'USB Receiver'  (string)
  usb_device.linux.device_number = 9  (0x9)  (int)
  usb_device.version = 1.1  (double)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.can_wake_up = true  (bool)
  info.vendor = 'Jing-Mold Enterprise Co., Ltd'  (string)
  usb_device.speed = 1.5  (double)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.is_self_powered = false  (bool)
  linux.subsystem = 'usb'  (string)
```
"0: udi" seems to be my keyboard, then "1: udi", "2:udi", "3: udi" and "4: udi" seem all related to my mouse.
I'm currently searching for the .fdi file that should configure my mouse ...
By the way Favux, thank you a lot for your kind help ;)

---

### Post by Favux on 2009-05-06
Hi didli,

Alright, looking at the HAL sections the mouse and usb receiver are perceived as a pair, with the manufacturer being Jing-Mold Enterprise Co., Ltd.  Does this sound right?  It's being seen as an HID (human interface device).  I'm guessing that means it's drivers are in the kernel.  And evdev is taking control of the mouse/receiver.  Have you checked mouse and keyboard in Preferences and made sure everything is configured the way you want?  Especially Double-click Timeout in mouse.  And that you don't accidentally have a mouse setting enabled in Preferences>Assistive Technologies?

---

### Post by baracuda68 on 2009-05-10
didi, I think this is what you want:
[http://ubuntuforums.org/showthread.php?t=1116446&highlight=single+click](http://ubuntuforums.org/showthread.php?t=1116446&highlight=single+click)

:)

---

### Post by didli on 2009-05-11
Not at all baracuda68, but thanks anyway.
@Favux : I give up. Might try to buy another mouse and test with it. But I want to thank you Favux for all you've done to help me. Thanks again ;)

---

