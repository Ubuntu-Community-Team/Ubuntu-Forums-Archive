---
title: "will only boot in Low Graphics Mode"
date: 2019-12-02
forum: Hardware
---

### Post by flyinghigh2 on 2019-12-02
will only boot in Low Graphics Mode

Hi this means the wifi doesn't work and I cant get online.
Ive tried restarting

the message on start up reads,

**The system is running in low graphics mode**
Your screen, graphics card and input device settings could not be detected correctly, You will need to configure these yourself.

it boots fine in default graphics mode but cant use wifi *update last time I restarted the mouse wasnt visible so I couldnt boot

luckily I just bought a raspberry Pi so can still access the web

thanks in advance for any help

I did an update and upgrade recently and it said something was missing and I had to do something but being a noob I didnt know what to do
not sure if Ive restarted since then, so that may be the problem?

Robert

---

### Post by flyinghigh2 on 2019-12-02
well I booted into recovery mode 

and choose upgrade broken packages

this seemed to work

wifi is now working, sorta

I restarted and it wont boot again...

well will onlyboot into safe mode with no wifi

---

### Post by Autodave on 2019-12-02
Was this a new install?  An update?  Did it ever work right and then just quit?

Some info on your system would be quite helpful.

What version of 'buntu are you running?

---

### Post by flyinghigh2 on 2019-12-02
16.04
been running sweet for years
now it wont even boot,
just get the black screen with a lonely blinking cursor

---

### Post by flyinghigh2 on 2019-12-02
im running a diagnostic test, one of the few things i could do

timers. ati sb [something]
error code 0221
msg' error code 2000-0221
msg, timer - inteval timer not functional

mean anything?

---

### Post by flyinghigh2 on 2019-12-02
oh yeah, i did drop a cd case on the touchpad button, which now doesnt work, neither does the headphone port underneath it, but the computer has been running fine , I just use an optical mouse

---

### Post by flyinghigh2 on 2019-12-02
[TABLE="class: table table-hover table-bordered, width: 1095"]
[TR="bgcolor: #F0F0F0"]
[TD="bgcolor: #CCE5F1, align: center"][B]PSA 1000-0221

ePSA 2000-0221 (Not used with [UEFI BIOS]("https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/uefi-firmware"))[/B][/TD]
[TD="bgcolor: #CCE5F1, align: center"]PSA System board - Interval timer Channel 0 (mode 0) is not generating interrupts.

ePSA Timer - Interval timer not functional.[/TD]
[TD="bgcolor: #CCE5F1"]An error occurred during the tests that may involve the main system board of the system. When a memory error is detected, try memory modules individually. When no 2000-0123 memory error occurs, and when diagnostics fail again after the BIOS is at the most current version, visit our [ePSA online tool]("https://www.dell.com/support/home/Pre-boot-Analysis").[/TD]
[TD="bgcolor: #CCE5F1, align: left"]
[LIST]
[*]Update to the latest [BIOS]("https://www.dell.com/support/article/SLN129956/en").
[*]Reseat the CMOS battery.
[*]Repeat the PSA diagnostics
[*]When the diagnostics still results in an error code, visit our [ePSA online tool]("https://www.dell.com/support/home/Pre-boot-Analysis"). You can get more information on possible resolutions to your issue and even get a part dispatched if needed.
[/LIST]
[/TD]
[/TR]
[/TABLE]
i now get this error code on the psa so its probably not a linux issue, more a dead computer problem ?

---

### Post by Autodave on 2019-12-03
You still didn't give any info on your machine.  Is this a laptop?  If so, disconnect every cable from it after powering down.  Disconnect power cable.  Remove battery.  Wait 10 minutes.  Reassemble and try.

---

### Post by flyinghigh2 on 2019-12-04
thats great dave its working again 


yes a dell inspiron laptop m5030

it still only boots into low graphics mode atm but its a start

---

