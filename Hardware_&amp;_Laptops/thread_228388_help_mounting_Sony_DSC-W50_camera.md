---
title: "help mounting Sony DSC-W50 camera?"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by nashife on 2006-08-03
Hi all,

I just bought a Sony DSC-W50 digital camera and I'm not able to mount it as a mass-storage device.  

I'm really a beginner and I could use some help explaining what I need to know to figure out what's wrong or why it is not detected. I searched the ubuntu forums but I can't find answers yet.

when I type dmesg, these are the last lines...I've seen in other threads that people ask for this, but I don't yet understand what it means: 

[17180008.660000] usb 5-7: USB disconnect, address 4
[17180011.168000] usb 5-7: new high speed USB device using ehci_hcd and address 5

How can I mount my camera manually as a mass storage device? It auto-mounts on my ibook fine, so I'm sure the camera works properly.

Thanks in advance.

**Edit:** I just discovered that I CAN import photos with Gthumb as long as I have it set to auto-import when a camera is detected and I'm using the right setting in the camera (not mass storage).

This is good, but I'd still like to learn how to troubleshoot mounting it as a mass storage device.  I'm seeing a lot more people with problems with mounting it as a mass storage device... perhaps it's just not possible right now.

---

### Post by zxee on 2006-08-03
It is possible. I have a sony dsc camera also. I don't remember the exact model but it does automount when I plug it in and turn it on.
Since you know how to do that with the ibook I presume that you have the camera selector set to the correct setting to use for transfer. 
Maybe you want to provide more of your computers hardware specs and the version of ubuntu you are running?

---

### Post by nashife on 2006-08-03
I'm running Dapper, and I'm on a custom built machine... AMD processor, what other hardware specs would people need to help me troubleshoot this?

When I connect with my ibook, it just auto-mounts and places the icon on my desktop just like any other device.

When I connect to my Ubuntu machine, nothing happens.  When I enabled the "import images when camera connected", it auto-ran Gthumb and imported my images, but still there is nothing mounted on my desktop.

I hope that makes sense.

It would be helpful if you knew what model you're using. I've seen people say that earlier models worked fine, auto mounted, etc... but other models did not work.

---

### Post by zxee on 2006-08-04
> **nashife said:**
> 

It would be helpful if you knew what model you're using. I've seen people say that earlier models worked fine, auto mounted, etc... but other models did not work.

I'm not at home but I'll check the model for you when I get there.
The camera is a recent model-got it this past Christmas-I think it's a DSC-7 anyway I'll check. 
I've been using linux for some time now and have never had any problems mounting digital cameras. I know that doesn't help you but I think the problem can be hardware related-however if you can import as you said then it's probably not a usb issue.
I wonder if HAL or hotplugging is functioning correctly.
Two things to try: From a terminal do lsmod and dmesg.
The dmesg command, done after you've plugged in your camera, should show some output about a usb device. The lsmod command will tell you if all the necessary modules are loading. 
Post the output here. Hope that helps.

Added: The model of my sony camera is DSC-W7

---

### Post by chiron69 on 2006-08-18
I also have this camera Sony DSC-W50 and I can only transfer through PTP mode. (set up in the phone)

some info when I connect it to my computer:

**dmesg:**

[17221159.568000] usb 5-2: new high speed USB device using ehci_hcd and address 7

**sudo lsusb -v**

Bus 005 Device 008: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92 Cybershot/Mavica Digital Camera
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x054c Sony Corp.
  idProduct          0x0010 DSC-S30/S70/S75/F505V/F505/FD92 Cybershot/Mavica Digital Camera
  bcdDevice            6.00
  iManufacturer           1 Sony
  iProduct                2 Sony DSC
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass    255
      bInterfaceProtocol      1
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              16
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

**sudo fdisk -l**

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1       23943   192322116   83  Linux
/dev/sda2           23944       24321     3036285    5  Extended
/dev/sda5           23944       24321     3036253+  82  Linux swap / Solaris

---

### Post by zxee on 2006-08-18
chiron69, I don't know why your camera doesn't automount.
Mine does here the output of my lsmod command:

juntu:~$ lsmod
Module                  Size  Used by
ppp_deflate             6272  0
zlib_deflate           24344  1 ppp_deflate
bsd_comp                6272  0
ppp_async              11904  1
crc_ccitt               2304  1 ppp_async
ppp_generic            30100  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7424  1 ppp_generic
ipv6                  265728  8
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
tsdev                   8000  0
usblp                  13056  0
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
psmouse                36100  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
nvidia               4550772  12
floppy                 62148  0
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
rtc                    13492  0
serio_raw               7300  0
pcspkr                  2180  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
amd64_agp              12356  1
agpgart                34888  2 nvidia,amd64_agp
i2c_nforce2             6912  0
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_nforce2
sg                     37920  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
usb_storage            74176  0
forcedeth              30732  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  5 usblp,usb_storage,ehci_hcd,ohci_hcd
pdc202xx_new            9600  1
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  6
generic                 5124  0
sd_mod                 19984  1
amd74xx                15260  0 [permanent]
sata_nv                 9732  4
libata                 78992  1 sata_nv
scsi_mod              139496  6 sr_mod,sbp2,sg,usb_storage,sd_mod,libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

Compare that with yours and see if a module isn't loading?
There are other posts on digital cameras in the forums too.

---

### Post by dmery on 2006-08-30
I have the same problem with this camera (DSC-W50)](*,)  , Ubuntu does not open a directory, but when I connected my old Sony DSC-P93 not problem, it works fine.:) 
Someone knows haw to set Sony DSC-W50 ? I would appreciate some help and support

thanks in advance
regards,
dmery

---

### Post by zxee on 2006-08-30
There is a hardware database at: [http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)
and a supported hardware section for ubuntu here [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

It's obvious that manufacturers change the internal specs of their devices without informing anyone-so it's really hard for open source developers to keep their software compatible.

Note: I did a search for this an found that there is an O'Reilly page specific to getting a digital camera working in linux. It's for debian and should work with ubuntu too. Go here: [http://www.linuxdevcenter.com/pub/a/linux/2005/01/06/digicam.html](http://www.linuxdevcenter.com/pub/a/linux/2005/01/06/digicam.html)

---

### Post by Atomic Dog on 2006-08-30
I love that camera (bought it about a month ago).  great photos, great clarity.  Yet I also can't get it to connect :(

---

### Post by Atomic Dog on 2006-09-05
I found the trick for the DSC-W30 / W50 & more sony cameras!  Press the menu button on the camera after it's connected to the USB port. Then select the USB mode setting from "Auto" to "PTP." Ubuntu will suddenly see the camera and will start gthumb to pull down the photos.

---

### Post by scottym on 2007-08-17
I have the DCS 55 and it mounts and stores the photos but I can not get it to play back movies. I get an error msg: Totem could not play 'file:///media/usbdisk/DCIM/101MSDCF/MOV00068.MPG'. I have added the the extra pludins for Totem but still it does not work. Has anyone gotten this feature to work?

---

### Post by Aleksandro on 2007-12-29
Hi nashife! Hope you're doing great.

Both, the W35 and W50 Sony DSC cameras, have 4 options for external connections:

1. [PictBridge]("http://en.wikipedia.org/wiki/PictBridge")

2. [PTP]("http://en.wikipedia.org/wiki/Picture_Transfer_Protocol")

3. [USB Mass Storage]("http://en.wikipedia.org/wiki/USB_mass_storage_device_class")

4. AUTO

So, to make Ubuntu load up a drive volume (Nautilus for example) as soon as you plug the device to a USB port, on the camera:

Press the "Menu" button, and choose the "Setup" option. On the next menu, go to "Setup 2" and select "USB Connect", set it to "Mass Storage".

There you go gal! Plug your camera to a USB port and be happy!

Hope you got it done. :)

---

