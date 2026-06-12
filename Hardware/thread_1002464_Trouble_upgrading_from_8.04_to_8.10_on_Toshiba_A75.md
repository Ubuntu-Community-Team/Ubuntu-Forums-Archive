---
title: "Trouble upgrading from 8.04 to 8.10 on Toshiba A75"
date: 2008-12-05
forum: Hardware
---

### Post by Cthulhu32 on 2008-12-05
Hey everyone,

    Been loving Ubuntu so far, and the only real issue I've run into so far is when I upgraded from 8.04 to 8.10 via the program updater. Burned DVDs and CDs (including game media) work fine, but commercial DVDs are no longer working. I stick the media in and nothing pops up. So I did a little inspection, and here's what I've come up with so far:

fstab is set to :
...
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

So I tried mounting this manually, and I got mount: special device /dev/hdc does not exist   So I try manually mounting /dev/scd0, and I get:

sudo mount -t iso9660 /dev/scd0 /media/cdrom0/
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

then dmesg | tail
[ 2434.476627] sr: Sense Key : Hardware Error [current]
[ 2434.476634] sr: Add. Sense: Focus servo failure
[ 2434.484393] sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 0000 00 00 00 00 00 02 00
[ 2434.484426] sr: Sense Key : Hardware Error [current]
[ 2434.484433] sr: Add. Sense: Focus servo failure
[ 2434.493158] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=32
[ 2448.376271] ACPI Error (evregion-0315): No handler for Region [ECR_] (f7012410) [EmbeddedControl] [20080609]
[ 2448.376293] ACPI Error (exfldio-0291): Region EmbeddedControl(3) has no handler [20080609]
[ 2448.376307] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.EPWR.PCLK] (Node f7011858), AE_NOT_EXIST
[ 2448.376370] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._Q1E] (Node f7018930), AE_NOT_EXIST


Not sure what the last bit is (probably not related), but I've been reading through this error on google, and none of the solutions have worked so far. I've got libdvdcss2 and libdvdread3 installed, and I've run install-css.sh

The DVD was working great in 8.04, but the update killed it :/

Also I am running Ubuntu 8.10 2.6.27.9-generic kernel on a Toshiba Satellite A75-S229.

---

