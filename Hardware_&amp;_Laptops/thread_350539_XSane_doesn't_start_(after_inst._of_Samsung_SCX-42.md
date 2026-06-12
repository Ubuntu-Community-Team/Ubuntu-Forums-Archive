---
title: "XSane doesn't start (after inst. of Samsung SCX-4216f)"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by Bernhard001 on 2007-01-31
Samsung SCX-4216f. After Installation I can use the "reconfigurator" (from Samsung) or Gimp for scanning images (but not via XSane-option)

XSane-problem:
As I tried to start XSane I got the message from XSane, whether i really want to start XSane as root. 
I uninstalled XSane and installed XSane a second time: XSane doesn't start!

Do you have a solution for this strange problem?

I use Ubuntu 6.10 Edgy Eft

Bernhard

---

### Post by tweedledee on 2007-01-31
I have some notes on how to deal with this problem in this thread:
[http://www.ubuntuforums.org/showthread.php?t=341621](http://www.ubuntuforums.org/showthread.php?t=341621).

---

### Post by Bernhard001 on 2007-02-01
Hi Tweedledee, 

thank you for your help. 

> **tweedledee said:**
> I have some notes on how to deal with this problem in this thread:
[http://www.ubuntuforums.org/showthread.php?t=341621](http://www.ubuntuforums.org/showthread.php?t=341621).
[COLOR="DarkOrange"][B]
O.K., let's see:[/B][/COLOR]

> **tweedledee said:**
> b: sudo edit /etc/sane.d/dll.conf, and comment out (add a "#") in front of the line that says "smfp" (probably the last line).
If you only do (a) and not (b), xsane will crash.

My samsung mfp (multi funct. printer) SCX-4216f needs smfp. Without smfp it doesn't work. It's very simple.

> Note that those with multifunction printers: xsane (and the smfp protocol Samsung adds) appears to be a problem. The above solution MIGHT work for you, I don't know.

It doesn't. May be we need more help. Some idea?

**Link [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian#Fix_for_the_MFP_port_issue:]("http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian#Fix_for_the_MFP_port_issue:"):** My driver-tarball-file from samsung is dated as the newest unified driver package for linux. And the fix file of jacobo belongs to an other package. Is there a difference between printing/scaning via usb port or via parallel port? I use lp:0. I guess the solution of jacobo isn't the right one for me.

**[http://www.elijahlofgren.com/ubuntu/#scx-4521f]("http://www.elijahlofgren.com/ubuntu/#scx-4521f"):**
What does the following code mean? ```
DeviceURI file:/dev/usblp0
``` What's about *usblp0*?
```
# Samsung|SCX-4100
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="3413", MODE="664", GROUP="scanner"
```
Mode "664" seems to be "simple user mode" with read property. But Do you know the meaning of "3413"? Is it important? How shall a newbie understand these lines? Has the scx-4216f an other id? Does "04e8" stay constant? 

I think the written instruction is for an expert like you, not for me. Perhaps the lines are written for an usb-printer. I havn't an usb-printer.

Tweedledee, you intended to help me. Thanks for the try. Nethertheless I'm finely confused now.

:idea: Some useful ideas? :idea:

Best regards from Germany
Bernhard

---

### Post by tweedledee on 2007-02-02
> **Bernhard001 said:**
> I think the written instruction is for an expert like you, not for me. Perhaps the lines are written for an usb-printer. I havn't an usb-printer.

Tweedledee, you intended to help me. Thanks for the try. Nethertheless I'm finely confused now.


Expert?  No, just already had to deal with some of these problems!  To address your udev issues, there is a guide that will explain far more than you probably need, but should help in the event my instructions don't: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html).

For the DeviceURI part, that's basically saying what port the printer is located on.  I think you'll be okay with the usblp0 as shown, but you may also need to try /dev/lp0 instead.  I can't test that, as all my printers are currently networked, so point to an IP address.

Basically, in the udev rule, idVendor is probably the same, but the idProduct will definitely be different.  You can determine the current value(s) as follows:
1. Determine the sysfs path.  On Gnome, the easiest way do to this is go to System -> Administration -> Device Manager and find your printer on the left-hand side.  Click to the Advanced tab on the right-hand side and you'll see a lot of stuff - you are looking for the linux.sysfs_path key.  You probably want the "deepest" tree entry under your printer on the right, but make a note of all the available sysfs paths.
EDIT: if you don't see your printer listed, you'll probably have to rely on Google to find those (or equivalent) values to use to identify your printer - you'll be looking for sysfs details.

2. Use the udevinfo command in a terminal with each path to try to find the correct values.  When you provide a path to udevinfo, you drop the initial "/sys" from each path.  An example for my mouse is below (the sysfs path is /sys/class/input/mouse0):
```
$ udevinfo -a -p /class/input/mouse0

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/class/input/input4/mouse0':
    KERNEL=="mouse0"
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:32"

  looking at device '/class/input/input4':
    ID=="input4"
    BUS=="input"
    DRIVER==""
    SYSFS{modalias}=="input:b0003v046DpC408e1400-e0,1,2,k110,111,112,113,114,r0,1,amlsfw"
    SYSFS{uniq}==""
    SYSFS{phys}=="usb-0000:00:1d.1-1/input0"
    SYSFS{name}=="Logitech USB Trackball"

  looking at device '/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0':
    ID=="2-1:1.0"
    BUS=="usb"
    DRIVER=="usbhid"
    SYSFS{modalias}=="usb:v046DpC408d1400dc00dsc00dp00ic03isc01ip02"
    SYSFS{bInterfaceProtocol}=="02"
    SYSFS{bInterfaceSubClass}=="01"
    SYSFS{bInterfaceClass}=="03"
    SYSFS{bNumEndpoints}=="01"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceNumber}=="00"

  looking at device '/devices/pci0000:00/0000:00:1d.1/usb2/2-1':
    ID=="2-1"
    BUS=="usb"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{product}=="USB Trackball"
    SYSFS{manufacturer}=="Logitech"
    SYSFS{maxchild}=="0"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="3"
    SYSFS{speed}=="1.5"
    SYSFS{bMaxPacketSize0}=="8"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bcdDevice}=="1400"
    SYSFS{idProduct}=="c408"
    SYSFS{idVendor}=="046d"
    SYSFS{bMaxPower}==" 50mA"
    SYSFS{bmAttributes}=="a0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.1/usb2':
    ID=="usb2"
    BUS=="usb"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.1"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="12"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.1':
    ID=="0000:00:1d.1"
    BUS=="pci"
    DRIVER=="uhci_hcd"
    SYSFS{modalias}=="pci:v00008086d00002484sv00001179sd00000001bc0Csc03i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="11"
    SYSFS{class}=="0x0c0300"
    SYSFS{subsystem_device}=="0x0001"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x2484"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""
```
As you can see, you get a variety of sets of information.  The key to udev is to pick a couple of items from a single block to use to identify the device.  In my case, the idVendor and idProduct  pieces of information happen to be useless, so I'd need to pick a couple of others instead.  Hopefully you'll just need to find the SYSFS{idProduct} tag and change the number, and then the solution from the page you are using as a guide will work.

I think the 644 for mode is probably okay.

Report back either way - if you are still stuck I will try to provide another solution.

---

### Post by Bernhard001 on 2007-02-03
Hello Tweedledee,

thank you for the explanation.

I will follow your instructions...

when i will have finished the next try i will drop some lines here.

Best regards
Bernhard

---

### Post by Bernhard001 on 2007-02-06
Hi Tweedledee,

i'm so sorry, the code "_udevinfo /dev/lp0_" leads to nothing. I don't know how to get the informaton about the value of  SYSFS{idproduct}.

Look, what I found in ***smfp.conf*** (directory /etc/sane.d/):

"[B][COLOR="DarkRed"]<model vendor="samsung" id="scx4x16" modelstring="SCX-4x16 Series">
		<hwoption name="twainspec" type="enum">1</hwoption>
		<hwoption name="sleep_after_scan_ms" type="int">0</hwoption>
		<hwoption name="adf" type="enum">simplex</hwoption>
		<hwoption name="flatbed" type="enum">yes</hwoption>
		<hwoption name="resolution" type="list" default="300">75 150 300 600</hwoption>
		<hwoption name="colorcompose" type="list" default="color24bit">color24bit gray256 bw_halftone bw_lineart</hwoption>
		<hwoption name="pageformat" type="list" default="a4">
			a4 letter legal statement folio
			a5 a5_extra b5 b5_extra b5_jis
			executive quatro letter_plus a4_plus
			envelope_9 envelope_10 envelope_11 envelope_12
			envelope_14 envelope_b5 envelope_b6 envelope_c5
			envelope_c6 envelope_c6c5 envelope_dl
			envelope_110x230 envelope_monarch
			custom
		</hwoption>
	</model>[/COLOR][/B]"

Is it possible to make the scx-4216f - as scanner (lp0 !) - visible for all users (readable for XSane). XSane-rights readable for all users?

Is there a chance to make a udevrule using the information above? Symlink for the XSane-program? If yes, what could the correct code be?

The file "**_45-libsane.rules_**" is for usb-Devices, isn't it? Which file have i to change/make instead?

Best regards 
Bernhard

---

### Post by tweedledee on 2007-02-06
Okay, after a little more digging around, I think I've come to a more complete understanding of what Samsung has done.  If your scanner no longer works once you comment out smftp from /etc/sane.d/dll.conf, then you are stuck.  It appears there is no other interface that will work with a parallel port (with usb you have other options, many of which you seem to have found and tried).  Something about the way their driver communicates with the device over a parallel port is poorly executed and requires root access.  I believe the answer to your initial question is "no, there is no solution."  It is not really a hardware or xsane issue - it's strictly an issue with the way Samsung compiled their driver and the way it seeks to communicate with a parallel port.

All this of course assumes that (as I think you indicated) that you can at least scan as root.  If you can't scan at all, that problem at least should be addressable.

For your general understanding, since I've spent a lot of time in the last month in the udev & related systems and dealing with my own Samsung issues:
1. The udev rules are good only for directing where and how devices are mounted; they are not useful for actually DOING anything directly with the device.  I wasted a lot of time on that before I really understood the limitations.  Sometimes playing with udev rules is essential, sometimes it is entirely the wrong solution.  For you, I now think the latter.
2. Most of the files in /etc (many exceptions, though) are just configuration settings.  the smfp.conf is an example - changes there would allow you to tune how your scanner worked, but not regulate whether or not it will work.  For the most part, they also seem to not to regulate hardware issues.
3. From lots of experience, despite the warning xsane gives, it is not really a problem to run xsane as root.  It is annoying, in that all files you scan will be owned by root, but you can fix that by running "gksudo nautilus" and changing ownership in the gui, or using a terminal and "sudo chown user.user *" in the directory with the files you just scanned, where "user" is your user name.  Actually, if you always scan to the same target directory, you could even automate that with a script to change the ownership after you quit xsane - if that solution interests you, I could post a quick example.
4. If you still have the problem with your re-installed xsane crashing and would like it to work again (at least as root), you'll need to run "sudo chmod u+s /usr/bin/xsane" in a terminal.

Sorry I can't provide a real solution.

---

