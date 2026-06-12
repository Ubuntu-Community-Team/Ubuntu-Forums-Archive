---
title: "1TB external drive was NOT unmounted, now can't mount"
date: 2009-10-16
forum: Hardware
---

### Post by db4elle on 2009-10-16
Hey everyone!

I'm new to linux, and didn't realize how important it is to unmount external drives before unplugging. When I unplugged drives in windows (vista) the worst that ever happened was it recognized the drive was removed incorrectly, asked to be repaired (to which I would say yes), and then after some time it would be back to normal. 

The other day I was reading an excel file off my NTFS 1TB SimpleTech usb drive, and a friend pulled the usb connection unaware of the consequences. Now I can't mount the drive anymore in ubuntu, and windows. Luckily, I DID backup the contents of the drive (my Masters thesis data...) onto another 1TB drive to which I still have access, but I would like to make this drive useable again, and preferably without losing the data on it.

Please, any and all help is very much appreciated! Thank you in advance!

I've seen people asking for outputs of some diagnostic commands so I list them here:

Output to fdisk -l:

```
andrzej@andrzej-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64472ecd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         191     1534176   27  Unknown
/dev/sda2            4294       30401   209712510    5  Extended
/dev/sda4             192        1144     7654972+  17  Hidden HPFS/NTFS
/dev/sda5            4294        8209    31455238+  83  Linux
/dev/sda6            8210       29748   173011986   83  Linux
/dev/sda7           29749       30401     5245191   82  Linux swap / Solaris

Partition table entries are not in disk order

```Output from ls /dev/sd*
```
andrzej@andrzej-laptop:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda4  /dev/sda5  /dev/sda6  /dev/sda7

```Output from tail -f /var/log/messages
```
andrzej@andrzej-laptop:~$ tail -f /var/log/messages
Oct 16 17:41:17 andrzej-laptop kernel: [ 2953.289482] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1
Oct 16 17:46:45 andrzej-laptop kernel: [ 3281.444159] usb 1-2: new full speed USB device using uhci_hcd and address 10
Oct 16 17:46:45 andrzej-laptop kernel: [ 3281.594177] usb 1-2: configuration #1 chosen from 1 choice
Oct 16 18:12:21 andrzej-laptop -- MARK --
Oct 16 18:32:21 andrzej-laptop -- MARK --
Oct 16 18:36:25 andrzej-laptop kernel: [ 6261.424142] usb 1-2: USB disconnect, address 10
Oct 16 18:52:21 andrzej-laptop -- MARK --
Oct 16 18:58:56 andrzej-laptop kernel: [ 7612.468131] usb 1-2: new full speed USB device using uhci_hcd and address 11
Oct 16 18:58:56 andrzej-laptop kernel: [ 7612.616035] usb 1-2: configuration #1 chosen from 1 choice
Oct 16 19:01:42 andrzej-laptop kernel: [ 7777.915729] loop: module loaded

```Output from dmesg
```
andrzej@andrzej-laptop:~$ dmesg
[ 7612.468131] usb 1-2: new full speed USB device using uhci_hcd and address 11
[ 7612.616035] usb 1-2: configuration #1 chosen from 1 choice
[ 7777.915729] loop: module loaded
[ 8218.287393] ------------[ cut here ]------------
[ 8218.287405] WARNING: at /build/buildd/linux-2.6.27/drivers/net/wireless/iwlwifi/iwl-tx.c:1196 iwl_tx_cmd_complete+0x117/0x120 [iwlcore]()
[ 8218.287412] wrong command queue 63, command id 0x0
[ 8218.287416] Modules linked in: loop ipv6 nls_iso8859_1 nls_cp437 vfat fat usb_storage libusual af_packet i915 drm binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_ondemand cpufreq_conservative cpufreq_powersave cpufreq_stats freq_table cpufreq_userspace sbs container pci_slot sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport joydev snd_hda_intel snd_pcm_oss arc4 snd_mixer_oss ecb snd_pcm snd_seq_dummy crypto_blkcipher uvcvideo snd_seq_oss iwlagn psmouse iwlcore compat_ioctl32 videodev serio_raw pcspkr snd_seq_midi v4l1_compat evdev rfkill snd_rawmidi snd_seq_midi_event led_class snd_seq mac80211 sdhci_pci sdhci snd_timer snd_seq_device cfg80211 mmc_core snd iTCO_wdt iTCO_vendor_support soundcore shpchp pci_hotplug snd_page_alloc video output wmi intel_agp button battery ac agpgart ext3 jbd mbcache sr_mod cdrom pata_acpi sd_mod crc_t10dif sg ata_piix usbhid hid ata_generic ahci ohci1394 libata ieee1394 scsi_mod dock sky2 uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse [last unloaded: ehci_hcd]
[ 8218.287602] Pid: 6642, comm: Xorg Not tainted 2.6.27-14-generic #1
[ 8218.287608]  [<c0132f05>] warn_slowpath+0x65/0x90
[ 8218.287624]  [<c0236685>] ? apparmor_socket_recvmsg+0x15/0x20
[ 8218.287634]  [<c02e79e6>] ? __sock_recvmsg+0x66/0x80
[ 8218.287643]  [<c02e7adc>] ? sock_aio_read+0xdc/0x120
[ 8218.287653]  [<f8c70167>] iwl_tx_cmd_complete+0x117/0x120 [iwlcore]
[ 8218.287674]  [<f8ca6df9>] iwl_rx_handle+0xd9/0x260 [iwlagn]
[ 8218.287689]  [<f8ca8fed>] iwl4965_irq_tasklet+0x1ad/0x320 [iwlagn]
[ 8218.287701]  [<c01e3aae>] ? inotify_inode_queue_event+0xe/0xe0
[ 8218.287711]  [<c01383f8>] tasklet_action+0x78/0x100
[ 8218.287718]  [<c0138822>] __do_softirq+0x92/0x120
[ 8218.287725]  [<c013890d>] do_softirq+0x5d/0x60
[ 8218.287731]  [<c0138a85>] irq_exit+0x55/0x90
[ 8218.287738]  [<c0106c1a>] do_IRQ+0x4a/0x80
[ 8218.287745]  [<c01b3f52>] ? sys_read+0x42/0x70
[ 8218.287754]  [<c0105003>] common_interrupt+0x23/0x30
[ 8218.287762]  =======================
[ 8218.287766] ---[ end trace 3c56333cdc3d8cd8 ]---

```Output from blkid
```
andrzej@andrzej-laptop:~$ sudo blkid
/dev/sda1: UUID="3A6E6E9B6E6E4FA5" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda4: UUID="1E1E76BC1E768C91" LABEL="HDDRECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="c81507be-bc99-4484-841a-05cb7f16c4c3" TYPE="ext3" 
/dev/sda6: UUID="a77d5403-c19c-40a0-9b06-447397bc55af" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="6afacf4a-86fe-4a6e-9d3d-5314ae607af0" 
```

---

### Post by stinger30au on 2009-10-16
out of interest if you plug it in to a vista machine what happens?
does it try to reapir it again??

---

### Post by db4elle on 2009-10-16
> **stinger30au said:**
> out of interest if you plug it in to a vista machine what happens?
does it try to reapir it again??


Thanks for the quick reply! I tried plugging it into two seperate XP machines, and each time it 'looks for driver to install new hardware device' and fails. Did the exact same thing with a Vista machine...

Normal behaviour used to be immediately recognized as USB mass storage 'SimpleTech' drive....no searching for drivers necessary, but something must've gotten screwed up when the plug was pulled...

I'm trying to find solved threads involving 'unplugging NTFS before unmounting' but can't really find anything useful...surely I can't be the only one....?

---

### Post by db4elle on 2009-10-16
Ok, well I officially have NO idea what happened...earlier today when I tried the drive on 2 xp boxes and a Vista box it couldn't find drivers for the hardware device....

after replying to your message I thought that since I had nothing to lose, I would try on another xp box AGAIN....and it worked fine :confused:

so I did a 'Safely Remove' and plugged it back into my ubuntu laptop; got this error:

'Unable to mount SimpleDrive'
```
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```BUT then it just mounted itself and worked....

So in essence, I didn't do anything (except try ANOTHER xp box) and it worked.

Anyone care to comment?

---

### Post by Vague Rant on 2009-10-17
I'd recommend a file (system) recovery tool such as [TestDisk](http://www.cgsecurity.org/wiki/TestDisk). It may or may not be able to restore the drive to working order without having to format it (through, e.g. rewriting the boot sector), but even if it can't you may be able to copy at least some of the data to another drive.

---

