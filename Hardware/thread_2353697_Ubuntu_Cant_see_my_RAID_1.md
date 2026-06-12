---
title: "Ubuntu Cant see my RAID 1"
date: 2017-02-24
forum: Hardware
---

### Post by katana-9988 on 2017-02-24
Hi guys. I am using two 4TB drives as RAID 1 using the motherboard to have all my data. It is working will with CentOS, But I gess Ubuntu need some tweeking to do.

The information that I got:-

[https://i.stack.imgur.com/SE3Nc.jpg](https://i.stack.imgur.com/SE3Nc.jpg)

```
ahmed@arkan:~$ dmesg | tail
[   14.955111] wlx5cd998c2f547: associated
[   14.955160] IPv6: ADDRCONF(NETDEV_CHANGE): wlx5cd998c2f547: link becomes ready
[   66.537356] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  296.021304] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  314.401983] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  561.931592] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  687.623557] systemd[1]: apt-daily.timer: Adding 7h 41min 2.586014s random time.
[  687.623739] systemd[1]: snapd.refresh.timer: Adding 4h 9min 42.826348s random time.
[  687.623745] systemd[1]: snapd.refresh.timer: Adding 3h 10min 18.720376s random time.
[  687.934658]  sdd: sdd1 < sdd5 >
```


The following is from gparted.

```
Filesystem volume name:   Raid_Data
Last mounted on:          /mnt/f9a8ab95-9996-4978-a656-25c7fe243aa2
Filesystem UUID:          f9a8ab95-9996-4978-a656-25c7fe243aa2
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              244195328
Block count:              976753920
Reserved block count:     48837696
Free blocks:              684664036
Free inodes:              243846930
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      791
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Oct 11 17:56:22 2015
Last mount time:          Fri Feb 24 08:14:43 2017
Last write time:          Fri Feb 24 09:41:51 2017
Mount count:              398
Maximum mount count:      -1
Last checked:             Sun Mar  6 23:46:32 2016
Check interval:           0 (<none>)
Lifetime writes:          1474 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      d9a98f9a-d8d0-4e4a-9661-5db2d45f7c28
Journal backup:           inode blocks
```

```
dumpe2fs 1.42.13 (17-May-2015)
dumpe2fs: Invalid argument while reading journal super block
```

```
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+.
```

I check the Intel Raid Drivers and it is installed.

My guess is that I need to resize the raid 1 partition for it to work with Ubuntu. According to this post.[http://www.linuxquestions.org/questions/linux-general-1/cannot-mount-hard-disk-block-count-exceeds-size-of-device-bad-partition-table-880149/](http://www.linuxquestions.org/questions/linux-general-1/cannot-mount-hard-disk-block-count-exceeds-size-of-device-bad-partition-table-880149/)

Please advice me. I am afraid to do anything to the drive that will wipe out everything I got. 

So please give me the steps so I can read them and copy and past them.

Thanks,

---

### Post by SeijiSensei on 2017-02-24
So let's start from the beginning.  This is a hardware RAID arrangement, not a software RAID made by mdadm?  And it works under CentOS but not on Ubuntu? My guess is that Ubuntu simply isn't loading the required driver.  Run the command "lspci" at a prompt and see what hardware RAID adapter you have.  On a Dell box I manage, we have
```
02:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS (rev 08)
```
If I run the command "lsmod" to display the kernel modules in use I have these:
```

mptsas                 51992  3 
mptscsih               36638  1 mptsas
mptbase                93647  3 mptctl,mptsas,mptscsih
scsi_transport_sas     35588  1 mptsas

```
which correspond to the "SAS" RAID controller. (It appears as a SCSI device, though it really uses SATA to connect to the drives.)

If you can boot into CentOS, run the same commands and see how the results differ from Ubuntu.  The results I posted came from a CentOS installation on the Dell.

---

### Post by katana-9988 on 2017-02-25
This is CentOS 

```
root@arkan-clearos-lan ahmed# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
**_00:1f.2 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 05)_**
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750] (rev a2)
01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
05:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
```

I have removed CentOS and Installed Ubuntu. This is from Ubuntu:-



```
ahmed@arkan:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
**_00:1f.2 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 05)_**
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750] (rev a2)
01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
05:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
ahmed@arkan:~$ 
```


As you can see they both have the drivers. I dont have CentOS now but I did this on Ubuntu

```
ahmed@arkan:~$ lsmod
Module                  Size  Used by
ccm                    20480  2
arc4                   16384  2
rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2800lib,rt2800usb,rt2x00usb
mac80211              761856  3 rt2800lib,rt2x00lib,rt2x00usb
cfg80211              581632  2 rt2x00lib,mac80211
gpio_ich               16384  0
snd_hda_codec_hdmi     45056  1
nvidia_uvm            745472  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
input_leds             16384  0
aesni_intel           167936  4
snd_hda_codec_realtek    86016  1
joydev                 20480  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
ablk_helper            16384  1 aesni_intel
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
intel_cstate           16384  0
intel_rapl_perf        16384  0
snd_hda_intel          36864  5
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_pcm               110592  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    86016  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
mei_me                 40960  0
mei                   102400  1 mei_me
serio_raw              16384  0
shpchp                 36864  0
soundcore              16384  1 snd
lpc_ich                24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
dm_mirror              24576  1
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  3 dm_mirror,dm_region_hash
uas                    24576  0
usb_storage            73728  2 uas
hid_generic            16384  0
usbhid                 53248  0
hid                   122880  2 hid_generic,usbhid
nvidia_drm             16384  1
nvidia_modeset        765952  4 nvidia_drm
drm                   368640  3 nvidia_drm
fjes                   28672  0
nvidia              11489280  59 nvidia_modeset,nvidia_uvm
ahci                   36864  4
libahci                32768  1 ahci
r8169                  81920  0
mii                    16384  1 r8169
ahmed@arkan:~$ 
```

So this is what I got. Just to note, I have taken a full backup from the RAID drives using fedora live CD (the same as CentOS). So I can do whatever without worring on the data. Also, if you need me to boot using CentOS live CD to get some info. Please say so.

Thanks,

---

### Post by SeijiSensei on 2017-02-25
Hmm.  The lsmod output shows the ahci kernel module is loaded which should be the appropriate driver for the Intel device from my brief research on the subject. 

So does Ubuntu see the drives at all?  Sees them as separate devices?

I'm running out of ideas here, so maybe someone else could chime in.

---

### Post by katana-9988 on 2017-02-25
Ubuntu see both. As a separate Devices and one RAID Drive.

How about his? Considering:-

```
[   66.537356] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  296.021304] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  314.401983] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  561.931592] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
```

Can I just fix the bad geometry? I can experiment as I did take the backup.

---

### Post by CharlesA on 2017-02-25
Can you boot off a centos livecd and mount the drive there?

As a sidenote, I have added code tags to your posts with terminal output. It makes it easier to read and you can add them by highlighting to text you want and clicking on the "#" icon in the toolbar on the reply screen.

---

### Post by katana-9988 on 2017-02-25
Yes it is working in CentOS with no issues (even with the latest fedora 25).

---

### Post by katana-9988 on 2017-02-25
Please check this [http://www.linuxquestions.org/questions/linux-general-1/cannot-mount-hard-disk-block-count-exceeds-size-of-device-bad-partition-table-880149/](http://www.linuxquestions.org/questions/linux-general-1/cannot-mount-hard-disk-block-count-exceeds-size-of-device-bad-partition-table-880149/)

It seems that if I fix the file system, it will work using (resize2fs -f /dev/md-0 976753920). Or, I can just Format the drive and it work.

What do you think?

---

### Post by CharlesA on 2017-02-25
Back up your data from the centos or fedora livecd before doing anything with the file systems or partitions.

---

### Post by katana-9988 on 2017-02-27
I have formatted the device, restore the data and it is working well now. I have used the build in utility in application called Disk. <br><br>Thank you so much for your time :D.

---

### Post by ajgreeny on 2017-02-27
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

