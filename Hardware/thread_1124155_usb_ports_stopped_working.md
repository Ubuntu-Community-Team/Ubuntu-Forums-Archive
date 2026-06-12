---
title: "usb ports stopped working"
date: 2009-04-13
forum: Hardware
---

### Post by nshailesh on 2009-04-13
I am using ubuntu on a dual boot system with windows xp.
My usb ports suddenly stopped working .
They do not recognize any usb device on both the systems.

Looking at other related forums I tried following commands .

lsusb
dmesg | grep -i usb (or grep usb)
dmesg | grep -i hci

But they didn't show anything.

Also there is no such directory like /usb in /sys/bus so no file like sys/bus/usb/devices/5-8.4.1/power/level.


ls /sys/bus shows 

ac97  eisa  isa  pci          platform  scsi   spi
acpi  i2c   MCA  pci_express  pnp       serio

---

### Post by schmidtbag on 2009-04-13
check if its disabled in bios.  key terms you should look for is peripheral, south bridge, integrated, or onboard.  i'm not sure why both linux and windows can't find it but its definitely caused by the drivers disabled

---

### Post by nshailesh on 2009-04-13
but how to check peripheral etc .
If it's a driver problem where can I get the drivers for intel 845 gvsr motherboar.
Also reinstalling any of the os does not work.

---

### Post by schmidtbag on 2009-04-13
what?  i said turn it on in bios, just look for it.  i said that its probably disabled and the only way to check from an OS is lsmod or lshal.  if 2 different OSes have a problem with it then theres clearly not a driver issue and reinstalling was a waste of time.  check bios first

---

### Post by nshailesh on 2009-04-14
I did lsmod as well as lshal.
I don't know what entry is there for usb exactly in the kernel modules

I did grep usb and grep ehci on both the commands .They showed nothing.


Below is the output of lsmod.
I could not display lshal output because of the forum restrictions.

Thanks.....



lsmod shows:

Module                  Size  Used by
xt_TCPMSS               5504  1 
xt_tcpmss               3200  1 
xt_tcpudp               4096  1 
iptable_mangle          3712  1 
pppoe                  14528  2 
pppox                   4876  1 pppoe
i915                   32512  2 
drm                    82580  3 i915
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
af_packet              23812  2 
ppp_generic            29588  6 pppoe,pppox
slhc                    7040  1 ppp_generic
iptable_filter          3840  0 
ip_tables              14820  2 iptable_mangle,iptable_filter
x_tables               16132  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
vfat                   14464  0 
fat                    54556  1 vfat
ac                      6916  0 
lp                     12324  0 
ipv6                  267780  10 
parport_pc             36260  1 
parport                37832  2 lp,parport_pc
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
evdev                  13056  3 
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
psmouse                40336  0 
serio_raw               7940  0 
pcspkr                  4224  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
button                  9232  0 
i2c_i810                5636  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_algo_bit            7300  1 i2c_i810
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  3 drm,intel_agp
i2c_core               24832  2 i2c_i810,i2c_algo_bit
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
floppy                 59588  0 
ata_piix               19588  2 
ata_generic             8324  0 
e100                   37388  0 
mii                     6400  1 e100
libata                159344  3 pata_acpi,ata_piix,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3

---

### Post by schmidtbag on 2009-04-14
Actually I'm not 100% sure if lsmod shows the USB controller, but it should show all USB devices.  If you can't post lshal and you didn't find anything usb related in it, then like i said, its disabled in bios.  the only other way to prove this is to go into windows, open up device manager, and see if theres a USB section.  it should have its own category.  if you really have no idea how to fix usb in bios then in bios, select "load optimal settings".  this is usually either on the main page or the last page, but if your bios was being messed with in any way, that should reset it.

---

### Post by nshailesh on 2009-04-14
I checked lsmod from other computer .
It shows many entries for usb.

I also troubleshooted in xp .
There is generally a usb or ehci controller in the device manager
but it is not there in my xp.

I will see the bios settings.

---

### Post by schmidtbag on 2009-04-14
yes, like i said about 4 times, find it in bios or reset cmos.  do you not know what bios is?

---

### Post by nshailesh on 2009-04-14
ya , i will see It 
Thanks

---

### Post by yayakhaled on 2009-04-20
hi everyone,
 I have similar problem !! USB is not working for some reason, But with Xp its ok!
After plugging a USB memory stick or external hardisk, Nothing happens at all on the system (ubuntu) however, the usb LED seems to fash and for the case of HD it goes on (power ok).

I've check the devices using fdisk -l, I got the following

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       14593    86501992+   f  W95 Ext'd (LBA)
/dev/sda5            3825        9215    43303176    7  HPFS/NTFS
/dev/sda6            9216       12691    27920938+   7  HPFS/NTFS
/dev/sda7           12692       14507    14586988+  83  Linux
/dev/sda8           14508       14593      690763+  82  Linux swap / Solaris


All these are internal drives, After I plug USB device I still get the same table. It doesn't recognize any usb device.

However, If I really keep the USB device connected for a pretty long time, it works as normal. Also, sometimes the whole problem vanish and it functions normally.

I'm running Ubuntu Desktop on my portege A100 toshiba laptop.

Any one could give me clue?

---

### Post by krustybaguette on 2011-02-21
> **nshailesh said:**
> I checked lsmod from other computer .
It shows many entries for usb.

I also troubleshooted in xp .
There is generally a usb or ehci controller in the device manager
but it is not there in my xp.

I will see the bios settings.


BIOS could be involved. While trying to get my sound working in xubuntu 10.10 on a PIII Toshiba Portege I changed BIOS setting for peripherals from "all devices" to "setup by OS". Lo and behold when I rebooted I had my sound working, but as a side effect all my usb devices. Back into BIOS and changed the setting back. After rebooting, sound still works and all my usb devices too  :D:D

It's easy enough to try it to see if it works;)

---

### Post by cariboo on 2011-02-21
@krustybaguette

this thread is almost 2 years old, and the poster you replied to hasn't been back since he posted. This thread is closed.

---

