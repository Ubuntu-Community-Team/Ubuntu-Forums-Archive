---
title: "USB Not Mounting Correctly?"
date: 2010-08-13
forum: Hardware
---

### Post by Thomas_Bates on 2010-08-13
I purchased [this watch](http://www.thinkgeek.com/computing/thumb-drives-storage/9771/) from ThinkGeek, but it does not seem to mount correctly for me. Considering the driver included on the disk is for Windows 98, I think possibly the system is just old.
It is apparently called a Mega Memory Watch, and its system requirements are as follows:
> Windows 98 SE
Windows ME
Windows 2000
Windows XP
Linux 2.4 or higher
Mac OS 9.0 or higher

I'm running Ubuntu 10.04, so I do meet those requirements. It mounts for a few moments if it is inserted at boot, but disappears after a few seconds.

I looked around in Terminal:

> thomas@thomas-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
isofs                  29250  1 
vfat                    8933  0 
udf                    78785  0 
fat                    47767  1 vfat
crc_itu_t               1371  1 udf
aes_i586                7268  1091 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
vboxdrv               190441  0 
snd_hda_codec_realtek   203310  1 
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  7 
ipt_addrtype            1631  4 
xt_state                1098  7 
snd_hda_intel          21941  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ip6table_filter         2343  1 
ip6_tables             11227  1 ip6table_filter
snd_seq_dummy           1338  0 
nf_nat_irc              1124  0 
snd_seq_oss            26726  0 
nf_conntrack_irc        3332  1 nf_nat_irc
snd_seq_midi            4557  0 
nf_nat_ftp              1836  0 
snd_rawmidi            19056  1 snd_seq_midi
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack           61583  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          2271  1 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables               9991  1 iptable_filter
x_tables               14299  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
joydev                  8708  0 
snd                    54148  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
nvidia               9961216  28 
agpgart                31724  1 nvidia
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
usb_storage            39425  0 
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
forcedeth              49556  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
pata_amd                8766  0 
ahci                   32168  5 
thomas@thomas-desktop:~$ modprobe usb_storage
thomas@thomas-desktop:~$ tail -s 3 -f /var/log/messages
Aug 13 15:36:14 thomas-desktop kernel: [ 1146.416064] usb 1-5: USB disconnect, address 10
Aug 13 15:36:14 thomas-desktop kernel: [ 1146.416190] scsi 8:0:0:0: Device offlined - not ready after error recovery
Aug 13 15:36:14 thomas-desktop kernel: [ 1146.528032] usb 1-5: new high speed USB device using ehci_hcd and address 11
Aug 13 15:36:25 thomas-desktop kernel: [ 1157.196033] usb 1-5: new high speed USB device using ehci_hcd and address 12
Aug 13 15:36:36 thomas-desktop kernel: [ 1167.860045] usb 1-5: new high speed USB device using ehci_hcd and address 13
Aug 13 15:36:41 thomas-desktop kernel: [ 1173.408043] usb 1-5: new high speed USB device using ehci_hcd and address 14
Aug 13 15:36:47 thomas-desktop kernel: [ 1179.304059] usb 2-5: new full speed USB device using ohci_hcd and address 9
Aug 13 15:36:58 thomas-desktop kernel: [ 1190.048028] usb 2-5: new full speed USB device using ohci_hcd and address 10
Aug 13 15:37:08 thomas-desktop kernel: [ 1200.796031] usb 2-5: new full speed USB device using ohci_hcd and address 11
Aug 13 15:37:14 thomas-desktop kernel: [ 1206.380039] usb 2-5: new full speed USB device using ohci_hcd and address 12



It seems to be detecting it every few seconds, and reassigning it.

I paid $40 for the watch, and I would love if it worked. Does anyone have any advice?

I should also note that all other USB devices mount correctly, including my keyboard, my wireless mouse, USB Flash drive, and my External. This one is the only thing which is having an issue.

---

### Post by Thomas_Bates on 2010-08-13
In install directions, it says this:

> 4. Linux Kernel 2.4 or up
i. Start up your computer
ii. Get into the root directory of your computer OS system
iii. Plug the USB drive into a USB port of the computer
iv. For installing the USB drive, please enter “mount/dev/sda1/mnt”
v. For uninstalling the USB drive, please enter “umount/mnt”


Production of that command:

> thomas@thomas-desktop:~$ mount/dev/sda1/mnt
bash: mount/dev/sda1/mnt: No such file or directory


---

### Post by Thomas_Bates on 2010-08-13
Excuse my idiocy, I left out spaces.


thomas@thomas-desktop:~$ sudo mount /dev/sda1 /mnt
thomas@thomas-desktop:~$ 

However, 


thomas@thomas-desktop:/media$ ls
cdrom  cdrom0  usb  usb0  usb1  usb2  usb3  usb4  usb5  usb6  usb7
thomas@thomas-desktop:/media$ 

cdrom and cdrom0 are both the same. usb and usb0 are the same. usbx all show as containing nothing, and having just short of 300 GB of space, so obviously not a flash drive.

---

### Post by earthpigg on 2010-08-13
well, a USB mass storage device is a USB mass storage device.

have you tried it on any other computers, linux or otherwise? you may have gotten a defective unit.

---

### Post by Thomas_Bates on 2010-08-14
Yes, I tried it on Windows. It does work, plug-and-play.

It is a driver error. I've attempted to install the driver via ndiswrapper. However, having no experience with the system, I'm unsure of my success:

> thomas@thomas-desktop:~$ cd ~/Desktop/Driver-USB/
thomas@thomas-desktop:~/Desktop/Driver-USB$ ndiswrapper -i Umss.inf
couldn't create /etc/ndiswrapper/umss: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194.
thomas@thomas-desktop:~/Desktop/Driver-USB$ sudo ndiswrapper -i Umss.inf
[sudo] password for thomas: 
installing umss ...
thomas@thomas-desktop:~/Desktop/Driver-USB$ ndiswrapper -l
netmw245 : driver installed
umss : driver installed
thomas@thomas-desktop:~/Desktop/Driver-USB$ ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
sh: cannot create /etc/modprobe.d/ndiswrapper: Permission denied
couldn't add module alias:  at /usr/sbin/ndiswrapper-1.9 line 882.



> thomas@thomas-desktop:/media/cdrom0/CBUMSS$ ndiswrapper -l
netmw245 : driver installed
umss : driver installed
thomas@thomas-desktop:/media/cdrom0/CBUMSS$ ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

thomas@thomas-desktop:/media/cdrom0/CBUMSS$ modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
thomas@thomas-desktop:/media/cdrom0/CBUMSS$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


---

### Post by Thomas_Bates on 2010-08-14
I believe the problem is actually on my computer, rather than the drive.

On a whim, I plugged it into my laptop (which also runs Ubuntu 10.04), and it runs, perfectly.

I am now at a loss of what to do, does anyone know what could be causing my desktop to be ignoring this specific device?

---

### Post by Thomas_Bates on 2010-08-14
I compared the two /media folders, between my laptop and my desktop.

Desktop:


thomas@thomas-desktop:/media$ ls
cdrom   FreeAgent Drive  usb0  usb2  usb4  usb6
cdrom0  usb              usb1  usb3  usb5  usb7
thomas@thomas-desktop:/media$ 

FreeAgent Drive is my external, and a few of these are actually the same thing.

Laptop:

CB06-EE06 cdrom cdrom0

CB06-EE06 being the flash drive. Why does my desktop have all of the USB folders? I briefly considered that perhaps for each slot there is a folder in media, but that doesn't make sense for an array of reasons. And, if it were true, my laptop should have 3 USB folders.

Any advice?

I've also noticed that I lack permissions for my flash drives now, prior to this, it was not that way.

---

### Post by Thomas_Bates on 2010-08-14
thomas@thomas-desktop:~$ tail -f /var/log/messages
Aug 14 09:03:33 thomas-desktop kernel: [   92.955581] [UFW BLOCK] IN=eth0 OUT= MAC=00:1f:e2:05:ab:66:00:22:b0:ba:d8:fa:08:00 SRC=192.168.0.1 DST=192.168.0.104 LEN=338 TOS=0x00 PREC=0x00 TTL=127 ID=3048 PROTO=UDP SPT=1900 DPT=36509 LEN=318 
Aug 14 09:04:02 thomas-desktop kernel: [  121.877740] usb 2-4.2: reset full speed USB device using ohci_hcd and address 5
Aug 14 09:04:11 thomas-desktop kernel: [  130.650846] scsi 9:0:0:0: Device offlined - not ready after error recovery
Aug 14 09:04:11 thomas-desktop kernel: [  130.659817] usb 2-4.2: USB disconnect, address 5
Aug 14 09:04:26 thomas-desktop kernel: [  145.558945] usb 1-6: USB disconnect, address 5
Aug 14 09:04:32 thomas-desktop kernel: [  151.884037] usb 1-6: new high speed USB device using ehci_hcd and address 7
Aug 14 09:04:32 thomas-desktop kernel: [  152.017872] usb 1-6: configuration #1 chosen from 1 choice
Aug 14 09:04:32 thomas-desktop kernel: [  152.018236] scsi10 : SCSI emulation for USB Mass Storage devices
Aug 14 09:05:08 thomas-desktop kernel: [  187.928038] usb 1-6: reset high speed USB device using ehci_hcd and address 7
Aug 14 09:05:19 thomas-desktop kernel: [  198.596037] usb 1-6: reset high speed USB device using ehci_hcd and address 7
Aug 14 09:05:30 thomas-desktop kernel: [  209.260041] usb 1-6: reset high speed USB device using ehci_hcd and address 7
Aug 14 09:05:35 thomas-desktop kernel: [  214.808043] usb 1-6: reset high speed USB device using ehci_hcd and address 7
Aug 14 09:05:41 thomas-desktop kernel: [  220.244062] usb 1-6: USB disconnect, address 7
Aug 14 09:05:41 thomas-desktop kernel: [  220.244093] scsi 10:0:0:0: Device offlined - not ready after error recovery
Aug 14 09:05:41 thomas-desktop kernel: [  220.356057] usb 1-6: new high speed USB device using ehci_hcd and address 8
Aug 14 09:05:51 thomas-desktop kernel: [  231.024029] usb 1-6: new high speed USB device using ehci_hcd and address 9
Aug 14 09:06:02 thomas-desktop kernel: [  241.684032] usb 1-6: new high speed USB device using ehci_hcd and address 10
Aug 14 09:06:08 thomas-desktop kernel: [  247.232534] usb 1-6: new high speed USB device using ehci_hcd and address 11
Aug 14 09:06:08 thomas-desktop kernel: [  247.955247] [UFW BLOCK] IN=eth0 OUT= MAC=00:1f:e2:05:ab:66:00:22:b0:ba:d8:fa:08:00 SRC=192.168.0.1 DST=192.168.0.104 LEN=338 TOS=0x00 PREC=0x00 TTL=127 ID=3157 PROTO=UDP SPT=1900 DPT=34093 LEN=318 
Aug 14 09:06:08 thomas-desktop kernel: [  247.957108] [UFW BLOCK] IN=eth0 OUT= MAC=00:1f:e2:05:ab:66:00:22:b0:ba:d8:fa:08:00 SRC=192.168.0.1 DST=192.168.0.104 LEN=338 TOS=0x00 PREC=0x00 TTL=127 ID=3158 PROTO=UDP SPT=1900 DPT=54488 LEN=318 
Aug 14 09:06:14 thomas-desktop kernel: [  253.124041] usb 2-6: new full speed USB device using ohci_hcd and address 6
Aug 14 09:06:24 thomas-desktop kernel: [  263.868034] usb 2-6: new full speed USB device using ohci_hcd and address 7
Aug 14 09:06:35 thomas-desktop kernel: [  274.612036] usb 2-6: new full speed USB device using ohci_hcd and address 8
Aug 14 09:06:41 thomas-desktop kernel: [  280.196066] usb 2-6: new full speed USB device using ohci_hcd and address 9


That is after an update/upgrade, as instructed by those on the Ubuntu IRC. Since it is still not working, I've been told to file a bug report.

However, if anyone knows it would be nice.

---

### Post by Thomas_Bates on 2010-08-14
Somehow, Rythmbox was messing with it. Solved now I suppose.

---

