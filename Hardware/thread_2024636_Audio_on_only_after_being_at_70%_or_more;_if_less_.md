---
title: "Audio on only after being at 70% or more; if less there's no sound"
date: 2012-07-13
forum: Hardware
---

### Post by cyb3rponk on 2012-07-13
Hi guys! I have an HP Pavilion DV9500 with Ubuntu 12.04 LTS installed and it detected every driver when I first installed, which is awesome! I'm still amazed at Linux's betterment in hardware compatibility over ther years. 

I have sound, but I have to turn on my volume and when its at 70% that's when I can hear the laptop's audio, but if I'm below 70% I don't hear anything, which is kinda weird. I assume that there's something wrong with the driver, but don't know how to fix it. 

Any suggestions are welcome. I submitted the bug to the developers and here's some information that might come in handy for any suggestions:

ProblemType: Bug
DistroRelease: Ubuntu 12.04
Package: alsa-base 1.0.25+dfsg-0ubuntu1
ProcVersionSignature: Ubuntu 3.2.0-26.41-generic 3.2.19
Uname: Linux 3.2.0-26-generic x86_64
NonfreeKernelModules: nvidia wl
AlsaVersion: Advanced Linux Sound Architecture Driver Version 1.0.24.
ApportVersion: 2.0.1-0ubuntu8
Architecture: amd64
ArecordDevices:
 **** List of CAPTURE Hardware Devices ****
 card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
   Subdevices: 1/1
   Subdevice #0: subdevice #0
AudioDevicesInUse:
 USER PID ACCESS COMMAND
 /dev/snd/controlC0: alejandro 1803 F.... pulseaudio
Card0.Amixer.info:
 Card hw:0 'NVidia'/'HDA NVidia at 0xf6480000 irq 21'
   Mixer name	: 'Conexant CX20549 (Venice)'
   Components	: 'HDA:14f15045,103c30cf,00100100'
   Controls : 18
   Simple ctrls : 9
Date: Fri Jul 13 19:21:04 2012
InstallationMedia: Ubuntu 12.04 LTS "Precise Pangolin" - Release amd64 (20120425)
PackageArchitecture: all
ProcEnviron:
 PATH=(custom, no user)
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SourcePackage: alsa-driver
Symptom: audio
Symptom_Card: Built-in Audio - HDA NVidia
Symptom_Jack: Speaker, Internal
Symptom_Type: Volume slider, or mixer problems
Title: [HP Pavilion dv9500 Notebook PC, Conexant CX20549 (Venice), Speaker, Internal] volume slider problem
UpgradeStatus: No upgrade log present (probably fresh install)
dmi.bios.date: 03/22/2010
dmi.bios.vendor: Hewlett-Packard
dmi.bios.version: F.33
dmi.board.name: 30D1
dmi.board.vendor: Quanta
dmi.board.version: 85.26
dmi.chassis.type: 10
dmi.chassis.vendor: Quanta
dmi.chassis.version: N/A
dmi.modalias: dmi:bvnHewlett-Packard:bvrF.33:bd03/22/2010:svnHewlett-Packard:pnHPPaviliondv9500NotebookPC:pvrRev1:rvnQuanta:rn30D1:rvr85.26:cvnQuanta:ct10:cvrN/A:
dmi.product.name: HP Pavilion dv9500 Notebook PC
dmi.product.version: Rev 1
dmi.sys.vendor: Hewlett-Packard
mtime.conffile..etc.modprobe.d.alsa.base.conf: 2012-07-04T15:33:38.157062

Thanks in advance for any suggestion, guys!

---

