---
title: "Firewire stability issues with Ubuntu on Mac Mini mid 2007 (sbp2_scsi_abort)"
date: 2015-02-05
forum: Hardware
---

### Post by peter_london on 2015-02-05
Hi!

I am new on this forum but not completely new with Linux. I was playing around with Ubuntu years ago. Loved it but ended up going Apple instead. Just recently re-discovered Linux when I realized I need a home server for files, backups, media etc... Took a few days of research and reading but now I got the server up and running the way I planned, and I'm simply having a blast with Linux :).

However, I have an issue with my Firewire interface. A quite serious issue, and to my big surprise, Google doesn't seem to have the answer this time :O.

My Mac Mini has  a few USB 2.0 ports and a Firewire 400 port, so I obviously want to connect all my hard drives to the Firewire port. This works fine at first, but after some time the drives just "disappears", resulting in obvious /IO errors.

I have tried with two different enclosures - same thing. However, connecting only ONE drive seems to work OK. But once I connect another drive, and do some copying between them, either one of them, or both, will "disappear" eventually. I have not found a way yet to restart the firewire bus, so what I do is simply unmount both drives, turn off the power, turn them back on and re-mount them. If I connect the drives via USB instead they run for days without any problems at all.

Since this problem occurs with all the Firewire equipment I currently can test with I suppose there is something on the Mac Mini that's causing problems, or perhaps the 1394 driver in Linux.

I would truly appreciate some help on what to do next here! My setup is kind of useless without Firewire capabilities - running all my drives on USB 2.0 sounds like a nightmare :D.

Some info :

```
$ cat /proc/version
Linux version 3.13.0-24-generic (buildd@batsu) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014
```

```
$ lsmod | grep -e 1394 -e firewire
firewire_sbp2          22665  1 
firewire_ohci          40409  0 
firewire_core          68769  2 firewire_ohci,firewire_sbp2
crc_itu_t              12707  1 firewire_core
```

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
03:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 61)
```

And today's syslog for everything regarding Firewire (I think...). The key seems to be the "sbp2_scsi_abort" as it always appears when I get this error (only happened one time today though).

```
$ cat /var/log/syslog | grep -e 1394 -e firewire
Feb  5 10:51:46 UBServer64bit kernel: [53182.728435] firewire_core 0000:03:03.0: phy config: new root=ffc1, gap_count=5
Feb  5 10:51:49 UBServer64bit kernel: [53185.935303] firewire_core 0000:03:03.0: phy config: new root=ffc1, gap_count=5
Feb  5 10:51:49 UBServer64bit kernel: [53186.247026] scsi23 : SBP-2 IEEE-1394
Feb  5 10:51:49 UBServer64bit kernel: [53186.247143] firewire_core 0000:03:03.0: created device fw1: GUID 0030e101e0020275, S400
Feb  5 10:51:50 UBServer64bit kernel: [53186.477397] firewire_sbp2 fw1.0: logged in to LUN 0000 (0 retries)
Feb  5 11:22:44 UBServer64bit kernel: [55041.293738] firewire_core 0000:03:03.0: phy config: new root=ffc1, gap_count=5
Feb  5 11:22:45 UBServer64bit kernel: [55041.792069] firewire_core 0000:03:03.0: giving up on node ffc2: reading config rom failed: bus reset
Feb  5 11:22:46 UBServer64bit kernel: [55042.632094] firewire_core 0000:03:03.0: rediscovered device fw0
Feb  5 11:22:46 UBServer64bit kernel: [55042.632230] firewire_core 0000:03:03.0: giving up on node ffc0: reading config rom failed: bus reset
Feb  5 11:22:46 UBServer64bit kernel: [55042.632263] firewire_core 0000:03:03.0: phy config: new root=ffc1, gap_count=5
Feb  5 11:22:46 UBServer64bit kernel: [55043.292063] firewire_sbp2 fw1.0: ORB reply timed out, rcode 0x11
Feb  5 11:22:48 UBServer64bit kernel: [55045.292050] firewire_sbp2 fw1.0: ORB reply timed out, rcode 0x11
Feb  5 11:22:51 UBServer64bit kernel: [55047.492053] firewire_sbp2 fw1.0: ORB reply timed out, rcode 0x11
Feb  5 11:22:51 UBServer64bit kernel: [55047.591578] Modules linked in: iptable_filter ip_tables x_tables nls_utf8 hfsplus firewire_sbp2 arc4 ath5k coretemp hid_apple hid_appleir ath applesmc kvm_intel hid_generic mac80211 kvm i915 cfg80211 input_polldev drm_kms_helper snd_hda_codec_idt drm snd_hda_intel usbhid snd_hda_codec i2c_algo_bit snd_hwdep lpc_ich hid snd_pcm snd_page_alloc snd_timer snd soundcore video mac_hid lp parport usb_storage firewire_ohci firewire_core crc_itu_t sky2
Feb  5 11:22:51 UBServer64bit kernel: [55047.955772] scsi26 : SBP-2 IEEE-1394
Feb  5 11:22:51 UBServer64bit kernel: [55047.955891] firewire_core 0000:03:03.0: created device fw2: GUID 0030e101e0020275, S400
Feb  5 11:22:51 UBServer64bit kernel: [55048.000239] firewire_sbp2 fw1.0: released target 23:0:0
Feb  5 11:22:51 UBServer64bit kernel: [55048.185204] firewire_sbp2 fw2.0: logged in to LUN 0000 (0 retries)
Feb  5 11:24:56 UBServer64bit kernel: [55173.216101] firewire_core 0000:03:03.0: rediscovered device fw0
Feb  5 11:24:56 UBServer64bit kernel: [55173.216147] firewire_core 0000:03:03.0: phy config: new root=ffc1, gap_count=5
Feb  5 11:25:00 UBServer64bit kernel: [55176.780202] firewire_sbp2 fw2.0: released target 26:0:0
Feb  5 11:25:01 UBServer64bit kernel: [55178.237963] scsi27 : SBP-2 IEEE-1394
Feb  5 11:25:01 UBServer64bit kernel: [55178.238098] firewire_core 0000:03:03.0: created device fw1: GUID 0030e101e0020275, S400
Feb  5 11:25:02 UBServer64bit kernel: [55178.470724] firewire_sbp2 fw1.0: logged in to LUN 0000 (0 retries)
Feb  5 11:25:21 UBServer64bit kernel: [55198.160200] firewire_sbp2 fw1.0: released target 27:0:0
Feb  5 11:26:04 UBServer64bit kernel: [55240.556075] firewire_core 0000:03:03.0: rediscovered device fw0
Feb  5 11:26:47 UBServer64bit kernel: [55284.164100] firewire_core 0000:03:03.0: rediscovered device fw0
Feb  5 11:29:22 UBServer64bit kernel: [55439.370596] firewire_core 0000:03:03.0: BM lock failed (busy), making local node (ffc0) root
Feb  5 11:29:22 UBServer64bit kernel: [55439.370604] firewire_core 0000:03:03.0: phy config: new root=ffc0, gap_count=5
Feb  5 11:29:26 UBServer64bit kernel: [55442.522660] firewire_core 0000:03:03.0: phy config: new root=ffc1, gap_count=5
Feb  5 11:29:26 UBServer64bit kernel: [55442.886520] scsi29 : SBP-2 IEEE-1394
Feb  5 11:29:26 UBServer64bit kernel: [55442.886664] firewire_core 0000:03:03.0: created device fw1: GUID 0030e101e0020275, S400
Feb  5 11:29:26 UBServer64bit kernel: [55443.119248] firewire_sbp2 fw1.0: logged in to LUN 0000 (0 retries)
Feb  5 11:50:02 UBServer64bit kernel: [56678.916213] firewire_sbp2 fw1.0: released target 29:0:0
Feb  5 11:51:10 UBServer64bit kernel: [56746.404363] firewire_core 0000:03:03.0: phy config: new root=ffc1, gap_count=5
Feb  5 11:51:10 UBServer64bit kernel: [56746.904065] firewire_core 0000:03:03.0: giving up on node ffc0: reading config rom failed: bus reset
Feb  5 11:51:20 UBServer64bit kernel: [56756.682529] firewire_core 0000:03:03.0: phy config: new root=ffc1, gap_count=5
Feb  5 11:51:27 UBServer64bit kernel: [56763.845124] firewire_core 0000:03:03.0: phy config: new root=ffc1, gap_count=5
Feb  5 11:51:27 UBServer64bit kernel: [56764.233376] scsi31 : SBP-2 IEEE-1394
Feb  5 11:51:27 UBServer64bit kernel: [56764.233493] firewire_sbp2 fw1.0: workarounds 0x20 (firmware_revision 0x012804, model_id 0x000001)
Feb  5 11:51:27 UBServer64bit kernel: [56764.233511] firewire_core 0000:03:03.0: created device fw1: GUID 00d0b80e013150de, S400
Feb  5 11:51:28 UBServer64bit kernel: [56764.432764] firewire_sbp2 fw1.0: logged in to LUN 0000 (0 retries)
Feb  5 11:51:31 UBServer64bit kernel: [56768.403711] firewire_core 0000:03:03.0: phy config: new root=ffc2, gap_count=7
Feb  5 11:51:32 UBServer64bit kernel: [56768.901507] firewire_sbp2 fw1.0: reconnected to LUN 0000 (0 retries)
Feb  5 11:51:35 UBServer64bit kernel: [56771.910368] firewire_core 0000:03:03.0: phy config: new root=ffc2, gap_count=7
Feb  5 11:51:35 UBServer64bit kernel: [56771.910790] firewire_sbp2 fw1.0: reconnected to LUN 0000 (0 retries)
Feb  5 11:51:35 UBServer64bit kernel: [56771.911219] firewire_sbp2 fw1.0: reconnected to LUN 0000 (0 retries)
Feb  5 11:51:35 UBServer64bit kernel: [56772.230946] scsi32 : SBP-2 IEEE-1394
Feb  5 11:51:35 UBServer64bit kernel: [56772.231076] firewire_core 0000:03:03.0: created device fw2: GUID 0030e101e0020275, S400
Feb  5 11:51:36 UBServer64bit kernel: [56772.446297] firewire_sbp2 fw2.0: logged in to LUN 0000 (0 retries)
Feb  5 12:25:23 UBServer64bit kernel: [58799.836074] firewire_sbp2 fw1.0: sbp2_scsi_abort
Feb  5 12:25:33 UBServer64bit kernel: [58809.836039] firewire_sbp2 fw1.0: sbp2_scsi_abort
Feb  5 12:25:43 UBServer64bit kernel: [58820.113942] sd 31:0:0:0: rejecting I/O to offline device
Feb  5 12:25:44 UBServer64bit kernel: [58821.113945] sd 31:0:0:0: rejecting I/O to offline device
Feb  5 12:25:46 UBServer64bit kernel: [58823.013949] sd 31:0:0:0: rejecting I/O to offline device
```

Happy to provide any additional info if needed - just let me know!

A million thanks in advance :)

Best regards

Peter

---

### Post by swix on 2015-03-03
It just seems I have exactly the same issue with an intel mac mini and a lacie firewire drive.  I first thought one disk of the array would be broken, but it doesn't seem to be the case.  Have you been able to find a solution in the meantime ?  Otherwise I guess I will have to revert to the slower USB.   

Merci & regards

---

### Post by peter_london on 2015-03-03
Hi swix! Interesting to hear that you have the same problem. I find very little on Google regarding this issue, which surprises me alot. 

I'm curious on what firewire controller you have in your computer?

But nope, I'm still on USB. I currently have two raid enclosures connected to my Mac Mini, and I have a feeling that one of them works better than the other one - which is strange since they both have JMicron chipset for the firewire.

I have tried to find a firmware update for my raid enclosures, but no luck there. Plus I never had a problem connecting them with Firewire to my Macbook running OSX, no matter how much I stress the hard drives :P.

Ultimately, what I want to do is to mod my Mac Mini and install two eSata ports in it, however - I do like Firewire a lot and it would be amazing to get it to work as well.

When I was googling for capturing dv I found one interesting note, this guy (even though due to a completely different issue) reverted to the older Firewire stack (I think...) to get his dv cam to work :

[http://www.wisnaes.com/2010/08/30/capturing-dv-in-kubuntu-linux/](http://www.wisnaes.com/2010/08/30/capturing-dv-in-kubuntu-linux/)

Though my /etc/modprobe.d/blacklist-firewire.conf is already "fixed" :

```

$ cat sudo nano /etc/modprobe.d/blacklist-firewire.conf 
# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.


blacklist ohci1394
blacklist sbp2
blacklist dv1394
blacklist raw1394
blacklist video1394


#blacklist firewire-ohci
#blacklist firewire-sbp2

```

Maybe it could be worth to swap this to :
 
```

# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.


#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394


blacklist firewire-ohci
blacklist firewire-sbp2

```

Haven't had the time to play around with it yet. But it's clearly the "firewire-sbp2" that's been complaining in my logs, so it should be worth to give it a try, perhaps. :).

Best

Peter

---

### Post by tgalati4 on 2015-03-03
Because firewire is a high-speed protocol, it's not unusual that a 7 to 8 year-old computer will have problems maintaining the precise timing required to keep all of the firewire devices in sync.  Perhaps there are timing parameters that you can change in the module options:

> tgalati4@Mint17 ~ $ modinfo firewire-ohci
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/firewire/firewire-ohci.ko
alias:          ohci1394
license:        GPL
description:    Driver for PCI OHCI IEEE1394 controllers
author:         Kristian Hoegsberg <krh@bitplanet.net>
srcversion:     186E69F7C92A63A04DE3EE0
alias:          pci:v*d*sv*sd*bc0Csc00i10*
depends:        firewire-core
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:           **quirks**:Chip quirks (default = 0, nonatomic cycle timer = 0x1, reset packet generation = 0x2, AR/selfID endianness = 0x4, no 1394a enhancements = 0x8, disable MSI = 0x10, TI SLLZ059 erratum = 0x20, IR wake unreliable = 0x40) (int)
parm:           **debug**:Verbose logging (default = 0, AT/AR events = 1, self-IDs = 2, IRQs = 4, busReset events = 8, or a combination, or all = -1) (int)


Perhaps turn on debugging as well.

---

