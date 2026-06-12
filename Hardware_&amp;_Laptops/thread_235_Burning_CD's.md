---
title: "Burning CD's"
date: 2004-10-11
forum: Hardware &amp; Laptops
---

### Post by mikew777 on 2004-10-11
Is anyone else having trouble burning CD's? My hardware is all dectected but I'm having trouble burning. My system is up to date as of 10-11-04. I'm using a LG drive and it sees that just fine but when I load the blank CD it can't see the CD and keeps asking for a new Cd or a rewritable one. I tried 3 different brands of Cd's and it won't use any of them. I hope someone has some answers to this problem.
Thanks
Mike

---

### Post by FLeiXiuS on 2004-10-12
What are you using to burn these CD's?

---

### Post by mikew777 on 2004-10-12
[quote=FLeiXiuS]What are you using to burn these CD's?[/quote]

The drive I'm using is a LG Drive and in all the other Distros I've tried there has never been any problem. Mainly used K3B and Xcdroast writers with 0 issues.

Thanks
Mike

---

### Post by Tasu on 2004-10-13
Taken directly from [www.xcdroast.org:](www.xcdroast.org:)
-------------------------------------------------------------------------------------
Linux Kernel 2.6.8 broke CD-Writing:
I had several reports that the last 2.6.x kernel broke CD-Writing using the ATAPI driver. Don't update if you want to continue to use X-CD-Roast, or switch back to SCSI-emulation. 
Update: When started from a root shell burning still works, but non-root mode is disabled by this kernel.
-------------------------------------------------------------------------------------

I think this could be the issue! Hope they'll fix it really soon!

---

### Post by FLeiXiuS on 2004-10-13
try cdrecord.  It has never failed for me ! :-P

Also CLI &gt; GUI!! :-)

---

### Post by oddabe19 on 2004-10-14
What about K3b? cause I prefer that in Gnome over Xcdroast. How stable is K3b?

---

### Post by mikew777 on 2004-10-15
Just installed K3B from universe and running it from **sudo k3b ** works and everything burns just fine, so the burning program in Ubuntu must be where the problem is for not burning.

Mike

---

### Post by FX on 2004-10-15
I also use "sudo k3b" from a term and it works great. Hopefully in the next kernel release they'll have the non-root burning inabled again.

FX

---

### Post by cseg on 2004-10-15
[quote=FLeiXiuS]try cdrecord[/quote]I could not get cdrecord working for me on ubuntu.  Granted, I was previously using a version on a 2.4 kernel from Debian Stable or Testing.  But still, it hasn't changed that radically, has it?  It doesn't want to see my CD-R drive.

---

### Post by HungSquirrel on 2004-10-15
Could it be that Ubuntu doesn't make cdrecord SETUID root?  When installind Debian I was asked a question about that but Ubuntu doesn't ask the question; I am assuming it defaults to 'no'.

---

### Post by FLeiXiuS on 2004-10-16
As some small case studies has shown I believe this would be a kernel problem and should be fixed with 2.6.9.

---

### Post by mark on 2004-10-16
I have successfully used *nautilus* to burn data &amp; ISO CDs &amp; DVDs, and I'm running kernel 2.6.8.1-3-686-smp.  For ISOs, just point to 'em in *nautilus*, right-click and select *Write to CD*.  For data, open *nautilus*, select *Go-&gt;CD Creator*, then open another *nautilus* instance, drag 'n drop your selections to the *CD Creator* window &amp; select *Write to CD*.

This is on system based on the Intel D865GLC main board, P4/2.8GHz (hyper-threading enabled, hence the SMP kernel) and a Lite-On SOHW-812S DVD+RW drive.

Haven't tried this with music yet, so I can't say how that works...

---

### Post by sfw5000 on 2004-10-17
I was having the same problem and running sudo k3b fixed it. Now, how do you make it so anyone can burn cd's?

---

### Post by jeremy on 2004-10-18
I have downloaded, compiled and installed the latest version 0.11.17 of k3b, it fixes the problem.

---

### Post by ulefr01 on 2004-10-19
I hope you have using apt-get.
How can i install K3b version 0.11.17 ?
Which entries are you using in the sources.list

---

### Post by jeremy on 2004-10-20
No, I d'ld the source code.

---

### Post by snowx1000 on 2004-10-27
[QUOTE=jeremy]I have downloaded, compiled and installed the latest version 0.11.17 of k3b, it fixes the problem.[/QUOTE]
 What other packages did you need to compile?  Regardless of the packages I install, it always complains about kde headers.

---

### Post by az on 2004-10-28
Header are in the development packages.  That is what they are for.

apt-get install kdelibs-dev

(If that is what it's called.)

apt-cache search kde | grep -dev

---

### Post by emperor on 2004-11-16
cdrecord does work if you specific the dev as "/dev/hdc"  (hda hdb or hdd)
 My burner is attached as "/dev/hdd", so the following works:
 
 sudo cdrecord dev=/dev/hdd speed=6 -v somedistro-disc1.iso

---

### Post by Sintara on 2004-11-30
I'm using an IDE Lite-On CD-RW and am unable to burn.  The drive is recognized by the kernel during boot.  I have had no success with cdrecord, Nautilus, xcdroast, gcombust, or k3b.  Here is some relevant information:

john@ubuntu-desktop:~ $ lsmod
Module                  Size  Used by
nfsd                  197984  8
exportfs                6464  1 nfsd
lockd                  62792  2 nfsd
sunrpc                149796  2 nfsd,lockd
proc_intf               3840  0
cpufreq_powersave       1792  0
cpufreq_userspace       5336  0
freq_table              4292  0
ipt_ttl                 1984  1
ipt_limit               2560  34
ipt_state               2112  9
iptable_mangle          2944  0
ipt_LOG                 6592  1
ipt_MASQUERADE          4032  0
ipt_TOS                 2560  0
ipt_REDIRECT            2240  0
iptable_nat            24684  2 ipt_MASQUERADE,ipt_REDIRECT
ipt_REJECT              7040  1
ip_conntrack_irc       71412  0
ip_conntrack_ftp       72180  0
ip_conntrack           34432  6 ipt_state,ipt_MASQUERADE,ipt_REDIRECT,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp
iptable_filter          2944  1
ip_tables              18112  11 ipt_ttl,ipt_limit,ipt_state,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REDIRECT,iptable_nat,ipt_REJECT,iptable_filter
ipv6                  258116  16
8139cp                 20352  0
8139too                25792  0
mii                     5120  2 8139cp,8139too
crc32                   4352  2 8139cp,8139too
ohci1394               35268  0
pciehp                 96236  0
shpchp                 99436  0
pci_hotplug            33776  2 pciehp,shpchp
snd_intel8x0           35564  2
snd_ac97_codec         67908  1 snd_intel8x0
snd_pcm_oss            53160  0
snd_mixer_oss          19520  3 snd_pcm_oss
snd_pcm                95332  2 snd_intel8x0,snd_pcm_oss
snd_timer              25028  1 snd_pcm
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
snd_mpu401_uart         7872  1 snd_intel8x0
snd_rawmidi            25088  1 snd_mpu401_uart
snd_seq_device          8136  1 snd_rawmidi
snd                    55524  9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  3 snd
forcedeth              17472  0
ehci_hcd               30852  0
joydev                  9792  0
tsdev                   7296  0
usbhid                 31680  0
ohci_hcd               21060  0
usbcore               115876  5 ehci_hcd,usbhid,ohci_hcd
nvidia_agp              7772  1
agpgart                33704  1 nvidia_agp
analog                 11808  0
gameport                4672  2 snd_intel8x0,analog
floppy                 59348  0
pcspkr                  3688  0
rtc                    12600  0
nls_iso8859_1           4096  1
nls_cp437               5760  1
vfat                   14592  1
fat                    46144  1 vfat
xfs                   598360  1
md                     48648  0
dm_mod                 57660  1
capability              4616  0
commoncap               7168  1 capability
parport_pc             34944  1
lp                     10820  0
parport                40904  2 parport_pc,lp
evdev                   9536  0
sbp2                   24072  0
ieee1394              109304  2 ohci1394,sbp2
ide_cd                 41732  0
mousedev               10316  1
psmouse                19784  0
sr_mod                 17124  0
scsi_mod              122828  2 sbp2,sr_mod
cdrom                  39648  2 ide_cd,sr_mod
reiserfs              241968  1
ext2                   70504  0
ext3                  124712  1
jbd                    61144  1 ext3
mbcache                 9156  2 ext2,ext3
ide_generic             1472  0
ide_disk               18816  8
amd74xx                14108  1
unix                   28272  795
fan                     4044  0
thermal                13072  0
processor              17456  1 thermal
font                    8448  0
vesafb                  6624  0
cfbcopyarea             3776  1 vesafb
cfbimgblt               3136  1 vesafb
cfbfillrect             3712  1 vesafb
ide_core              136344  4 ide_cd,ide_generic,ide_disk,amd74xx

john@ubuntu-desktop:~ $ sudo cdrecord -scanbus
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

Attempt to Burn Using cdrecord
john@ubuntu-desktop:~ $  sudo cdrecord dev=/dev/hdb speed=6 -v image.iso
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
cdrecord: No such file or directory. Cannot open '/dev/hdb'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

Using xcdroast
Tried to manually configure the burner in xcdroast, but after entering the device path, the "device scan" window appeared saying that the device wasn't found.

Using Nautilus
Nautilus didn't open the burning folder when a blank CD-RW was loaded.  I opened the folder manually, dragged a few small files to the folder, clicked File > Write to Disk, and accepted the default filename for the iso image.  The image appeared to be written to hard disk successfully, but the "Writing Files to Disc Progress" window hung at "Completed writing /home/john/image.iso.  No actual burning happened.

Using k3b
k3b didn't recognize the CD-RW drive.  Manually specifying the drive path didn't work.  k3b said that it couldn't find a drive there.

Any help appreciated.

Here's a new piece of information.  I tried to listen to a pressed audio cd using this drive.  Nothing happened upon insertion, so I went to Nautilus' Disks folder and double-clicked the drive.  A mount error occurred, the cited reason being "special device /dev/hdb does not exist."  I tried to mount the disc via the console, as well, and got the same error message.

Why can't the system mount a disc in a drive that obviously *does* exist and is recognized by the kernel?

---

### Post by ametade on 2005-03-01
[QUOTE=Sintara]I'm using an IDE Lite-On CD-RW and am unable to burn.  The drive is recognized by the kernel during boot.  I have had no success with cdrecord, Nautilus, xcdroast, gcombust, or k3b.[/QUOTE]
Sintara, I'm having the same problem with my Lite-On CD-RW: it gets detected on boot, but It cannot burn cd's. I Can't find any solution... help needed!

---

### Post by aswin_biogenie on 2005-03-25
Hi

I have a unique problem with K3B..

I installed K3B using synaptic and ran it once with sudo k3b.. well, it ran fine, but the problem was i could not log in to my gnome again!! I got an error like "unable to find .ICE-authority" or something like that.. And i ended up reinstalling the whole stuff..

could anyone help me??

rg
aswin

---

### Post by Sqeaky on 2005-03-25
use ctrl+alt+f1 to get a console login then rename the .ICE-authority directory to somethign new, I did something like "mv .ICE-Authority .ICE-Authority_old". then you should be able to login again

---

