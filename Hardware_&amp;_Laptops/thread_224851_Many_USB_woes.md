---
title: "Many USB woes"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by dean.s.wood on 2006-07-28
Hi,

I am just about at the end of my tether here. I have struggled and struggled to get my usb ports working on ubuntu and so far not a single thing has changed (which is frustrating as everything else works.)

I have a usb key and also an external hard drive by Lacie. I know the hardware on both of these works fine as windows has no problems with them.

The first question I have is where is the mountpoint in /dev for the USB ports? On previous versions of Linux it has been sda* with the star depending on the port but these don't appear on ubuntu. This is slightly academic as I don't get to a point where I could mount them. 

On plugging in anything on the usb port and doing lsusb I see that nothing is 'seen'. When doing dmesg I get the following printout:

[17181882.072000] usb 4-3: new high speed USB device using ehci_hcd and address 15
[17181892.496000] usb 4-3: device not accepting address 15, error -110
[17181892.608000] usb 4-3: new high speed USB device using ehci_hcd and address 16
[17181903.032000] usb 4-3: device not accepting address 16, error -110
[17182782.472000] usb 4-3: new high speed USB device using ehci_hcd and address 17


and so on. Now googling gives me a certain fix which seems to work for some people which is removing ehci_hcd (so modprobe -r ehci_hcd) which does stop me recieving the error messages. But lsusb still sees nothing on the usb ports.

root@dean-laptop:/home/dean# lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

I have spent ages on this thing and cannot get any joy and am very close to surrendering and admitting linux is pants for usb and I still need windows.

So if anyone has any ideas or suggestions I would greatly appreciate it.

Thanks 

Dean

---

### Post by jordilin on 2006-07-28
Ubuntu mounts external usb hard drives and flash drives automatically. It's weird. I suppose that you have rebooted your system to see if that happens again and it does. Give us your fstab, located in /etc and we will be able to see what's going on or not ;)

---

### Post by dean.s.wood on 2006-07-28
Hi,

I have tried so many things it is unbelievable. Just for a laugh, I have just reinstalled and tried again same message (see below):
[
4294958.111000] usb 4-3: new high speed USB device using ehci_hcd and address 2[4294959.111000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[4294969.645000] usb 4-3: device not accepting address 2, error -110
[4294969.747000] usb 4-3: new high speed USB device using ehci_hcd and address 3

It just repeats from here. Previous to reinstalling I modified fstab with a line something like:

/dev/sda1     /media/usbdisk    auto    defaults,user,users,noauto,noatime  0  0

I didn't expect this to work as according to my system /dev/sda1 doesn't exist. 

Anyway, here is a copy of my fstab now.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



Do you think it would be worth putting a line like that back in or is there something more fundamental happening? Should I not be able to see sda1 or similar in /dev?

Don't really know if it would be any use but here is a copy of mtab:

/dev/hda6 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-23-386/volatile tmpfs rw 0 0
/dev/hda7 /home ext3 rw 0 0
/dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0

I am really at a loss.


Thanks for any help you can give me.


Dean

---

### Post by jordilin on 2006-07-28
> **dean.s.wood said:**
> 
> lrm /lib/modules/2.6.15-23-386/volatile tmpfs rw 0 0



I see that you are using the kernel 2.6.15-23-386. Type 
```
uname -r
``` and give us the kernel version, so as to be sure.
If it is the 386 version, update to the 686 version and with smp support if your cpu supports that. I'm quite sure is a problem of the kernel version.

---

### Post by dean.s.wood on 2006-07-29
Hi,

I upgraded to the 686 version and had the same problem. Also,with the 686 version the wifi connection died the death as well. This does not seem to be the answer. Can anyone answer the question about where I should see my USB ports? I am used to seeing /dev/sda* with * being a number but I am not seeing this here. 

I am tired at the mo so I am feeling completely beaten by this and will play with the 686 version when I am a little more awake. By the way, what was smp support that you suggested on the kernel?

Thanks again for all the help.

Dean

---

### Post by wcbaker on 2006-07-30
I am having the exact same problem, where anything I plug into my USB refuses to work. I have the same kernel and I'm on a IBM T42.

---

### Post by dean.s.wood on 2006-07-30
Hi,

googling for this kind of thing it seems to be a pretty common fault. The demoralising thing is that all the threads about it seem to wander into oblivion without a solution. 

I am getting the impression this is a known fault everyone has given up on until the next release. That doesn't help us very much. I think we may have to resign ourselves to the discomfort of keeping dual boot and transfer things through windaz.

Dean

---

### Post by dean.s.wood on 2006-07-30
Sorry to post too many times but can someone at least answer this question about ubuntu: Where are you meant to see the USB ports? I have seen in other posts referrals to /dev/sda but my configuration doesn't seem to have this. Every other distribution I have used I have mounted usb stuff on /dev/sda so is ubuntu different or is this indicative of the usb not setting up right.

Thanks

Dean

---

### Post by br77 on 2006-08-12
I know that this thread is a bit old, but I am having the same problem. I upgraded the kernel to 686, and still nothing.

In my case, I have a USB thumbdrive, a USB mouse, and a Nikon D50 camera. When I plug these in, nothing happens. /var/log/messages does not change, and lsusb shows nothing.

To answer the question above, USB storage devices should be registering in /dev/sda*, but there is no /dev/sd* when I plug these devices in, which seems to be the case with everyone else.

Has anyone gotten any farther with this?

Brian

---

### Post by Original Brownster on 2006-08-14
Hi, have you no usb working at all? 
What pc /laptop are u using? 

Might be worth checking that the on board usb controllers are being correctly identified and loading the drivers.

"dmesg | grep -i hcd" and "dmesg | grep -i usb" should at least show that the controllers have been found and assigned the correct usb drivers.
Also check "lsmod | grep -i usb" for loaded modules.

If you could confirm this and any working usb devices that would be a start and may show something?

HTH

---

### Post by br77 on 2006-08-14
I'm on a Systemax laptop with a 2.4 GHz Intel celeron. As far as I can tell, there is no USB working at all. I have a Wacom tablet that I am able to use on my Thinkpad R40 with the dapper live CD running, but when I plug it into the Systemax, the power light does not even turn on.

Here is the output of those three commands you suggested. It looks to me as though things are being loaded, but I'm not sure.

dmesg | grep -i hcd

```
[17179578.908000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.908000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179579.456000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179579.456000] ohci_hcd 0000:00:03.0: irq 10, io mem 0xdfff7000
[17179579.616000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179580.136000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179580.136000] ohci_hcd 0000:00:03.1: irq 10, io mem 0xdfff8000
[17179580.296000] ohci_hcd 0000:00:03.2: OHCI Host Controller
[17179580.820000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179580.820000] ohci_hcd 0000:00:03.2: irq 10, io mem 0xdfff9000
[17179580.984000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179580.984000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[17179580.984000] ehci_hcd 0000:00:03.3: irq 11, io mem 0xdfffa000
[17179580.984000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
```

dmesg | grep -i usb

```
[17179573.620000] PCI0 PS2M PS2K  EC0  LID USB1 USB2 USB3 USB4 S139  LAN  MDM  AUD CBC0 SLPB 
[17179578.904000] usbcore: registered new driver usbfs
[17179578.904000] usbcore: registered new driver hub
[17179578.908000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179579.456000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179579.512000] hub 1-0:1.0: USB hub found
[17179580.136000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179580.192000] hub 2-0:1.0: USB hub found
[17179580.820000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179580.876000] hub 3-0:1.0: USB hub found
[17179580.984000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[17179580.984000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.988000] hub 4-0:1.0: USB hub found

```

lsmod | grep -i usb

```

usbcore               139076  4 ndiswrapper,ehci_hcd,ohci_hcd

```

Any insights that anyone can come up with will be much appreciated.

Brian

> **Original Brownster said:**
> Hi, have you no usb working at all? 
What pc /laptop are u using? 

Might be worth checking that the on board usb controllers are being correctly identified and loading the drivers.

"dmesg | grep -i hcd" and "dmesg | grep -i usb" should at least show that the controllers have been found and assigned the correct usb drivers.
Also check "lsmod | grep -i usb" for loaded modules.

If you could confirm this and any working usb devices that would be a start and may show something?

HTH

---

### Post by Original Brownster on 2006-08-15
Hi Brian,

Are u using Dapper Drake? If so did u upgrade from Breezy?
The reason i ask is with Dapper it switched to using UDEV and moved away from the hotplug scripts.
Working with just your thumbdrive first, i take it this is a usb stick? which should appear as a fat formatted file system? let us know as much as you can.

on plug in you would expect to see some kernel messages, again look at dmesg after plugging in and post the output. also lsusb.
We should see the usb storage driver load I believe and this will show with lsmod.

The output posted shows the controller and bus load the correct drivers (AFAIK)

---

### Post by br77 on 2006-08-15
OB,

Thanks for responding.

I am on Dapper, but it's a fresh install on a new laptop that I bought sans an OS (it did come with a FreeDOS CD, though). The thumbdrive is a 1 GB Lexar JumpDrive.

dmesg shows nothing new with the thumbdrive plugged in (the output is the same as in my previous post). lsusb also appears to be fruitless: "Bus 004 Device 001: ID 0000:0000" (same for Bus 1, Bus 2, and Bus 3). Should they all be Device 001?

tail -f /var/log/messages also shows no action when I plug in/unplug any usb devices.

Incidentally, I'm also working on a few other problems. It's a long shot, but perhaps there is some relationship: (1) the fan appears to be on all the time (including when in suspend); (2) closing the laptop lid puts the computer into suspend mode (with the fan still whirring), but opening the lid does not wake it up--I have to reboot; (3) the screensaver runs at a slow fsp, it's very choppy. I'm suspecting that problems 2 and 3 could be related (improper video drivers, for example). All of these issues are, of course, for another thread.

p.s. Love your signature!

---

### Post by ephesius on 2006-08-15
I have this problem on my thinkpad t40. A workaround is to remove the ehci_hcd module.

```
modprobe -r ehci_hcd
```

---

### Post by Original Brownster on 2006-08-15
Hi, 
That's interesting, isn't this the usb 2.0 driver your removing? Leaving another like ohci or uhci loaded which would still give usb 1.1 support? 

> **ephesius said:**
> I have this problem on my thinkpad t40. A workaround is to remove the ehci_hcd module.

```
modprobe -r ehci_hcd
```

---

### Post by Original Brownster on 2006-08-15
Hi, 
I've been trying to get to the bottom of this, and the nearest I can find is in the [URL="http://www.linux-usb.org/FAQ.html#ts2"]linux usb faq: 
[/URL]

quote:

You may have some problem with your PCI setup that's preventing your USB host controller from getting hardware interrupts. (Current Linux 2.6 kernels will actually tell you when they notice this problem; see the "dmesg" output.) When Linux submits a request, but never hears back from the controller, this is the diagnostic you'll see. To see if this is the problem, look at /proc/interrupts to see if the interrupt count for your host controller driver ever goes up. If it doesn't, this is the problem: either your BIOS isn't telling the truth to Linux (ACPI sometimes confuses these things, or setting the expected OS to windows in your BIOS), or Linux doesn't understand what it's saying.

unquote.

I think it may be an interrupt issue, try passing the 'noapic' kernel option at boot up. fingers crossed.

HTH

> **br77 said:**
> OB,

Thanks for responding.

I am on Dapper, but it's a fresh install on a new laptop that I bought sans an OS (it did come with a FreeDOS CD, though). The thumbdrive is a 1 GB Lexar JumpDrive.

dmesg shows nothing new with the thumbdrive plugged in (the output is the same as in my previous post). lsusb also appears to be fruitless: "Bus 004 Device 001: ID 0000:0000" (same for Bus 1, Bus 2, and Bus 3). Should they all be Device 001?

tail -f /var/log/messages also shows no action when I plug in/unplug any usb devices.

Incidentally, I'm also working on a few other problems. It's a long shot, but perhaps there is some relationship: (1) the fan appears to be on all the time (including when in suspend); (2) closing the laptop lid puts the computer into suspend mode (with the fan still whirring), but opening the lid does not wake it up--I have to reboot; (3) the screensaver runs at a slow fsp, it's very choppy. I'm suspecting that problems 2 and 3 could be related (improper video drivers, for example). All of these issues are, of course, for another thread.

p.s. Love your signature!

---

### Post by ephesius on 2006-08-15
> **Original Brownster said:**
> Hi, 
That's interesting, isn't this the usb 2.0 driver your removing? Leaving another like ohci or uhci loaded which would still give usb 1.1 support?

I don't know exactly what the module is but I still get the speeds of usb 2.0 so I am assuming that uhci isnt the usb 2.0 driver.
I could be wrong though.

---

### Post by br77 on 2006-08-16
modprobe -r ehci_hcd didn't do anything, nor did noapic (ahem, even after I realized that it was "noapic" not "noacpi"). lsusb showed nothing, and there was nothing new in dmesg.

On the advice of that faq, I disabled USB support in the BIOS, but that also didn't do anything, even if combined with the noapic option.

Any further test ideas very much welcome. Maybe some other BIOS option is the problem?

Brian

> **Original Brownster said:**
> Hi, 
I've been trying to get to the bottom of this, and the nearest I can find is in the [URL="http://www.linux-usb.org/FAQ.html#ts2"]linux usb faq: 
[/URL]

quote:

You may have some problem with your PCI setup that's preventing your USB host controller from getting hardware interrupts. (Current Linux 2.6 kernels will actually tell you when they notice this problem; see the "dmesg" output.) When Linux submits a request, but never hears back from the controller, this is the diagnostic you'll see. To see if this is the problem, look at /proc/interrupts to see if the interrupt count for your host controller driver ever goes up. If it doesn't, this is the problem: either your BIOS isn't telling the truth to Linux (ACPI sometimes confuses these things, or setting the expected OS to windows in your BIOS), or Linux doesn't understand what it's saying.

unquote.

I think it may be an interrupt issue, try passing the 'noapic' kernel option at boot up. fingers crossed.

HTH

---

### Post by Original Brownster on 2006-08-16
Hi,
mmm, does 'cat /proc/interrupts' show an increasing number against the usb controller lines? Below I pasted part of my output and the last line shows irq 5 then 28881, this number increases each time the cpu gets a response from the usb controller. if this is working / not working it tells us something more.

           CPU0
  0:      59812          XT-PIC  timer
  1:         99          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:      28881          XT-PIC  uhci_hcd:usb1, uhci_hcd:usb2

Is there an OS option in the bios, set to windows? just another thing to try. Failing this I'm running out of ideas!

> **br77 said:**
> modprobe -r ehci_hcd didn't do anything, nor did noapic (ahem, even after I realized that it was "noapic" not "noacpi"). lsusb showed nothing, and there was nothing new in dmesg.

On the advice of that faq, I disabled USB support in the BIOS, but that also didn't do anything, even if combined with the noapic option.

Any further test ideas very much welcome. Maybe some other BIOS option is the problem?

Brian

---

### Post by br77 on 2006-08-16
It does show an increasing number with irq 5:

```

           CPU0       
  0:     240877          XT-PIC  timer
  1:        195          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:      60366          XT-PIC  ohci1394, ohci_hcd:usb3, yenta, yenta, ath0
  7:          2          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:       1424          XT-PIC  acpi
 10:      42602          XT-PIC  ohci_hcd:usb1, ohci_hcd:usb2, SiS SI7012
 12:      63235          XT-PIC  i8042
 14:       9401          XT-PIC  ide0
 15:      16534          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

```

Note that this is with BIOS USB support turned off. Under this same state, lsusb shows only 3 buses, whereas with BIOS USB support turned on, there are 4 buses. Here is what /proc/interrupts looks like with BIOS USB:

```

           CPU0       
  0:      88642          XT-PIC  timer
  1:        360          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:      19460          XT-PIC  ohci1394, yenta, yenta, ath0
  7:          1          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:        676          XT-PIC  acpi
 10:        638          XT-PIC  ohci_hcd:usb1, ohci_hcd:usb2, ohci_hcd:usb3, SiS SI7012
 11:          0          XT-PIC  ehci_hcd:usb4
 12:      16315          XT-PIC  i8042
 14:       7475          XT-PIC  ide0
 15:       5526          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

```

(The 4th bus is at irq 11.) Do you think that irq 10, which does not increase could be causing problems?

There are no Windows-specific items in the BIOS, but there are a bunch of other hardware options (power management, etc.). I will try turning all of those off to see if there is any improvement.

Brian

> **Original Brownster said:**
> Hi,
mmm, does 'cat /proc/interrupts' show an increasing number against the usb controller lines? Below I pasted part of my output and the last line shows irq 5 then 28881, this number increases each time the cpu gets a response from the usb controller. if this is working / not working it tells us something more.

           CPU0
  0:      59812          XT-PIC  timer
  1:         99          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:      28881          XT-PIC  uhci_hcd:usb1, uhci_hcd:usb2

Is there an OS option in the bios, set to windows? just another thing to try. Failing this I'm running out of ideas!

---

### Post by Original Brownster on 2006-08-17
Hi,
With USB on in the bios the interrupt count on irq10 looks real low. Its a hunch but try and unload the sound module 'SiS SI7012', you may need to look as 'lsmod' to find the correct module name. 
If this doesn't work, try removing the 'ehci' module too, 
if it still doesnt work, turn usb off in the bios then unload the modules again. 
It maybe that the interrupt count we are seeing is not for the usb device but the sound card. 
In an ideal world these should all just get along dandy but stranger things have happened.

Cheers

---

### Post by br77 on 2006-08-18
I'm not sure which is the sound module. I've tried to "modprobe -r" a few of the modules that looked obvious to me (snd_intel8x0 and a few of the other snd modules), but I got a "FATAL: Module ... is in use" error.

Here's the output of lsmod:
```

Module                  Size  Used by
binfmt_misc            13064  1 
rfcomm                 43604  0 
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
ppdev                   9668  0 
ipv6                  286976  20 
speedstep_lib           4580  0 
cpufreq_userspace       6496  0 
cpufreq_stats           6688  0 
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        7752  0 
cpufreq_conservative     9000  0 
video                  16324  0 
tc1100_wmi              6884  0 
sony_acpi               5580  0 
pcc_acpi               12416  0 
hotkey                 11492  0 
dev_acpi               11236  0 
container               4608  0 
button                  6704  0 
acpi_sbs               20172  0 
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
dm_mod                 63256  1 
af_packet              24520  2 
md_mod                 76052  0 
ndiswrapper           189876  0 
sr_mod                 17988  0 
sbp2                   25060  0 
scsi_mod              145960  2 sr_mod,sbp2
lp                     12356  0 
wlan_wep                6912  1 
ath_pci                81852  0 
ath_rate_sample        17224  1 ath_pci
wlan                  146684  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148848  3 ath_pci,ath_rate_sample
irda                  217980  0 
pcmcia                 41948  0 
parport_pc             37988  1 
parport                39400  3 ppdev,lp,parport_pc
crc_ccitt               2240  1 irda
joydev                 10432  0 
pcspkr                  2244  0 
floppy                 64676  0 
tsdev                   8032  0 
yenta_socket           30124  5 
rsrc_nonstatic         14624  1 yenta_socket
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
sis900                 25152  0 
mii                     6176  1 sis900
snd_intel8x0           35772  1 
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
psmouse                40004  0 
snd_pcm_oss            56448  0 
snd_mixer_oss          20544  1 snd_pcm_oss
serio_raw               7748  0 
i2c_sis96x              5860  0 
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
i2c_core               22848  2 i2c_acpi_ec,i2c_sis96x
snd                    60004  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
shpchp                 49504  0 
pci_hotplug            30788  1 shpchp
sis_agp                 9028  1 
agpgart                36784  1 sis_agp
evdev                  10176  1 
ext3                  148104  2 
jbd                    65876  1 ext3
ide_generic             1504  0 
ohci1394               37524  0 
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0 
ohci_hcd               22724  0 
usbcore               139076  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 35780  0 
cdrom                  41408  2 sr_mod,ide_cd
ide_disk               19136  4 
sis5513                17320  1 
generic                 5124  0 
thermal                13768  0 
processor              26888  1 thermal
fan                     4836  0 
capability              4968  0 
commoncap               7328  1 capability
vga16fb                13992  1 
vgastate               10208  1 vga16fb
fbcon                  43904  72 
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```

Any suggestions?

Brian

> **Original Brownster said:**
> Hi,
With USB on in the bios the interrupt count on irq10 looks real low. Its a hunch but try and unload the sound module 'SiS SI7012', you may need to look as 'lsmod' to find the correct module name. 
If this doesn't work, try removing the 'ehci' module too, 
if it still doesnt work, turn usb off in the bios then unload the modules again. 
It maybe that the interrupt count we are seeing is not for the usb device but the sound card. 
In an ideal world these should all just get along dandy but stranger things have happened.

Cheers

---

### Post by Original Brownster on 2006-08-19
Hi,
You could blacklist them temporarily so the modules do not load at boot up.
Put the module names in the /etc/modprobe.d/blacklist file (you had the right modules, all that start snd_ . maybe take a copy before you edit the file then just put the original back after you've tested it.

Alternatively it might be easier to disable sound in the bios if the option is present of course.

Cheers,

---

### Post by br77 on 2006-08-19
OK, now I think we're getting somewhere. With USB BIOS support on and all of the sound modules blacklisted, this is the output of cat /proc/interrupts:

```

           CPU0       
  0:      31526          XT-PIC  timer
  1:        117          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:       6221          XT-PIC  ohci1394, yenta, yenta, ath0
  7:          2          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:         19          XT-PIC  acpi
 10:          0          XT-PIC  ohci_hcd:usb1, ohci_hcd:usb2, ohci_hcd:usb3
 11:          0          XT-PIC  ehci_hcd:usb4
 12:       2336          XT-PIC  i8042
 14:       6099          XT-PIC  ide0
 15:       1534          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

```

No increase in irq 10. USB devices still didn't work, even with the ehci module removed.

Here's one more possible kink: I've been having problems with ACPI (suspend does not resume, the fan does not shut off, cstate 3 is not available, the fully charged battery is drained within a minute or so, and acpi -t says that the temp is 75 C and never reports a change). In working on this problem, I've discovered that I don't have a /proc/acpi/processor/CPU0/ dir (it's CPU1). Do you think that it's a problem that /proc/interrupts lists the cpu as CPU0? Is it looking in the wrong place?

Thanks,
Brian

> **Original Brownster said:**
> Hi,
You could blacklist them temporarily so the modules do not load at boot up.
Put the module names in the /etc/modprobe.d/blacklist file (you had the right modules, all that start snd_ . maybe take a copy before you edit the file then just put the original back after you've tested it.

Alternatively it might be easier to disable sound in the bios if the option is present of course.

Cheers,

---

### Post by Original Brownster on 2006-08-20
Hi,
I think the problems with acpi maybe related as you said, I found this thread about [URL="http://forums.gentoo.org/viewtopic.php?t=122145"]
ACPI problems[/URL]
I'm not sure if this does effect usb or not but it sure looks possible to me.

Have a read and see what you think, I'm afraid it's not something I have had to do before but the guy has some good advice and explains how to test for the faults he describes. 

One other thought, with the blacklisted modules, what does passing the kernel 'no acpi' and or 'noapic' do? Maybe worth a shot even though it does not fix the acpi problems.

Cheers,

---

### Post by br77 on 2006-08-22
I tried various combinations of noapic, nolapic, and noacpi (I have to use acpi=off to get my kernel to not load those modules... I thought that dapper was pci=noacpi or just noacpi) with the sound modules blacklisted and saw no improvement. IRQ 10 remains silent; no usb devices register. Incidentally, irq 10 goes wild when I play music or some other sound, not surprisingly.

Well, I think that I'm going to spend some time on the acpi issue. I think that it's more important that acpi is registering the correct temp and can bring the computer down to state C3 than being able to get pictures off of our Nikon D50 (though my wife, whose computer this is, may not agree).

I checked out that forum and followed that guy's instructions for finding out if there is a problem with DSDT. Although mine is compiled by Microsoft, it produced no errors (only one warning). More shocking, I think, is that when I did dmesg |grep ACPI, there's a line that said that the DSDT was not found. Maybe getting DSDT to be found will be the magic solution to all of my problems.

I'd like to post updates for any future sufferers of this ailment, but this thread may not be the proper forum. Maybe I'll create a new thread if I make any progress.

Thanks for all your help!
Brian

> **Original Brownster said:**
> Hi,
I think the problems with acpi maybe related as you said, I found this thread about [URL="http://forums.gentoo.org/viewtopic.php?t=122145"]
ACPI problems[/URL]
I'm not sure if this does effect usb or not but it sure looks possible to me.

Have a read and see what you think, I'm afraid it's not something I have had to do before but the guy has some good advice and explains how to test for the faults he describes. 

One other thought, with the blacklisted modules, what does passing the kernel 'no acpi' and or 'noapic' do? Maybe worth a shot even though it does not fix the acpi problems.

Cheers,

---

### Post by gadean on 2006-08-23
I'm experiencing the exact same problems.  I've been watching this thread closely hoping to find an answer.  Still no luck!

---

### Post by Original Brownster on 2006-08-23
Hi,
One other avenue to explore is a bios upgrade, not something I'd recommend normally but in this case it's a possibility. Perhaps checking with the manufacturer site for your model might uncover an upgrade along with notes on what the upgrade fixes.




> **br77 said:**
> I tried various combinations of noapic, nolapic, and noacpi (I have to use acpi=off to get my kernel to not load those modules... I thought that dapper was pci=noacpi or just noacpi) with the sound modules blacklisted and saw no improvement. IRQ 10 remains silent; no usb devices register. Incidentally, irq 10 goes wild when I play music or some other sound, not surprisingly.

Well, I think that I'm going to spend some time on the acpi issue. I think that it's more important that acpi is registering the correct temp and can bring the computer down to state C3 than being able to get pictures off of our Nikon D50 (though my wife, whose computer this is, may not agree).

I checked out that forum and followed that guy's instructions for finding out if there is a problem with DSDT. Although mine is compiled by Microsoft, it produced no errors (only one warning). More shocking, I think, is that when I did dmesg |grep ACPI, there's a line that said that the DSDT was not found. Maybe getting DSDT to be found will be the magic solution to all of my problems.

I'd like to post updates for any future sufferers of this ailment, but this thread may not be the proper forum. Maybe I'll create a new thread if I make any progress.

Thanks for all your help!
Brian

Good luck, let us know how it goes.

---

### Post by xens on 2007-03-28
I've got the same problem. I upgraded to the last BIOS and Controller version but the problem's still here. I opened a bug there: [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94540](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94540)

See you

Romain

---

