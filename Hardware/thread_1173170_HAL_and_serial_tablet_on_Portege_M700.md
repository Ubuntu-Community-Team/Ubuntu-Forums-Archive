---
title: "HAL and serial tablet on Portege M700"
date: 2009-05-29
forum: Hardware
---

### Post by TabletUbuntu on 2009-05-29
Hello All,

I have a Toshiba Portege M700 tablet that has worked fine since Hardy.  Upgrade to Jaunty lost all tablet support.  

Using the xorg.conf from Intrepid gets all devices to work, but they stop working soon after first use (i.e. writing in Xournal works for about 5 minutes, then the stylus stops responding at all).  So I went back to the default xorg.conf.  A fresh install also fails to solve the problem.

I know that in Jaunty the wacom tablet is now configured automatically by HAL.  I've found a few related threads here and elsewhere, the closest being [http://ubuntuforums.org/showthread.php?t=1144407]("http://ubuntuforums.org/showthread.php?t=1144407").  

wacdump /dev/ttyS0 does show some output so I believe the serial port is configured okay.  The wacom.o module is loaded when listed in /etc/modules.  xinput --list does not show any wacom related devices, but lshal does show 

info.product = 'PnP Device (WACf009)'

which I think is a wacom device.  I have included my xorg.conf, the output of lshal and xinput --list.

If anyone has gotten this to work on a Portege M700 or M750, please let me know.

Any help would be appreciated.

Thanks.

---

### Post by Favux on 2009-05-29
Hi TabletUbuntu,

Your right that HAL is seeing your tablet as 'PnP Device (WACf009)'.  Since the serial subsection of the 10-wacom.fdi doesn't quite work right xinput should be showing you:
'PnP Device (WACf009)' = stylus
'PnP Device (WACf009) eraser' = eraser
'PnP Device (WACf009) touch' = touch

I put the "= stylus" etc. to show you what linuxwacom needs to see.  Which would mean "xsetwacom list" would be blank and "wacomcpl" wouldn't work.  So you could either rename your .xinitrc or use rec's script to translate the names.

But "xinput" isn't showing any output from the tablet so something else is going on.  X-Kent got his M750 working using the xorg.conf, starting about page 7 here:  [http://ubuntuforums.org/showthread.php?t=1055845](http://ubuntuforums.org/showthread.php?t=1055845)  And we got the information that the setserial line from the M700 tutorial worked from arestivo here:  [http://ubuntuforums.org/showthread.php?t=1009359](http://ubuntuforums.org/showthread.php?t=1009359)

Good luck!

---

### Post by TabletUbuntu on 2009-06-04
Thanks.  As I understand that post, they got the tablet working by using the xorg.conf method, which is what I had.  Based on your comment, however, I decided to remove 10-wacom.fdi and see if that's what was causing the stylus to stop working.  It seems to be stable now (not locking up the stylus).  The only problem I notice is random lines occasionally appearing while writing in Xournal.

As an aside, while I am a big supporter of Ubuntu, I find it annoying that with each update things that previously worked well break.  I am happy with the overall progress being made, but things that worked well should not break.

---

### Post by Favux on 2009-06-04
Hi TabletUbuntu,

Good deal.  As I understand you, you kept your xorg.conf with its wacom entries and removed the 10-wacom.fdi and stylus etc. started working again.

The lines in Xournal may be from the new Xserver 1.6.  Also it seemed there was a bug in xserver-xorg that made the xorg.conf flaky, especially with "ServerLayout" wacom entries.  They may have fixed that.

I agree that no regressions would be nice.  But I don't think this is really a regression.  It has that effect on us users though.  The whole HAL/.fdi thing is to get hot plugging.  Which sort of puts them at the mercy of the upstream HAL folks, the Xorg folks' Xserver, and linuxwacom.  All those have to be coordinated.  It seems that they've been trying with the Wacom, but just not quite getting there.  They're already introducing a new .fdi for Kharmic and linuxwacom 0.8.3-2.  Although there isn't yet any change in the serial subsection of the new .fdi.

---

### Post by TabletUbuntu on 2009-06-15
Favux- Thanks for the update.

---

### Post by R3N3GAD3 on 2009-10-09
Same old story. Toshiba Tablet with ubuntu 9.04.

But I refuse to give up hotplugging. There is no way I will succumb to editing my xorg.conf file. The file is now 10 lines thanks to hal, and that is the way the file is going to stay. I speant a full day on this, and now I am in pure agony. It is almost 3am, and I have lost all brain processing power.

I have a brand new toshiba protege tablet M750, since the hinge on my macbook air decided to break and fray the video cable. Instead of paying $800 for a new lcd display (since it was exactly one year after I purchased it), I decided to get some real hardware and settled on the M750.

In theory, this should work.

Obviously, the problem is that the driver does not get attached to the hardware durring boot. But that's the simple explanation.

First attempt: 
- load the wacom driver at startup (add "wacom" to the end of /etc/modules)
- add the following lines to /etc/udev/rules.d/10-wacom.rules

DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="00", ENV{WACOM_TYPE}="stylus"
DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="01", ENV{WACOM_TYPE}="touch"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0009", SYMLINK+="input/wacom-touch"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0009", ENV{WACOM_TYPE}!="touch", SYMLINK+="input/wacom"

# Other attempts
#ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0009", SYMLINK+="input/wacom"
#ATTRS{idVendor}=="056a", ATTRS{idProduct}=="WACf009", SYMLINK+="input/wacom"
#ATTRS{idVendor}=="056a", SYMLINK+="input/wacom-$env{WACOM_TYPE}"
# legacy
#ATTRS{idVendor}=="056a", ENV{WACOM_TYPE}!="touch", SYMLINK+="input/wacom"
#ATTRS{idVendor}=="056a", ENV{WACOM_TYPE}=="touch", SYMLINK+="input/wacom-touch"
#ATTRS{idVendor}=="056a", ACTION=="add", RUN+="check_driver wacom $devpath $env{ID_BUS}"


$ dmesg | grep [Ww]acom
[    5.744585] usbcore: registered new interface driver wacom
[    5.744588] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver


I get an invalid argument for wacdump any /dev/ttyS# serial device

$ wacdump ttyS0
WacomOpenTablet: Invalid argument

I did wacdump on everything in /dev/input and everything worked, but nothing gave any events on tablet input 


$ grep -i name /proc/bus/input/devices
N: Name="Power Button (FF)"
N: Name="Lid Switch"
N: Name="Power Button (CM)"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="Toshiba RFKill Switch"
N: Name="CNA7157"
N: Name="PC Speaker"
N: Name="PS/2 Mouse"
N: Name="AlpsPS/2 ALPS GlidePoint"


lshal shows that the hardware is present:

udi = '/org/freedesktop/Hal/devices/pnp_WACf009'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (WACf009)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf009'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'  (string)
  pnp.id = 'WACf009'  (string)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x338'  (string)


I tried to set the serial device:

$ setserial /dev/ttyS0 port 0x338 irq 4 autoconfig

$ sudo /etc/init.d/setserial reload

but then wacdump did not like it:
$ wacdump ttyS0
02:58:58.555 WARN: Discarding C2
02:58:58.556 WARN: Discarding BE
02:58:58.556 WARN: Discarding D2
02:58:58.556 WARN: Discarding 1E
02:58:58.556 WARN: Discarding FE
02:58:58.556 WARN: Discarding 08
02:58:58.556 WARN: Discarding FE
02:58:58.063 WARN: Discarding C2
02:58:58.064 WARN: Discarding 3F
02:58:58.071 WARN: Discarding D2
02:58:58.071 WARN: Discarding C2
02:58:58.071 WARN: Discarding 5F
02:58:58.071 WARN: Discarding 0E
WacomOpenTablet: Connection timed out


I used udevadm to parse the device tree and found nothing:
$ udevadm info -a -p /sys/class/input/event...
$ udevadm info -a -p /sys/class/tty/ttyS...

Examples:

$ udevadm info -a -p /sys/class/tty/ttyS0

...

  looking at device '/devices/platform/serial8250/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/platform/serial8250':
    KERNELS=="serial8250"
    SUBSYSTEMS=="platform"
    DRIVERS=="serial8250"
    ATTRS{modalias}=="platform:serial8250"

  looking at parent device '/devices/platform':
    KERNELS=="platform"
    SUBSYSTEMS==""
    DRIVERS==""

$ udevadm info -a -p /sys/class/input/event6

...

  looking at device '/devices/virtual/input/input6/event6':
    KERNEL=="event6"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/virtual/input/input6':
    KERNELS=="input6"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="Toshiba RFKill Switch"
    ATTRS{phys}==""
    ATTRS{uniq}==""
    ATTRS{modalias}=="input:b0019v0930p0000e0000-e0,5,kramlsfw3,"


The right device name "WACf009" is present in /etc/hal/fdi/policy/10-wacom.fdi

<match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02
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
     </match>
</match>


$ xinput --list | grep \"*\"
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
"Video Bus"	id=3	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
"PS/2 Mouse"	id=5	[XExtensionPointer]
"AlpsPS/2 ALPS GlidePoint"	id=6	[XExtensionPointer]


$ xsetwacom --list 
does not list any results

$ wacomcpl 
does not list any wacom devices to select in the gui

$ dmesg | grep ttyS
does not list anything


I also recompiled linux-wacom:

./confire --enable-wacom
make
sudo make install
sudo cp ./src/2.6.28/wacom.ko /lib/modules/2.6.28-15-generic/kernel/drivers/input/tablet/.

It did not fix the problem.


Things to note:
The wacom driver is configured as a usb driver, but there is no seperate driver for integrated hardware. I noticed my internal webcam also uses a usb driver, so I assume this *should* not cause any problems, even though the tablet input is serial.

After adding the rules to the 10-wacom.rules file, after a reboot /dev/input/uinput appeared, but does not work with wacdump. I am about 99 percent sure it was not there when I started with these shenanigans. 

The ONLY thing I have left in my arsenal is to reconfigure the kernel. But I am right in the middle of some application development on my laptop, and it would kill me if my kernel went down for a few days. It has been years since I have had to reconfigure my kernel. Even though it is a simple task with make menuconfig. I have never had to do it before with ubuntu (only redhat and gentoo). And even if I do reconfigure my kernel, the only thing I can do is switch the wacom driver to be built into the base instead of a module.

I really do not want to take that last resort. Please save me someone.

---

### Post by Favux on 2009-10-09
Hi R3N3GAD3,

Wow!  I feel your pain.

First with the default Jaunty 0.8.2-2 linuxwacom packages wacom-tools & xserver-xorg-input-wacom udev rules is installed.  I think it's 40-wacom.rules, but in a new location, "/lib/udev/rules.d/".  I'm pretty sure your tablet is in there.  Getting the Wacom symlinks into Jaunty for a compiled linuxwacom is described in Appendix 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Second wacom.ko is the usb driver and is irrelevant to you.  Your Wacom digitizer has an internal serial connection.

What I would wonder is from a stock Jaunty install, making sure both linuxwacom packages are installed in Synaptic, and with setserial and the serial line installed does:
```
xinput --list
```
show your wacom devices?

In other words if you did what Fc1032 describes in post #91 here:  [http://ubuntuforums.org/showthread.php?t=1055845&highlight=m750&page=10](http://ubuntuforums.org/showthread.php?t=1055845&highlight=m750&page=10)  up to step 5), the xorg.conf, can we see your devices with the default 10-wacom.fdi?  You should have function at that point, the serial subsection has touch unlike the usb.  Then to setup and calibrate with wacomcpl you could translate the HAL/dBus output with rec's script.

Just some thoughts.

---

### Post by R3N3GAD3 on 2009-10-09
Thanks for the quick response Favux! I really appreciate the help.

I found /lib/udev/rules.d/40-xserver-xorg-input-wacom.rules
The one thing I noted was that this file is not setup to handle WACf009
I made the appropriate changes to the file, but it did not fix anything.

If there is a 10-wacom.rules file in /etc/udev/rules.d, and /lib/udev/rukes.d, which one gets precedence? I would assume the file in /etc/udev/rules.d, but I gather this is not the case.

There was no wacom-tools.rules file

So I took your advice, but instead of doing a fresh install (since I do not want to loose my development environment), I popped in the ubuntu 9.04 livecd, booted into a fresh OS, and installed setserial, and wacom-tools (xserver-xorg-wacom was already installed). I then did a setserial /dev/ttyS0 port 0x338 irq 4 autoconfig, but I got the same output from both wacdump /dev/ttyS0 and xinput --list.

So by rec's script, I assume you mean the following:

for udi in `hal-find-by-property --key input.x11_driver --string wacom`; do
    product="`hal-get-property --udi $udi --key info.product`"
    type="`hal-get-property --udi $udi --key input.x11_options.Type`"
    echo "product '$product' is type '$type'"
done

This would not do anything for me, since the hardware is not configured properly. There is no driver property, nor is there a type property. Is there something I am missing?

When I started troubleshooting this problem, I took the approach of doing as least as possible, since from reading through the thousands of posts, it seemed that the only people to get tablet input working with hotplugging seemed to have it work out of the box, or have recompiled linux-wacom.

The last thing I did was try and update the wacom drivers with the newest version of linux-wacom (0.8.4-3), when everything else failed. I also tried to purge everything, and install/configure everything again.

The reason I do not want to use xorg.conf is because it seems touch input can not be configured with it. Is this true? Or is it just that case that it can only be set up with either touch or stylus input, but not both? Touch input is definitely going to replace the trackpads eventually. I absolutely love using the touch interface as my mouse input. I desperately want it working in my ubuntu distro..

I really think the problem is that the out of the box setup does not handle the WACf009 hardware. I imagine the people who have their tablet pc working in ubuntu with hoplugging and both touch and stylus input are using the WACf008 hardware. I have made the appropriate changes to support WACf009, but no matter what I do, nothing seems to work, though I will never give up!

---

### Post by Favux on 2009-10-09
Hi R3N3GAD3,

Touch is configured with xorg.conf.

With the .rules /lib/udev/rules.d is executed first followed by /etc/udev/rules.d.  They want you to put custom rules in /etc/udev/rules.d but you're right.  I think you should be modifying 40-xserver-xorg-input-wacom.rules in /lib/udev/rules.d.

I thought WACf009 was in there.  I don't understand why a symlink patterned on the thinkpad serial wacom with touch (WACf008, rec's tablet) isn't working for you.

I'm hoping the problem, why it isn't configured, is that the serial line isn't installed in the "standard" manner and you missed that.  See X-Kent's post #78 and my post #79 here:  [http://ubuntuforums.org/showthread.php?t=1055845&highlight=m750&page=8](http://ubuntuforums.org/showthread.php?t=1055845&highlight=m750&page=8)  And the wiki we're getting that from:  [https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700)

Since it isn't in the wacom.rules maybe it also isn't in the Vendor and Product ID table in wcmUSB.c?  But then the xorg.conf method shouldn't work, I'd think.

You'd only need rec's script once the device is configured.

---

### Post by R3N3GAD3 on 2009-10-10
Thanks again Favux!

I definitely do not want to sacrifice hotplugging.

I already have the setserial command in my /etc/rc.local file:
/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig

It seems X-Kent sacrificed hotplugging as well with his M750 by using xorg.conf for configuration. But it is good to know everything works for the M750.

I completely agree with your last point. Why should it work for xorg.conf, but not for a .fdi file? It just does not make sense.

There are these tablet pc entries in the table for the default jaunty 1:0.8.2.2 wcmUSB.c

{ 0x90, 2540, 2540, &usbTabletPC   }, /* TabletPC 0x90 */ 
{ 0x93, 2540, 2540, &usbTabletPC   }, /* TabletPC 0x93 */
{ 0x9A, 2540, 2540, &usbTabletPC   }  /* TabletPC 0x9A */

I am not sure how these vales (140, 144, 154) map to the appropriate hardware. I can look deeper into the code, but I feel that there is something missing with my configuration somehow. I would love to know if someone else has successfully configured the M750 with jaunty without sacrificing hotplugging. 

Any more thoughts or ideas?

---

### Post by R3N3GAD3 on 2009-10-10
I found these in wacom_wac.c

{ "Wacom ISDv4 90",           8, 26202, 16325,  255,  0, TABLETPC },
{ "Wacom ISDv4 93",           8, 26202, 16325,  255,  0, TABLETPC },
{ "Wacom ISDv4 9A",           8, 26202, 16325,  255,  0, TABLETPC },

```
static struct wacom_features wacom_features[] = {
	{ "Wacom Penpartner",        7,   5040,  3780,  255,  0, PENPARTNER },
        { "Wacom Graphire",          8,  10206,  7422,  511, 63, GRAPHIRE },
	{ "Wacom Graphire2 4x5",     8,  10206,  7422,  511, 63, GRAPHIRE },
	{ "Wacom Graphire2 5x7",     8,  13918, 10206,  511, 63, GRAPHIRE },
	{ "Wacom Graphire3",         8,  10208,  7424,  511, 63, GRAPHIRE },
	{ "Wacom Graphire3 6x8",     8,  16704, 12064,  511, 63, GRAPHIRE },
	{ "Wacom Graphire4 4x5",     8,  10208,  7424,  511, 63, WACOM_G4 },
	{ "Wacom Graphire4 6x8",     8,  16704, 12064,  511, 63, WACOM_G4 },
	{ "Wacom BambooFun 4x5",     9,  14760,  9225,  511, 63, WACOM_MO },
	{ "Wacom BambooFun 6x8",     9,  21648, 13530,  511, 63, WACOM_MO },
	{ "Wacom Bamboo1 Medium",    8,  16704, 12064,  511, 63, GRAPHIRE },
	{ "Wacom Volito",            8,   5104,  3712,  511, 63, GRAPHIRE },
	{ "Wacom PenStation2",       8,   3250,  2320,  255, 63, GRAPHIRE },
	{ "Wacom Volito2 4x5",       8,   5104,  3712,  511, 63, GRAPHIRE },
	{ "Wacom Volito2 2x3",       8,   3248,  2320,  511, 63, GRAPHIRE },
	{ "Wacom PenPartner2",       8,   3250,  2320,  511, 63, GRAPHIRE },
	{ "Wacom Bamboo",            9,  14760,  9225,  511, 63, WACOM_MO },
	{ "Wacom Bamboo1",           8,   5104,  3712,  511, 63, GRAPHIRE },
	{ "Wacom Intuos 4x5",       10,  12700, 10600, 1023, 31, INTUOS },
	{ "Wacom Intuos 6x8",       10,  20320, 16240, 1023, 31, INTUOS },
	{ "Wacom Intuos 9x12",      10,  30480, 24060, 1023, 31, INTUOS },
	{ "Wacom Intuos 12x12",     10,  30480, 31680, 1023, 31, INTUOS },
	{ "Wacom Intuos 12x18",     10,  45720, 31680, 1023, 31, INTUOS },
	{ "Wacom PL400",             8,   5408,  4056,  255,  0, PL },
	{ "Wacom PL500",             8,   6144,  4608,  255,  0, PL },
	{ "Wacom PL600",             8,   6126,  4604,  255,  0, PL },
	{ "Wacom PL600SX",           8,   6260,  5016,  255,  0, PL },
	{ "Wacom PL550",             8,   6144,  4608,  511,  0, PL },
	{ "Wacom PL800",             8,   7220,  5780,  511,  0, PL },
	{ "Wacom PL700",             8,   6758,  5406,  511,  0, PL },
	{ "Wacom PL510",             8,   6282,  4762,  511,  0, PL },
	{ "Wacom DTU710",            8,  34080, 27660,  511,  0, PL },
	{ "Wacom DTF521",            8,   6282,  4762,  511,  0, PL },
	{ "Wacom DTF720",            8,   6858,  5506,  511,  0, PL },
	{ "Wacom DTF720a",           8,   6858,  5506,  511,  0, PL },
	{ "Wacom Cintiq Partner",    8,  20480, 15360,  511,  0, PTU },
	{ "Wacom Intuos2 4x5",       10, 12700, 10600, 1023, 31, INTUOS },
	{ "Wacom Intuos2 6x8",       10, 20320, 16240, 1023, 31, INTUOS },
	{ "Wacom Intuos2 9x12",      10, 30480, 24060, 1023, 31, INTUOS },
	{ "Wacom Intuos2 12x12",     10, 30480, 31680, 1023, 31, INTUOS },
	{ "Wacom Intuos2 12x18",     10, 45720, 31680, 1023, 31, INTUOS },
	{ "Wacom Intuos3 4x5",       10, 25400, 20320, 1023, 63, INTUOS3S },
	{ "Wacom Intuos3 6x8",       10, 40640, 30480, 1023, 63, INTUOS3 },
	{ "Wacom Intuos3 9x12",      10, 60960, 45720, 1023, 63, INTUOS3 },
	{ "Wacom Intuos3 12x12",     10, 60960, 60960, 1023, 63, INTUOS3L },
	{ "Wacom Intuos3 12x19",     10, 97536, 60960, 1023, 63, INTUOS3L },
	{ "Wacom Intuos3 6x11",      10, 54204, 31750, 1023, 63, INTUOS3 },
	{ "Wacom Intuos3 4x6",       10, 31496, 19685, 1023, 63, INTUOS3S },
	{ "Wacom Intuos4 4x6",       10, 31496, 19685, 2047, 63, INTUOS4S },
	{ "Wacom Intuos4 6x9",       10, 44704, 27940, 2047, 63, INTUOS4 },
	{ "Wacom Intuos4 8x13",      10, 65024, 40640, 2047, 63, INTUOS4L },
	{ "Wacom Intuos4 12x19",     10, 97536, 60960, 2047, 63, INTUOS4L },
	{ "Wacom Cintiq 21UX",       10, 87200, 65600, 1023, 63, CINTIQ },
	{ "Wacom Cintiq 20WSX",      10, 86680, 54180, 1023, 63, WACOM_BEE },
	{ "Wacom Cintiq 12WX",       10, 53020, 33440, 1023, 63, WACOM_BEE },
	{ "Wacom DTU1931",            8, 37832, 30305,  511,  0, PL },
	{ "Wacom Graphire Bluetooth", 8, 10208,  7424,  511, 63, WACOM_GB },
	{ "Wacom ISDv4 90",           8, 26202, 16325,  255,  0, TABLETPC },
	{ "Wacom ISDv4 93",           8, 26202, 16325,  255,  0, TABLETPC },
	{ "Wacom ISDv4 9A",           8, 26202, 16325,  255,  0, TABLETPC },
	{ "Wacom Intuos2 6x8",       10, 20320, 16240, 1023, 31, INTUOS },
	{ }
};

```

```
static struct usb_device_id wacom_ids[] = {
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x00) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x10) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x11) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x12) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x13) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x14) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x15) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x16) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x17) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x18) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x19) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x60) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x61) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x62) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x63) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x64) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x65) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x69) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x20) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x21) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x22) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x23) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x24) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x30) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x31) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x32) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x33) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x34) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x35) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x37) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x38) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x39) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xC4) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xC0) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xC2) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x03) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x41) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x42) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x43) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x44) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x45) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xB0) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xB1) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xB2) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xB3) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xB4) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xB5) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xB7) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xB8) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xB9) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xBA) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xBB) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x3F) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xC5) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xC6) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0xC7) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x81) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x90) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x93) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x9A) },
	{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x47) },
	{ }
};
```

I will keep searching deeper to unravel this mystery.

---

### Post by Favux on 2009-10-10
Hi R3N3GAD3,

First I want to thank you.  I'm learning new things.

My 'lshal' shows:
```
usb_device.product = 'ISD-V4'  (string)
  usb_device.product_id = 147  (0x93)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
```
So:
USB_DEVICE(USB_VENDOR_ID_WACOM, 0x93) = HP TX2000
and I'm pretty sure:
USB_DEVICE(USB_VENDOR_ID_WACOM, 0x9A) = HP TX2500

What's your lshal showing your product id as?

Another thought is that it may have to do with an upstream .fdi.  For example in the 10-tabletPCs.fdi in "/usr/share/hal/fdi/policy/10osvendor/" some serial tablet pc's have their serial lines preconfigured.  Hopefully I'm not sending you up a blind alley.

My impression is that some of these serial tablet pc's work "out of the box" with no need to set a serial line etc.  Could this make a difference?  Or do you need a brand specific "quirk" added in a .fdi further upstream?  To kind of see what I'm talking about:  [http://hal.freedesktop.org/quirk/](http://hal.freedesktop.org/quirk/)

---

### Post by X-Kent on 2009-10-11
Hello people. Nice to see more people using ubuntu+m750.

I didn't try the .fdi method as the xorg.conf method gave me everything I wish.
Hotpluging ? Not sure what that mean in the touch/pen context as the "screen" is always plugged so I don't really understand this part.

Anyway, good luck !

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

