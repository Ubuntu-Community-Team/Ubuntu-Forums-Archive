---
title: "prism2_cs card not working"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by drwhom on 2005-08-05
Good morning,
I have a Dell Latitude LS laptop.  I am not being successfull at the kernel connecting to the Proxim 8430 wireless card.  I believe the kernel sees it, but just can't connect.
I tried sudo apt-get install build-essential linux-headers-`uname -r` and received:

build-essential is already the newest version.
E: Version '2.6.8.1-5-386' for 'linux-headers' was not found

Also, last night, at the local LUG a sysadmin, had a go at it for several hours.  We noticed the modules for this card weren't there.  We downloaded 2.6.8.12.3 to compile (that's giving me compiling errrors as well).  We did notice a module was missing.  But, I can't 'make' or 'make modules_install'. 

Thank you for any help,
Dr Whom

---

### Post by stanwebber on 2005-08-05
try using the orinoco_cs or hostap_cs driver.  also consider upgrading the firmware on your card, see [http://linux.junsun.net/intersil-prism](http://linux.junsun.net/intersil-prism) or [cached](http://rds.yahoo.com/S=2766679/K=prism+firmware/v=2/SID=e/TID=F582_123/l=WS5/R=4/;_ylt=AkkYmqaOcSFt6Af31DIxLpZXNyoA/SIG=15to2tm49/EXP=1123339057/*-http%3A//216.109.125.130/search/cache?p=prism+firmware&sm=Yahoo%21+Search&toggle=1&ei=UTF-8&u=linux.junsun.net/intersil-prism/&w=prism+firmware&d=B071145933&icp=1&.intl=us)

---

### Post by az on 2005-08-05
Okay, are you running Warty?  The 2.6.8 kernel is in Warty and the 2.6.10 kernel is in Hoary.

Open a terminal and do
sudo tail -f /var/log/messages

and then plug in the card for the first time.  If it is a prism_cs chipset, the orinoco_cs driver should be loaded by hotplug.  The orinoco driver is equivalent to the prism2 drivers, so just use that.  It should not be neccessary to recompile any modules.


Show the output of that tail...

---

### Post by drwhom on 2005-08-05
When I bought my used laptop it did not, at that time, have a cd rom.  So I installed Ubuntu to the laptop's HD using my dekstop machine.  I wonder if this is a hangup?

When I boot I receive this error:
modprobe FATAL error inserting shpchp lib/modules/2.6.8.1-5-386/kernel/drivers/pci/hotplug/shpchp.ko
Could this, too, be a factor?

I want to wait on flashing the card till the last resort 

modprobe prism2_cs and hostap_cs are not found.  modprobe orinoco_cs doesn't tell me if it's found or not. ](*,) 

Dr Whom

---

### Post by drwhom on 2005-08-05
Okay Azz, here it is:

root@liGNUx:/home/kevin # sudo tail -f /var/log/messages
Aug  5 10:18:02 localhost kernel: cs: IO port probe 0x0800-0x08ff: clean.
Aug  5 10:18:02 localhost kernel: cs: IO port probe 0x0c00-0x0cff: clean.
Aug  5 10:18:02 localhost kernel: cs: IO port probe 0x0a00-0x0aff: clean.
Aug  5 10:18:05 localhost kernel: acpi: Unknown symbol acpi_processor_unregister_performance
Aug  5 10:18:05 localhost kernel: acpi: Unknown symbol acpi_processor_register_performance
Aug  5 10:18:36 localhost gconfd (kevin-3472): starting (version 2.8.1), pid 3472 user 'kevin'
Aug  5 10:18:36 localhost gconfd (kevin-3472): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  5 10:18:36 localhost gconfd (kevin-3472): Resolved address "xml:readwrite:/home/kevin/.gconf" to a writable configuration source at position 1
Aug  5 10:18:36 localhost gconfd (kevin-3472): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  5 10:19:06 localhost gconfd (kevin-3472): Resolved address "xml:readwrite:/home/kevin/.gconf" to a writable configuration source at position 0
Aug  5 10:20:55 localhost kernel: cs: memory probe 0xa0000000-0xa0ffffff: clean.

---

### Post by az on 2005-08-05
Is pcmcia-cs installed

(look in synaptic)

---

### Post by drwhom on 2005-08-05
The following are:

pcmcia-source
pcmcia-cs
pcmcia-module 2.4.26-1-386 3.2.5+1

---

### Post by az on 2005-08-05
"pcmcia-module 2.4.26-1-386 3.2.5+1"

?



How did you install this system?

Also, what is the output of lspci and lsmod?

---

### Post by drwhom on 2005-08-05
I installed from the packaged disks.  I went crazy installing anything pcmcia in an effort to get the wifi running.

The following are the lsmod and lspci after a reboot and I pushed the card in.

lsmod:
root@liGNUx:/home/kevin # lsmod
Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ds                     17796  2
ipv6                  230148  8
af_packet              20872  2
snd_nm256              69032  3
snd_ac97_codec         59268  1 snd_nm256
snd_pcm_oss            48296  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_nm256,snd_pcm_oss
snd_page_alloc         11144  1 snd_pcm
snd_timer              23300  1 snd_pcm
snd                    50660  8 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
3c59x                  36776  0
yenta_socket           19328  1
pcmcia_core            63156  2 ds,yenta_socket
uhci_hcd               29328  0
usbcore               104292  3 uhci_hcd
pci_hotplug            30640  0
intel_agp              20512  1
agpgart                31784  1 intel_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
joydev                  9536  0
evdev                   9216  1
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
sd_mod                 20480  0
scsi_mod              115148  1 sd_mod
ext3                  109672  1
jbd                    54680  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   26160  790
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
root@liGNUx:/home/kevin #

lspci:
root@liGNUx:/home/kevin # lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1211
0000:00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:00:10.0 Communication controller: Lucent Microelectronics WinModem 56k (rev 01)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)
root@liGNUx:/home/kevin #

---

### Post by drwhom on 2005-08-06
Okay -- I decided to reinstall Ubuntu.  Still, it says:
modprobe FATAL error inserting shpchp lib/modules/2.6.8.1-5-386/kernel/drivers/pci/hotplug/shpchp.ko

I am unsure if this is a necessary component for wifi.

Kevin

---

