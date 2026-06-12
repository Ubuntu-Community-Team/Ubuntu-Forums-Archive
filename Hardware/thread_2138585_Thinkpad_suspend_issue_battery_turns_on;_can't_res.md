---
title: "Thinkpad suspend issue: battery turns on; can't resume; must do hard reboot"
date: 2013-04-24
forum: Hardware
---

### Post by dangillmor on 2013-04-24
Using ThinkPad T430s, Ubuntu 12.10 with latest updates:

This started happening about a month ago. Suspend/resume was working fine but now is a problem ~50% of the time. I shut the lid and it suspends, but frequently one of two things happens:

1. The battery light stays on. The machine won't resume from Suspend. Have to reboot by holding down the startup button until it shuts off completely.

2. Sometimes immediately, but often after some time passes, the battery comes back on. Computer (especially as it's usually in a carrying case by then) gets very hot. Same inability to resume, and forced reboot.

At this point I don't dare use suspend. I shut it down entirely.

Here's what I sent to Ubuntu Bugs, which asked me to try an "upstream kernel" -- but the instructions were above my technical level; no other suggestions there.

ProblemType: Bug
DistroRelease: Ubuntu 12.10
Package: linux-image-3.5.0-26-generic 3.5.0-26.42
ProcVersionSignature: Ubuntu 3.5.0-26.42-generic 3.5.7.6
Uname: Linux 3.5.0-26-generic i686
ApportVersion: 2.6.1-0ubuntu10
Architecture: i386
AudioDevicesInUse:
 USER PID ACCESS COMMAND
 /dev/snd/controlC0: dsg 2496 F.... pulseaudio
Date: Tue Mar 26 20:19:22 2013
HibernationDevice: RESUME=UUID=022dee23-37cf-4d1c-b948-71107feb2ffa
InstallationDate: Installed on 2012-12-28 (88 days ago)
InstallationMedia: Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
MachineType: LENOVO 2352CTO
MarkForUpload: True
ProcEnviron:
 TERM=xterm
 PATH=(custom, no user)
 XDG_RUNTIME_DIR=<set>
 LANG=en_US.UTF-8
 SHELL=/bin/bash
ProcFB: 0 inteldrmfb
ProcKernelCmdLine: BOOT_IMAGE=/vmlinuz-3.5.0-26-generic root=/dev/mapper/ubuntu-root ro quiet splash vt.handoff=7
RelatedPackageVersions:
 linux-restricted-modules-3.5.0-26-generic N/A
 linux-backports-modules-3.5.0-26-generic N/A
 linux-firmware 1.95
RfKill:
 0: phy0: Wireless LAN
  Soft blocked: yes
  Hard blocked: no
SourcePackage: linux
UpgradeStatus: No upgrade log present (probably fresh install)
dmi.bios.date: 11/12/2012
dmi.bios.vendor: LENOVO
dmi.bios.version: G7ET63WW (2.05 )
dmi.board.asset.tag: Not Available
dmi.board.name: 2352CTO
dmi.board.vendor: LENOVO
dmi.board.version: Not Defined
dmi.chassis.asset.tag: No Asset Information
dmi.chassis.type: 10
dmi.chassis.vendor: LENOVO
dmi.chassis.version: Not Available
dmi.modalias: dmi:bvnLENOVO:bvrG7ET63WW(2.05):bd11/12/2012:svnLENOVO:pn2352CTO:pvrThinkPadT430s:rvnLENOVO:rn2352CTO:rvrNotDefined:cvnLENOVO:ct10:cvrNotAvailable:
dmi.product.name: 2352CTO
dmi.product.version: ThinkPad T430s
dmi.sys.vendor: LENOVO

---

### Post by tgalati4 on 2013-04-24
So it used to work fine and now it doesn't work?  How long was it working normally?  Have you updated the BIOS recently?  If not, look for a BIOS update and see if that fixes the problem.  It sounds more like a hardware problem than a kernel one.  Did you perform a kernel update a month ago that you could correlate to this issue?  You should have older kernels in your GRUB menu.  Try booting into an older kernel and see if it behaves the same.  That is why the older kernels are kept around.

---

### Post by jpakin on 2013-10-07
Just wanted to let you know I'm having the same problem, same machine (love my T430s otherwise). I'll try the above when I have a chance and let you know how it goes.

---

