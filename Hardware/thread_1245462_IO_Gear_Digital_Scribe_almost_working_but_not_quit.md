---
title: "IO Gear Digital Scribe almost working but not quite"
date: 2009-08-20
forum: Hardware
---

### Post by Tesla_Cubed on 2009-08-20
Hi Everyone 

I have a Digital Scribe pen model #GPEN100C I am trying to get to work on my hp notebook. The note book is a hp-dv6700 [3G amd64x2 4gb ram Ninvida chip set and GPU Athros WiFi(other thing I am trying to get to work reliably)] it daul boots 9.04 jaunty and win vistaHP. The pen is the only reason vista is even still on the book. When i saw some people had mad hedway with wizardpen in geting it to work with linux well ... :P ... sums it up. 

Heres what I have so far. 
Downloaded wizard pen source 0.7.somthing alpha 2 and built it installed it 
Set up the 99-x11-wizardpen.fdi in /etc/hal/fdi/policy
Restarted hal 
Pluged in my pen 
got nothing but a new error in the x11 log

```
(WW) config/hal: no driver or path specified for /org/freedesktop/Hal/devices/usb_device_e20_100_noserial 
```spent the rest of the morning playing with it trying to get beyond this point.
tryed the pre-built drivers from launchpad

same X error on pluging in of the pen 

Here is its relavant information.
my 99-x11-wizardpen.fdi
```

<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<!-- This MUST match with the name of your tablet -->
<match key="info.product" contains="NoteTaker FW Ver 2.05">
<merge key="input.x11_driver" type="string">wizardpen</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
<merge key="input.x11_options.TopX" type="string">5619</merge>
<merge key="input.x11_options.TopY" type="string">6554</merge>
<merge key="input.x11_options.BottomX" type="string">29405</merge>
<merge key="input.x11_options.BottomY" type="string">29671</merge>
<merge key="input.x11_options.MaxX" type="string">29405</merge>
<merge key="input.x11_options.MaxY" type="string">29671</merge>
</match>
</device>
</deviceinfo>

```
the pens part of my lsusb -v output
```

Bus 002 Device 020: ID 0e20:0100  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0e20 
  idProduct          0x0100 
  bcdDevice            2.05
  iManufacturer           3 
  iProduct                1 
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
    MaxPower              100mA
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
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      40
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              20
```lsusb output```

david@HP-dv6000:~$ lsusb
Bus 002 Device 020: ID 0e20:0100  
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd 

```
grep -i name /proc/bus/input/devices output
```

david@HP-dv6000:~$ grep -i name /proc/bus/input/devices
N: Name="Power Button (FF)"
N: Name="Lid Switch"
N: Name="Power Button (CM)"
N: Name="Sleep Button (CM)"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="PC Speaker"
N: Name="HP Webcam"
N: Name="SynPS/2 Synaptics TouchPad"

```
and finaly the relevent chunck of lshal output
```

udi = '/org/freedesktop/Hal/devices/usb_device_e20_100_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0'  (string)
  info.product = 'NoteTaker FW Ver 2.05'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_e20_100_noserial'  (string)
  info.vendor = 'Pegasus Technologies Ltd.'  (string)
  input.x11_driver = 'wizardpen'  (string)
  input.x11_options.BottomX = '29405'  (string)
  input.x11_options.BottomY = '29671'  (string)
  input.x11_options.MaxX = '29405'  (string)
  input.x11_options.MaxY = '29671'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.x11_options.TopX = '5619'  (string)
  input.x11_options.TopY = '6554'  (string)
  linux.device_file = '/dev/bus/usb/002/020'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 517  (0x205)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 20  (0x14)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2'  (string)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'NoteTaker FW Ver 2.05'  (string)
  usb_device.product_id = 256  (0x100)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Pegasus Technologies Ltd.'  (string)
  usb_device.vendor_id = 3616  (0xe20)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_e20_100_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_e20_100_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_e20_100_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = false  (bool)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 517  (0x205)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 20  (0x14)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0'  (string)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 256  (0x100)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Pegasus Technologies Ltd.'  (string)
  usb.vendor_id = 3616  (0xe20)  (int)
  usb.version = 1.1 (1.1) (double)

```
The hal seemes to be finding it and loading wizardpad but it dosnt show up in input devices and X seems to see it but not beleve that you can point with it. 
Thats where I get stuck. I have a hunch that if it would show up in the input devices then the rest would work but I dont know what to do to get it there.

Thanks Tesla^3

---

### Post by Favux on 2009-08-20
Hi Tesla_Cubed,

We got a similar error message when trying to make a .fdi for the Finepoint (fpit) driver in Kharmic.  Haven't gotten a working .fdi yet.

The wacom.fdi we modified to work and parse linuxwacom names correctly in Jaunty is nested in another match line like so:
```
    <match key="input.originating_device" contains="if0">
	<match key="info.product" contains="Wacom">

	</match>
    </match>
```
So maybe something similar will work?

---

### Post by Tesla_Cubed on 2009-08-21
Well that didn't make any diffrence it did change the number of times the error came up the more nesting the more times the error per plugin of my pen. Starting another instance of X vt5 -logverbose 10 :1. Gave me a much more detaild log to see what is going on. so heres the next clue 

```

(II) config/hal: getting input.x11_driver on /org/freedesktop/Hal/devices/usb_device_e20_100_noserial_if0 returned wizardpen
(II) config/hal: getting input.device on /org/freedesktop/Hal/devices/usb_device_e20_100_noserial_if0 returned (null)
(WW) config/hal: no driver or path specified for /org/freedesktop/Hal/devices/usb_device_e20_100_noserial_if0

```trying difrent things in the .fdi file I managed to get wizardpen to work with a old ibm usb mouse :-k . This revaled a pattern it is in the 2nd line there if X cant get somthing back for input.device it stops throws the error and gose on to somthing else. The lab mouse gives back 
```

(II) config/hal: getting input.device on /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0_if0_0_logicaldev_input returned /dev/input/event12

```and then X happly loads whatever module you tell it to 

So the trick here is to get the pen to show up in the input list. I will grep -i name /proc/bus/input/devices output without X running at all and see what I get this should help tell me where its not loading from. 


Thanks 
Tesla^3

---

### Post by Favux on 2009-08-21
Hi Tesla^3,

Wow!  That's great.

So the key is:
```
(II) config/hal: getting input.device on /org/freedesktop/Hal/devices/usb_device_e20_100_noserial_if0 returned (null)

```
input.device is returning null.

If you can figure that out maybe we can get fpit working too.

I know the 10-Tabletpcs.fdi does some pre-configuring upstream.  I looked at what they did for wacom usb tablets but it didn't seem relevant.  Told freedesktop the form factor was tablet pc, not I guess Wacom external usb tablet.

---

### Post by Tesla_Cubed on 2009-08-21
Hi Favux

Just got done checking the input list without X running and there idenical I pluged in a usb mouse and it was found and added to the list without X running so the input list is handled before X. I think X is looking at the input list for what to do. I will look at the 10-Tabletpcs.fdi fore some more clues. Do the fdi files controol all hutpluging or just things related to X? Any clues on where to look for more of how hutplug works.

Thanks 
Tesla^3

---

### Post by Favux on 2009-08-21
Hi Tesla^3,

I think HAL/dBus/.fdi controls hot plugging.  That was one of the main reasons to go to it.  But that's about all I know about hot plugging.  We went through the HAL spec.s to figure out how to add touch to our wacom usb tablet pc's.  Touch wasn't in the default 10-wacom.fdi.  And also to get it to parse the names HAL/dBus was returning correctly.

HAL spec.s:  [http://people.freedesktop.org/~dkukawka/hal-spec-0.5.11/hal-spec.html](http://people.freedesktop.org/~dkukawka/hal-spec-0.5.11/hal-spec.html)

Possibly relevant HAL and Xinput with some links:  [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

I'll check if I have more links.

---

### Post by Favux on 2009-08-21
Hi Tesla^3,

I think I may have figured out where the problem lies.

Looking at the Xlib manual:  [http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/)  it seems you are right.  It's not doing any configuring.

With the fpit struggle I wondered if we were missing a symlink in udev to the driver.  Maybe udev symlinks weren't just for xorg.conf?  So looking at /etc/udev/rules.d/ I see in 90-hal.rules:
```
# pass all events to the HAL daemon
RUN+="socket:/org/freedesktop/hal/udev_event"
```
Which then reminds me of this:  [http://www.mythic-beasts.com/~mark/random/hal/](http://www.mythic-beasts.com/~mark/random/hal/)  Where he says:
> HAL gets all its information from udevd via one of these rules. When the hal package is installed it adds various rules files to /etc/udev which basically tell udevd to copy everything to HAL: 
So that may be it.  Possibly something isn't handling your usb device correctly in say 20-names.rules.  Or possibly maybe in 60-persistent-input.rules the interface class or protocol isn't being specified for your device?  Or a symlink with your Vendor and Product ID's needs to be added?

Writing udev rules:  [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

So sanity check.  I am on the right track or off the rails?

---

### Post by Tesla_Cubed on 2009-08-21
Hi Favux

I think that might be close. All the other usb devices I have show 3 fields usb.device_class, usb.device_subclass , and usb.device_protocall. 3 in the device class semes to make it load the USBHID driver and look for a nother device down the tree then look at usb.device_subclass to tell what it dose 2 seems to be mice and 1 keybords at least for all of them I could find this evening. this tells it what to show in the info.capabilites then udev picks its best guess of kenal driver and that is what wizardpen is trying to get the name of. My pen show 2 nodes in the usb tree 
       Note Taker FW ver 2.05  all 3 usb varables are 0
          -USB hid Device usb.class=3 the other 2 are 0 
so i think its not being reconised as a pen it gets as far as USB hid then cant tell

This is very simmlar to a networking porblim I had on my zarus (small linux handheld) I bought a miniPCMCIA card to get it to work I had to add its vendor.name to a huge list of cards so that the driver would load. My card had a .v2 after its name so of corse it didnt work untell I changed the list. 

The udev list may live somwhere else on Jaunty this is what I have on the notebook.
```

david@HP-dv6000:/etc/udev/rules.d$ ls
010_local.rules   70-persistent-cd.rules   README
010_local.rules~  70-persistent-net.rules

```However on my cnc box runing Hardy There are a bunch of them 
```

david@emc-cnc-1:/etc/udev/rules.d$ ls
05-options.rules                   70-persistent-net.rules
05-udev-early.rules                75-cd-aliases-generator.rules
20-names.rules                     75-persistent-net-generator.rules
30-cdrom_id.rules                  80-programs.rules
40-basic-permissions.rules         85-alsa.rules
40-permissions.rules               85-brltty.rules
45-fuse.rules                      85-hdparm.rules
45-libmtp7.rules                   85-hplj10xx.rules
50-libpisock9.rules                85-hwclock.rules
50-xserver-xorg-input-wacom.rules  85-ifupdown.rules
55-hpmud.rules                     85-pcmcia.rules
60-persistent-input.rules          90-modprobe.rules
60-persistent-storage.rules        95-hal.rules
60-persistent-storage-tape.rules   95-udev-late.rules
60-symlinks.rules                  99-rtai.rules
61-persistent-storage-edd.rules    README
70-persistent-cd.rules

```So somthing along the lines of a heres how to tell a G-Pen100 is a usb pen and treat it as one even tho the usb identfiers dont tell you anything file. 
The other pens that people have gotten working are seem to tell the computer they are eather a usb mouse or a usb tablet this one semms to tell very litle. The windows driver for it ties to its maker and its device name to tell whitch usb device to look at. 

Thanks will work on it more tommorw
kde-hal-device-manager once installed gives a nice tree stile view of lshal

Tesla^3

---

### Post by Favux on 2009-08-22
Hi Tesla_Cubed,

I booted my desktop into Jaunty and sure enough udev rules are now in /lib/udev/rules.d/ instead of /etc/udev/rules.d/.  I did not know that.  So I found this tidbit:
> One of the biggest changes in this release is that the default rules
  are no longer conffiles and are now installed into /lib/udev/rules.d

  You may still add your custom rules to /etc/udev/rules.d and these
  will be processed after the default ones, and can thus override
  anything they do.

  To avoid side-effects of default rules (ie. running of programs),
  create the file with the same name.
From here:  [https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002619.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002619.html)

And the README in both locations talks about adding your own rules in a little more detail.

We may be getting somewhere.

---

### Post by Favux on 2009-08-22
Hi Tesla^3,

Maybe it's suppose to be in /lib/modules/`uname -r`/modules.usbmap?  Wacom tablets are there with Vendor id of 0x056a.  Nothing with "idVendor  0x0e20".  Of course I don't have the wizardpen driver installed.

---

### Post by Favux on 2009-08-22
Hi Tesla^3,

And sure enough as you would expect the wizardpen.c probes for a recognized device.  The relevant code seems to be:
```
/* Heavily inspired by synpatics/eventcomm.c */

#define DEV_INPUT_EVENT "/dev/input/event"
#define EV_DEV_NAME_MAXLEN 64
#define SET_EVENT_NUM(str, num) \
    snprintf(str, EV_DEV_NAME_MAXLEN, "%s%d", DEV_INPUT_EVENT, num)

static Bool
fd_query_wizardpen(int fd, char *wizardpen_name) {
    char name[256] = "Unknown";
    int cmp_at = strlen(wizardpen_name);
    if (cmp_at > 256)
        cmp_at = 256;
    ioctl(fd, EVIOCGNAME(sizeof(name)), name);
    name[cmp_at] = '\0';
	 if (xf86NameCmp(name, wizardpen_name) == 0)
        return TRUE;
    return FALSE;
}

static char wizardpen_name_default[10] = "  TABL";

#ifdef LINUX_SYSFS
static char usb_bus_name[4] = "usb";
static char acecad_driver_name[11] = "usb_wizardpen";
#endif

static Bool
WizardPenAutoDevProbe(LocalDevicePtr local, int verb)
{
    /* We are trying to find the right eventX device */
    int i = 0;
    Bool have_evdev = FALSE;
    int noent_cnt = 0;
    const int max_skip = 10;
    char *wizardpen_name = xf86FindOptionValue(local->options, "Name");
    char fname[EV_DEV_NAME_MAXLEN];
    int np;

#ifdef LINUX_SYSFS
    struct sysfs_bus *usb_bus = NULL;
    struct sysfs_driver *wizardpen_driver = NULL;
    struct sysfs_device *candidate = NULL;
    char *link = NULL;
    struct dlist *devs = NULL;
    struct dlist *links = NULL;
    unsigned int major = 0, minor = 0;
    void *libsysfs = NULL;
#endif

    if (!wizardpen_name)
        wizardpen_name = wizardpen_name_default;

    xf86MsgVerb(X_INFO, verb, "%s: probing event devices for WizardPen tablets\n", local->name);
    for (i = 0; ; i++) {
        int fd = -1;
	      Bool is_wizardpen;

        np = SET_EVENT_NUM(fname, i);
        if (np < 0 || np >= EV_DEV_NAME_MAXLEN) {
            xf86MsgVerb(X_WARNING, verb, "%s: too many devices, giving up %d\n", local->name, i);
            break;
        }
        SYSCALL(fd = open(fname, O_RDONLY));
        if (fd < 0) {
            if (errno == ENOENT) {
                if (++noent_cnt >= max_skip)
                    break;
                else
                    continue;
            } else {
                continue;
            }
        }
        noent_cnt = 0;
        have_evdev = TRUE;
        is_wizardpen = fd_query_wizardpen(fd, wizardpen_name);
        SYSCALL(close(fd));
        if (is_wizardpen) {
            goto ProbeFound;
        }
    }
    xf86MsgVerb(X_WARNING, verb, "%s: no WizardPen event device found (checked %d nodes, no device name started with '%s')\n",
            local->name, i + 1, wizardpen_name);
    if (i <= max_skip)
        xf86MsgVerb(X_WARNING, verb, "%s: The /dev/input/event* device nodes seem to be missing\n",
                local->name);
    if (i > max_skip && !have_evdev)
        xf86MsgVerb(X_WARNING, verb, "%s: The evdev kernel module seems to be missing\n", local->name);
    return FALSE;
```

---

### Post by Tesla_Cubed on 2009-08-22
Hi Favux 

Some progress made with your help but not quite there yet. After much reading and playing with the links you sent I think I am seeing how this works.

kernal -- basic stuff
udev -- re-wrights dev as nessecry with changes
hal -- keeps track of driver details and modprobes as needed
the rest everyone is used to working with Bash X ext.... 

I came up with 
90-Xserver-GPen.rules to be put in /ect/udev/rules.d
```

# udev GPen rules
# Very alpha version

#Digital Scribe by Iogear GPEN100C   
BUS=="usb",SYSFS{product}=="NoteTaker FW Ver 2.05", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"

```Its a blend of the udev in [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) and the wacom rules in /lib/udev. It makes udev create some simlinks when the pen is pluged in and cat /dev/tablet-event produces a lot of unreadable binary junk when I uncap the Pen :-D , move it, click the butten on the remote, click the pen and or recap it. Cool.
Its still not showing up in /proc/input so wizardpen isnt geting it it comes up as generic HID not a input device :confused: getting closer tho. So what wrights to /proc/input or is it just echoed to?

Thanks 
Tesla^3

---

### Post by Favux on 2009-08-22
Hi Tesla^3,

Very nice!  It looks like you're almost there.

> So what wrights to /proc/input or is it just echoed to?

Good question.  I don't know.  You'd think it would just echo in and since HAL is set up to copy it all there shouldn't be a rights issue.  Could it be because you're running it after the 90-hal.rules.  No that can't be, can it, because they want the custom .rules in /etc/udev/rules.d?

---

### Post by Tesla_Cubed on 2009-08-22
Hi Favux

A little test echo "test" > /proc/bus/input/devices should have added test to the end of the file gives premision denied as dose sudo echo "test" > /proc/bus/input/devices

A little googling seems to tell me /proc dosnt actuly exist its a illusion like dev excpt read only by everyoun including root and the kernal its self makes up what is in it when you try to read from it see [http://www.faqs.org/docs/kernel/x716.html](http://www.faqs.org/docs/kernel/x716.html) . It looks like a kernal module is code snipit that is linked into the kenral and called as needed and a basic kernal device driver reads from the device and wrights the relevent info to /proc/whatever so other processes can see and find it. 

So at this point I see eather two ways make a kernal module so the location of the pen can be reported to other programs through /proc/input/devices, or change wizardpen to look in the HAL or UDEV for the /dev/tablet-event or sysfs path to it maby a load switch like input.x11driver_path. The 2nd option is more flexable but I dont think my C++ is up to the task I'll take a stab at it but if anyone gets there first thats cool too. A kernil module might only work for my pen or even just one usb port on my notebook if i read the wrong address off and hard code it in, maby look for the name and then use that to get the address (shades of the old PnP days here).

Side thought
Somthing simmlar to this might solve the problim with some keybords and mice not being reconised if they report somthing like usb.device.class=255 (manufacture spific) or =0 (look at next device in chain to tell) whitch are passed stright through ending up on dev/usb/DeviceName_if_it_gave_one. This lets a spefic program in user space talk to it using its usb address but things like X looking in /proc to find the link see nothing, but works good for geting unknown devices to talk to things like a VMware box or vendor provided pice of software USB instrments dose this with there stingray usb oscilacope / function genrator (another thing on my list of things to get working in linux) they give the dll's out and a wraper that gets them to talk to the scope from linux and the rest is up to the user.
/Side thought

Maby a VMware box inside my notebook runing xp to talk to the pen once school starts.

Thanks
Tesla^3

---

### Post by Favux on 2009-08-22
Hi Tesla_Cubed,

I'm not sure how useful this is.  It shows how Ron at Debian and Ping at LWP solved adding touch to the 50-wacom.rules:
> KERNEL!="event[0-9]*", GOTO="wacom_end"

# The ID_PATH variable is set by the "path_id" script in an earlier rule file.
ATTRS{idVendor}=="056a", ENV{ID_PATH}=="?*", SYMLINK="input/by-path/$env{ID_PATH}-wacom"

# Multiple interface support for stylus and touch devices.
DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="00", ENV{WACOM_TYPE}="stylus"
DRIVERS=="wacom", ATTRS{bInterfaceNumber}=="01", ENV{WACOM_TYPE}="touch"
Then there is a big table of symlinks including two tablet pc's with touch, one of which is mine:
> ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0093",  SYMLINK="input/tablet-tpc93-$env{WACOM_TYPE}"
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="009a",  SYMLINK="input/tablet-tpc9a-$env{WACOM_TYPE}"
And then to finish:
> # Convenience links for the common case of a single tablet.  We could do just this:
#ATTRS{idVendor}=="056a", SYMLINK+="input/wacom-$env{WACOM_TYPE}"
# but for legacy reasons, we keep the input/wacom link as the generic stylus device.
ATTRS{idVendor}=="056a", ENV{WACOM_TYPE}!="touch", SYMLINK+="input/wacom"
ATTRS{idVendor}=="056a", ENV{WACOM_TYPE}=="touch", SYMLINK+="input/wacom-touch"

# Check and repossess the device if a module other than the wacom one
# is already bound to it.
ATTRS{idVendor}=="056a", ACTION=="add", RUN+="check_driver wacom $devpath $env{ID_BUS}"

LABEL="wacom_end"
I think the first line might be relevant to you, especially:
```
SYMLINK="input/by-path/
```
The check and repossess line also might come in useful if we get that far.

From my post #90 here:  [http://ubuntuforums.org/showthread.php?p=7065804](http://ubuntuforums.org/showthread.php?p=7065804)

Edit:  To see the whole thing go to Appendix 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  The wget command will download it.  Although come to think of it it may already be installed in the new location.  I think they may have renumbered it also.

---

### Post by Tesla_Cubed on 2009-08-23
Hi Favux

That looks like the exact pice of the bridge that we need. I will look at the wacom source for the kernal drive and see if I get any inspration form it. I am much better at recycling and changing code then making it up from scratch. Thats the great thing about linux there are lots of frendly giants to stand on the sholders of so to speek. Ive ben reading up on kernal drives and am thinking of somthing like.

Identfy it by name and manafucture.
Make char device in udev.
Put useful info into /proc/bus/input/devices

maby make the driver read a .config file so it could be easly changed or grown  for other odd reporting devices in future

wizardpen whith the fdi should do the rest 

This just got a lot easer with a working example of the same problim to look at.

Thanks 
Tesla^3

---

### Post by Favux on 2009-08-23
Hi Tesla^3,

Great!

In addition to wacom.ko you might want to look at hid-ntrig.c (builds the hid-ntrig.ko file I think).  Ayuthia has samples of Rafi Rubin's patches to the usb HID section of the kernel that enables the n-trig digitizer.  See post #157 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=16](http://ubuntuforums.org/showthread.php?t=1038898&page=16) and post #186 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=19](http://ubuntuforums.org/showthread.php?t=1038898&page=19)

---

### Post by Tesla_Cubed on 2009-08-24
Hi Favux

Cool it is getting closer. I'm back in school and ask one of the profs what he thought and his idea was to add a option device to the wizard pen driver so it could be told to look at a  device device or symlink sence cat /dev/tablet-event is making output kind of like post 159 in [http://ubuntuforums.org/showthread.php?t=1038898&page=16](http://ubuntuforums.org/showthread.php?t=1038898&page=16). Might be easer than a kernal driver. I've ben trying to get my C++ back up to speed and the kernal is new to me I found a online how to [http://tldp.org/LDP/lkmpg/2.6/html/x181.html](http://tldp.org/LDP/lkmpg/2.6/html/x181.html) and I get stuck at make it throws back no target spesfied for .....   after some more looking I found they were using "kbuild" I installed along with the kernal librarys it seems to find them but not know what to do that was the job of kbuild I thought unless I am missing somthing on how to build a kernal module from scratch. Tho chainging one of the existing ones may not be that hard if its just adding it to a list of known hardwar inside it somewhere. Getting closer :)

Thanks
Tesla^3

---

### Post by Favux on 2009-08-24
Hi Hi Tesla^3,

That's sounds reasonble.  Funny you should mention it, that's exactly what I'm talking about in post #151 on the same page you link to.  That's what Rafi's n-trig.patch does, adds n-trig to the wacom devices table:
```
patch linuxwacom-0.8.3-5/src/xdrv/wcmUSB.c < n-trig.patch
```
A little more on it I guess in #145 and the link to the patch in #136.

Hope school is going well and you are enjoying it.

---

### Post by Tesla_Cubed on 2009-08-25
Hi Favux

Some more progress. I was looking at the source for wizardpen and didnt see where it was opening /proc/input unless its buryed up in one of the standard hedders, so I thought what if I added 
 ```
<merge key="input.device" type="string">/dev/input/tablet</merge>
``` to the fdi file and used
```

# udev GPen rules
# Very alpha version

#Digital Scribe by Iogear GPEN100C   
ATTRS{manufacturer}=="Pegasus Technologies Ltd.", ATTRS{product}=="NoteTaker FW Ver 2.05", NAME="input/tablet", MODE="0666"

# ATTRS{idVendor}=="0e20", ATTRS{idProduct}=="0100" SYMLINK+="tablet-event"
#  ATTRS{manufacturer}=="Pegasus Technologies Ltd."
#   ATTRS{product}=="NoteTaker FW Ver 2.05", ATTR{bInterfaceClass}=="03",
```For .rules ..... it sort of worked wizardpen loaded on pluging in the pen :P  (it reads the hall not /proc/) it didnt do anything onece in but it loaded I tryed cat /dev/input/tablet nothing untell I uncaped the pen then X crashed then Kernal crashed ? Hard restat later same config files pluged in the pen and get 
```

(II) config/hal: Adding input device NoteTaker FW Ver 2.05
(**) NoteTaker FW Ver 2.05: TopX = 0
(**) NoteTaker FW Ver 2.05: TopY = 0
(**) NoteTaker FW Ver 2.05: BottomX = 100
(**) NoteTaker FW Ver 2.05: BottomY = 100
(**) Option "Device" "/dev/input/tablet"
(EE) xf86OpenSerial: Cannot open device /dev/input/tablet
    No such file or directory.
(EE) NoteTaker FW Ver 2.05: unable to open device
(EE) PreInit returned NULL for "NoteTaker FW Ver 2.05"
(EE) config/hal: NewInputDeviceRequest failed (8)

```it finds the pen but cant start the io steram cat /dev/tablet shows Cannot open device /dev/input/tablet [no such file or directory] or [no such device or address]. Rebooted into windoze ~30 min of updates later pen still working ok [good I didnt kill it by probing] rebooted back to linux theres about a 1 in 10 chance that when the pin is pluged everything will work and cat /dev/input/tablet shows a data stream when that happens wizard pen will load as well. I have compared settings form time to time and it seams random whether or not it loads in ok. Even when it dose the only thing I can get it to do is crash X, heres how if the pen is caped take off the cap --> X goes away a second or 2 later login reapirs all tasks runing in X gone too, if the pen is uncaped put the cap back on then uncap it same as above.

Thanks Tesla^3

---

### Post by Favux on 2009-08-25
Hi Tesla^3,

Maybe something more like?:
```
# Link Digital Scribe by Iogear (USB) to "/dev/input/tablet"
KERNEL=="event*", ATTRS{idVendor}=="0e20", ATTRS{idProduct}=="0100", SYMLINK="input/tablet"
```
Plus or minus the mode entry, where the xorg entry would be:
```
	Option "Device" "/dev/input/tablet"
```
and similar in .fdi

---

### Post by Favux on 2009-08-25
Did you check the 5.1 spec. if:
```
<merge key="input.device" type="string">/dev/input/tablet</merge>
```
is the right syntax.  And not something like?"
```
<merge key="input.x11_device" type="string">/dev/input/tablet</merge>
```
or
```
<merge key="input.x11_options.Device" type="string">/dev/input/tablet</merge>
```
Making it something like?:
```
<!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <!-- This MUST match with the name of your tablet -->
    <match key="info.product" contains="NoteTaker FW Ver 2.05">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.Device" type="string">/dev/input/tablet</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
        <merge key="input.x11_options.TopX" type="string">5619</merge>
        <merge key="input.x11_options.TopY" type="string">6554</merge>
        <merge key="input.x11_options.BottomX" type="string">29405</merge>
        <merge key="input.x11_options.BottomY" type="string">29671</merge>
        <merge key="input.x11_options.MaxX" type="string">29405</merge>
        <merge key="input.x11_options.MaxY" type="string">29671</merge>
    </match>
  </device>
</deviceinfo>
```

Edit:  Thinking about it, and given what the Option for the xorg.conf is, I'm semi-sure that it's actually the second .fdi line.  The one with "input.x11_options.Device".

---

### Post by Favux on 2009-08-25
Hi Tesla^3,

Also one thing I've been curious about is, is there a difference between:
```
SYMLINK=
```
and?
```
SYMLINK+=
```
The examples I've seen seem to imply it but I can't work out what.  So maybe they're just typos?  And by happy chance it works even without the '+'?

---

