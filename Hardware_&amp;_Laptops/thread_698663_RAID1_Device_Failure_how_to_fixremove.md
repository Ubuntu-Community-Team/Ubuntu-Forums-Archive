---
title: "RAID1 Device Failure: how to fix/remove?"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by jsym on 2008-02-16
Hello fellow Ubuntuians,

I hope you can help me--in short, I have a RAID1 device failure wrapped up with some strange inability to login as root.

I have two 160Gb Maxtor Diamonds (I think they are 9s)  in a software RAID1 set-up on my 64-bit desktop machine (This is not fake-RAID although my board, and ASUS A8N-SLI, has that capacity).  Recently one of the drives has started "clicking" a lot and performance has dropped significantly on anything requiring disk access.

Running **dmesg** produces the something like the following, repeated over and over with minor changes each time:
```
[77111.987645] ata6: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0x2 frozen
[77111.987658] ata6: hard resetting port
[77115.859513] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[77115.883896] ata6.00: configured for UDMA/33
[77115.883902] ata6: EH complete
[77115.909312] sd 7:0:0:0: [sde] 320173056 512-byte hardware sectors (163929 MB)
[77115.909539] sd 7:0:0:0: [sde] Write Protect is off
[77115.909542] sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
[77115.940515] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[77115.981815] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0x2 frozen
[77115.981825] ata6.00: cmd c8/00:40:6e:49:1f/00:00:00:00:00/e1 tag 0 cdb 0x0 data 32768 in
[77115.981827]          res ff/ff:ff:ff:ff:ff/ff:ff:ff:ff:ff/ff Emask 0x12 (ATA bus error)
[77115.981835] ata6: hard resetting port
[77119.850961] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[77119.875366] ata6.00: configured for UDMA/33
[77119.875379] ata6: EH complete
[77119.906904] sd 7:0:0:0: [sde] 320173056 512-byte hardware sectors (163929 MB)
[77119.907125] sd 7:0:0:0: [sde] Write Protect is off
[77119.907128] sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
[77119.917981] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[77119.995079] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0x2 frozen
[77119.995090] ata6.00: cmd c8/00:38:16:53:1f/00:00:00:00:00/e1 tag 0 cdb 0x0 data 28672 in
[77119.995091]          res ff/ff:ff:ff:ff:ff/ff:ff:ff:ff:ff/ff Emask 0x12 (ATA bus error)
[77119.995099] ata6: hard resetting port
[77123.866408] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[77123.890801] ata6.00: configured for UDMA/33
[77123.890813] ata6: EH complete
[77123.912801] sd 7:0:0:0: [sde] 320173056 512-byte hardware sectors (163929 MB)
[77123.912933] sd 7:0:0:0: [sde] Write Protect is off
[77123.912935] sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
[77123.927243] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[77123.994363] ata6: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0x2 frozen
[77123.994379] ata6: hard resetting port
[77127.865858] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[77127.890255] ata6.00: configured for UDMA/33
[77127.890261] ata6: EH complete
[77127.908348] sd 7:0:0:0: [sde] 320173056 512-byte hardware sectors (163929 MB)
[77127.931593] sd 7:0:0:0: [sde] Write Protect is off
[77127.931598] sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
[77127.933475] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[77128.017600] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0x2 frozen
[77128.017611] ata6.00: cmd c8/00:08:ee:e6:79/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
[77128.017612]          res ff/ff:ff:ff:ff:ff/ff:ff:ff:ff:ff/ff Emask 0x12 (ATA bus error)
[77128.017620] ata6: hard resetting port
```

From this I understand that it is something to do with sde that is the problem and I know which drive this is.  What I don't know is:
[LIST=1]
[*]What exactly is the problem?
[*]How do I fix it?
[*]If it requires scrapping the drive how can I do this without royally screwing up fstab? (I imagine that the odds fo finding another disk just like it to replace it with are pretty slim given that the disk is about 4 years old now)
[/LIST]

One last point of interest:  I had this problem before and I ended up locked out of my machine because it failed to boot, telling me I needed to run **fschk** as root to do anything.  I had no idea what the root password was so I was dead in the water.  I ended up running a live CD, copying everything to an external HD, and rebuilding everything from scratch (everything on the HDs got formatted except for /home).  This worked well for two weeks and now I seem to be suffering the same problem so I'm guessing a disk has to go.  I've tried to unlock root and give it a password in anticipation of the same problem when I reboot my machine, but nothing happens!

```
:~$sudo passwd -u root
:~$ sudo passwd root
:~$
```

Actually, it looks like I can't use **sudo** for anything! :confused:

Any thoughts on how I can save this sinking ship with anything better than copying all my data, pulling the drive and rebuilding everything from scratch would be hugely appreciated.

**UPDATE**
After leaving it alone for a while things seem to have sorted themselves out.  Running **dmesg** returns
```
[80832.247920] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0x2 frozen
[80832.247931] ata6.00: cmd c8/00:a0:76:b6:8a/00:00:00:00:00/e2 tag 0 cdb 0x0 data 81920 in
[80832.247932]          res ff/ff:ff:ff:ff:ff/ff:ff:ff:ff:ff/ff Emask 0x12 (ATA bus error)
[80832.247940] ata6: hard resetting port
[80836.120937] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[80836.145321] ata6.00: configured for UDMA/33
[80836.145334] ata6: EH complete
[80836.165884] sd 7:0:0:0: [sde] 320173056 512-byte hardware sectors (163929 MB)
[80836.166120] sd 7:0:0:0: [sde] Write Protect is off
[80836.166123] sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
[80836.201331] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[80836.302563] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x90000 action 0x2 frozen
[80836.302574] ata6.00: cmd c8/00:b0:e6:5f:8a/00:00:00:00:00/e2 tag 0 cdb 0x0 data 90112 in
[80836.302575]          res ff/ff:ff:ff:ff:ff/ff:ff:ff:ff:ff/ff Emask 0x12 (ATA bus error)
[80836.302584] ata6: hard resetting port
[80840.176376] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[80840.200783] ata6.00: configured for UDMA/33
[80840.200794] ata6: EH complete
[80840.216082] ata6.00: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0x2 frozen
[80840.216090] ata6.00: cmd c8/00:b0:e6:5f:8a/00:00:00:00:00/e2 tag 0 cdb 0x0 data 90112 in
[80840.216092]          res d0/d0:d0:d0:d0:d0/ff:ff:ff:ff:ff/c0 Emask 0x12 (ATA bus error)
[80840.216099] ata6: hard resetting port
[80840.940261] ata6: SATA link down (SStatus 0 SControl 310)
[80840.940272] ata6: failed to recover some devices, retrying in 5 secs
[80845.943570] ata6: hard resetting port
[80846.667468] ata6: SATA link down (SStatus 0 SControl 310)
[80846.667481] ata6.00: limiting speed to UDMA/33:PIO3
[80846.667483] ata6: failed to recover some devices, retrying in 5 secs
[80851.670778] ata6: hard resetting port
[80852.394676] ata6: SATA link down (SStatus 0 SControl 310)
[80852.394688] ata6.00: disabled
[80852.898617] sd 7:0:0:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[80852.898623] sd 7:0:0:0: [sde] Sense Key : Aborted Command [current] [descriptor]
[80852.898627] Descriptor sense data with sense descriptors (in hex):
[80852.898629]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[80852.898634]         00 d0 d0 d0 
[80852.898636] sd 7:0:0:0: [sde] Add. Sense: Scsi parity error
[80852.898642] end_request: I/O error, dev sde, sector 42622950
[80852.898647] raid1: sde7: rescheduling sector 29915472
[80852.898659] sd 7:0:0:0: rejecting I/O to offline device
[80852.898664] ata6: EH complete
[80852.899978] sd 7:0:0:0: rejecting I/O to offline device
[80852.899981] sd 7:0:0:0: rejecting I/O to offline device
[80852.899983] sd 7:0:0:0: rejecting I/O to offline device
[80852.899988] md: super_written gets error=-5, uptodate=0
[80852.899991] raid1: Disk failure on sde7, disabling device. 
[80852.899992]  Operation continuing on 1 devices
[80852.900008] sd 7:0:0:0: rejecting I/O to offline device
[80852.900012] sd 7:0:0:0: rejecting I/O to offline device
[80852.900015] sd 7:0:0:0: rejecting I/O to offline device
[80852.900018] sd 7:0:0:0: [sde] READ CAPACITY failed
[80852.900020] sd 7:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[80852.900023] sd 7:0:0:0: [sde] Sense not available.
[80852.900027] sd 7:0:0:0: rejecting I/O to offline device
[80852.900030] sd 7:0:0:0: [sde] Write Protect is off
[80852.900032] sd 7:0:0:0: [sde] Mode Sense: 00 00 00 00
[80852.900035] sd 7:0:0:0: rejecting I/O to offline device
[80852.900038] sd 7:0:0:0: [sde] Asking for cache data failed
[80852.900040] sd 7:0:0:0: [sde] Assuming drive cache: write through
[80852.900045] ata6.00: detaching (SCSI 7:0:0:0)
[80852.900224] sd 7:0:0:0: [sde] Stopping disk
[80852.900432] sd 7:0:0:0: [sde] START_STOP FAILED
[80852.900434] sd 7:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[80852.912922] RAID1 conf printout:
[80852.912929]  --- wd:1 rd:2
[80852.912933]  disk 0, wo:0, o:1, dev:sdd7
[80852.912935]  disk 1, wo:1, o:0, dev:sde7
[80852.926632] RAID1 conf printout:
[80852.926638]  --- wd:1 rd:2
[80852.926642]  disk 0, wo:0, o:1, dev:sdd7
[80852.938358] raid1: sdd7: redirecting sector 29915472 to another mirror
[80853.243776] scsi 7:0:0:0: rejecting I/O to dead device
[80853.243787] md: super_written gets error=-5, uptodate=0
[80853.243791] raid1: Disk failure on sde5, disabling device. 
[80853.243792]  Operation continuing on 1 devices
[80853.304479] RAID1 conf printout:
[80853.304486]  --- wd:1 rd:2
[80853.304489]  disk 0, wo:0, o:1, dev:sdd5
[80853.304491]  disk 1, wo:1, o:0, dev:sde5
[80853.314545] RAID1 conf printout:
[80853.314547]  --- wd:1 rd:2
[80853.314549]  disk 0, wo:0, o:1, dev:sdd5
[80853.347675] scsi 7:0:0:0: rejecting I/O to dead device
[80853.347686] raid1: sde8: rescheduling sector 185549144
[80853.347699] scsi 7:0:0:0: rejecting I/O to dead device
[80853.388747] scsi 7:0:0:0: rejecting I/O to dead device
[80853.388754] raid1: Disk failure on sde8, disabling device. 
[80853.388755]  Operation continuing on 1 devices
[80853.388760] raid1: sdd8: redirecting sector 185549144 to another mirror
[80853.413931] RAID1 conf printout:
[80853.413938]  --- wd:1 rd:2
[80853.413941]  disk 0, wo:0, o:1, dev:sdd8
[80853.413943]  disk 1, wo:1, o:0, dev:sde8
[80853.422529] RAID1 conf printout:
[80853.422531]  --- wd:1 rd:2
[80853.422533]  disk 0, wo:0, o:1, dev:sdd8

```
So, it looks like it has detected the error on the drive (finally) and decided to kill the device entirely.  Can I keep the RAID1 running for the rest of the partitions on the drive?  How long might I be able to get away with this for?

Oh yeah, I still don't have any root/sudo access, the best I can get is this error:
*The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.*

---

### Post by jsym on 2008-02-18
Well, everything is pretty much fixed (with the exception of swapping out the faulty drive).  I didn't get any help from the forums directly, but through many hours of trolling I did find pieces of what I needed.  I write the following in the hopes that it will similarly help someone in the future.

**[NOTE: Substitute your username for all cases of "USERNAME"]**

The recommendation for overcoming this error:

*The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.*

was to switch to recovery mode in GRUB and then run the following command:
```
adduser admin USERNAME
```
It failed to do anything.

Running the **groups** command (just type "groups" at the command prompt) hinted at what the problem might be because it returned nothing, not even when I was logged in as root in recovery mode (it should at least return some groups for root).

Given this, I suspected that somehow all my groups had been erased.  This would require rebuilding the group list.  To do this I elected to rebuild the group file using nano (I understand that this can be done via the command line, but that seemed to be more of a pain than it was worth).  The command to edit this from within recovery mode is:
```
nano /etc/group
```
Once inside nano I simply typed out the following, copying it from a computer whose group file I was confident was correct (similar installation):
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:USERNAME
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,USERNAME
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,USERNAME
floppy:x:25:haldaemon,USERNAME
tape:x:26:
sudo:x:27:
audio:x:29:USERNAME
dip:x:30:USERNAME
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:USERNAME
sasl:x:45:
plugdev:x:46:haldaemon,USERNAME
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
crontab:x:104:
ssh:x:105:
lpadmin:x:106:USERNAME
messagebus:x:107:
haldaemon:x:108:
slocate:x:109:
scanner:x:110:cupsys,USERNAME,hplip
gdm:x:111:
jsimpson:x:1000:
admin:x:112:USERNAME
avahi:x:113:
ssl-cert:x:114:
avahi-autoipd:x:115:
netdev:x:116:
nvram:x:117:
powerdev:x:118:haldaemon
fuse:x:119:
```
This restored my group access as well as restoring all the appropriate groups and giving me the power to use **sudo** again.

When I rebooted I received the following error:

*The GDM user 'gdm' does not exist...*

Which prevented me from logging in via GDM.  I was able to login via the command prompt and then get into X via **startx**, but this was not a viable longterm solution.

To solve this I called on my newly restored administrative powers and, based on advice in [this forum post]("http://ubuntuforums.org/showthread.php?t=623647"), ran:
```
sudo dpkg-reconfigure -a
```
This failed miserably (I don't remember the error).  Likely a good thing because who really wants to reconfigure *everything*?  Instead I figured that since I was having problems with gdm I would reconfigure gdm and thus ran:
```
sudo dpkg-reconfigure gdm
```
This worked!

After reboot and login via gdm I was greeted with a warning about HAL.  This was overcome by running
```
sudo dpkg-reconfigure hal
```
Now, everything seems to be hopping along quite nicely.
:)

---

