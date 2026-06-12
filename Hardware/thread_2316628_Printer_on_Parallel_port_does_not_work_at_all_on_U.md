---
title: "Printer on Parallel port does not work at all on Ubuntu 14.04"
date: 2016-03-09
forum: Hardware
---

### Post by abcuser on 2016-03-09
Hi,

[SIZE=3]**EDIT: Please jump to the last post. All other post (problems) in between already solved. Start reading at: [http://ubuntuforums.org/showthread.php?t=2316628&p=13458617#post13458617](http://ubuntuforums.org/showthread.php?t=2316628&p=13458617#post13458617) where I am describing command's outputs of Parallel Printer tests as described on official Ubuntu web page.**[/SIZE]

I have got Ubuntu 14.04 and "HP LaserJet 2010 tn" connected to [Parallel port]("https://en.wikipedia.org/wiki/Parallel_port") (not USB!) and printer was working without a problem (this is Parallel printer only, not an USB printer).

I have had some problems with Ubuntu (with USB wireless WiFi card), so I decided to wipe out Ubuntu and install it one more time. So I downloaded Ubuntu 14.04.4 64-bit Desktop and installed it.

Installation without a problem. But now my parallel printer does not work. I am not very capable of debugging parallel port. I followed this tutorial: [https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer)

First my BIOS settings has not changed! Just to make sure I have checked BIOS settings and Parallel port is Enabled.

To follow above debug tutorial, bellow are the outputs:
1. My printer is connected to my PC and printer is turned on. I can make printer test by pressing on printer button and test page is printed out successfully.

2. Commands:
> lsmod | grep lp
lsmod | grep ppdev
lsmod | grep parport_pc

None of above commands put any output!

3.I tried command: dmesg | grep par | grep -v apparmor  (I added the "apparmor" to remove this from output):
> [    0.000000] Booting paravirtualized kernel on bare hardware
[    0.097111] regulator-dummy: no parameters
[    0.104618] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff8801a738b708), AE_ALREADY_EXISTS (20131115/psparse-536)
[    0.105313] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-10] only partially covers this bridge
[    0.112442] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.439240] Asymmetric key parser 'x509' registered

4. Command: ls -l /dev/lp* /dev/parport* 
Returns that no file or directory is found (two lines, one for each of the commmand).

5. Command: ls -l /proc/sys/dev/parport/parport*/autoprobe* 
Returns that no file or directory is found.

sudo cat /proc/sys/dev/parport/parport*/autoprobe* 
Also returns that no file or directory is found.

6. Command: lpinfo -v
> serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS4?baud=115200
network ipp
network socket
network ipp14
network http
network https
network lpd
direct hp
network ipps
network smb
direct hpfax

7. Both bellow command outputs nothing.
> /usr/lib/cups/backend/parallel 
sudo /usr/lib/cups/backend/parallel 

How to fix the problem and establish printer as it was on plain Ubuntu 14.04 (also with latest updates)?
Thanks

---

### Post by abcuser on 2016-03-20
bump...

---

### Post by SeijiSensei on 2016-03-20
Have you tried using the CUPS web interface?  Open a browser on the machine to which the printer is attached and point it to [http://localhost:631/](http://localhost:631/).  Choose Administration > Add Printer and enter your login username and password when prompted.  Does CUPS see the printer?

---

### Post by coldraven on 2016-03-20
Without knowing anything about this topic I seem to have stumbled upon a solution. So check this post and see if it helps.
[http://ubuntuforums.org/showthread.php?t=2316959&p=13454538#post13454538](http://ubuntuforums.org/showthread.php?t=2316959&p=13454538#post13454538)

---

### Post by abcuser on 2016-03-21
@SeijiSensei, I have tried that, but the settings are the same as from System Settings | Printer | Add Printer.

@coldraven, I have uninstall package: sudo apt-get remove libsane-hpaiov
This package was installed. System Settings | Printer | Add Printer | Manually Add URI, I pasted: parallel:/dev/lp0
as suggested by forum post, but then when I tried to print "test printer page" nothing happened. I clicked on Printer icon from top bar and there was message: "Is printer connected" (something similar, I don't use English in Ubuntu). I have double checked. Printer is turned on. At printer side there is unpluggable cable type (so it can't be unplugged) and on PC there is LPT port connected without a problem.

But in my humble opinion there got to be something else wrong. You know every tutorial I read on internet there is info to check if **_kernel modules for LPT printer is turned on_** like commands:

lsmod | grep lp
lsmod | grep ppdev
lsmod | grep parport_pc

but non of above commands return any info!!! This most probably indicate like there is something wrong with printer kernel modules or something similar. But in any tutorial there is zero info how to continue if above commands return no output. There is ALWAYS assumption that above command do return output. But in my case they don't!

I have double check my PC's BIOS settings to be sure Parallel port is turned on in BIOS. So there are BIOS settings:
Parallel port: Enabled
Mode: Output only
Base IO/ address: 378
Interrupt: IRQ7

So Parallel port in BIOS looks OK, I haven't touched any setting in BIOS and previously my printer (before fresh install of Ubuntu 14.04.4) was working without a problem. Printer is turned on, properly connected with PC.

Any idea how to debug this printer problem? How to install kernel printer modules or something??? How to continue if above three commands return no output?

Thanks

---

### Post by abcuser on 2016-03-21
Now I have **partially** solved the problem, but I still can't print.


**KERNEL MODULES**

Like I have written above there was something wrong with kernel modules. I have found out the following:
```
uname -r
```
Outputted: 3.13.0-37-generic
but output of:
```
ls /lib/modules
```
Outputted: 3.13.0-79-generic 

This is obvious stupidity. Kernel with one version and modules with another.
```
sudo apt-get install --reinstall -y --force-yes linux-generic
```
and rebooted machine.
```
uname -r
```
Outputted: 3.13.0-83-generic
and
```
ls /lib/modules
```
Outputted: 3.13.0-79-generic and  3.13.0-83-generic

Just to clean up old messed up kernel modules I deleted:
```
sudo rm -rf 3.13.0-79-generic
```

OK, so now kernel modules are exactly the same as kernel version.




**RETESTING PARALLEL PRINTER**

Retesting the instructions from Parallel Printing debug web page: [https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Parallel_port_printer)
1. I checked Printer is turned on and properly connected to PC.
2.
```
lsmod | grep lp
```
and output is:
```
drm_kms_helper         55071  1 i915
drm                   303102  4 i915,drm_kms_helper
lpc_ich                21080  0 
lp                     17759  2 
parport                42348  3 lp,ppdev,parport_pc

```

```
lsmod | grep ppdev
```
outputs:
```
ppdev                  17671  44 
parport                42348  3 lp,ppdev,parport_pc
```

```
lsmod | grep parport_pc
```
outpus:
```
parport_pc             32701  3 
parport                42348  3 lp,ppdev,parport_pc
```

NOTE: So finally those commands does ouptput something.

3. 
```
dmesg | grep par
```
outputs:
```

[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.092006] regulator-dummy: no parameters
[    0.103975] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff8801a738b708), AE_ALREADY_EXISTS (20131115/psparse-536)
[    0.104681] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-10] only partially covers this bridge
[    0.108684] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.436418] Asymmetric key parser 'x509' registered
[   16.352185] parport_pc 00:09: reported by Plug and Play ACPI
[   16.352211] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   16.366758] parport0: Printer, Hewlett-Packard HP LaserJet 2100 Series
[   16.368010] lp0: using parport0 (interrupt-driven).
[   16.415076] ppdev: user-space parallel port driver
[   16.545471] type=1400 audit(1458584764.073:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=362 comm="apparmor_parser"
[   16.545477] type=1400 audit(1458584764.073:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=362 comm="apparmor_parser"
[   16.545482] type=1400 audit(1458584764.073:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=362 comm="apparmor_parser"
[   16.545832] type=1400 audit(1458584764.073:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=362 comm="apparmor_parser"
[   16.545837] type=1400 audit(1458584764.073:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=362 comm="apparmor_parser"
[   16.546036] type=1400 audit(1458584764.073:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=362 comm="apparmor_parser"
[   20.704019] type=1400 audit(1458584768.229:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=735 comm="apparmor_parser"
[   20.704027] type=1400 audit(1458584768.233:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=735 comm="apparmor_parser"
[   20.706260] type=1400 audit(1458584768.233:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=735 comm="apparmor_parser"
[   20.877782] type=1400 audit(1458584768.405:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=797 comm="apparmor_parser"
[   21.778129] type=1400 audit(1458584769.305:61): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=969 comm="apparmor_parser"
[   50.798802] type=1400 audit(1458584798.325:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2167 comm="apparmor_parser"
[   50.798810] type=1400 audit(1458584798.325:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2167 comm="apparmor_parser"
[   50.799169] type=1400 audit(1458584798.325:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2167 comm="apparmor_parser"
[  217.342853] type=1400 audit(1458584964.873:65): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2449 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  217.342869] type=1400 audit(1458584964.873:66): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2449 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  217.343552] type=1400 audit(1458584964.873:67): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  217.343561] type=1400 audit(1458584964.873:68): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  244.576290] type=1400 audit(1458584992.105:69): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  244.576297] type=1400 audit(1458584992.105:70): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  244.576302] type=1400 audit(1458584992.105:71): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  244.576306] type=1400 audit(1458584992.105:72): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  244.576310] type=1400 audit(1458584992.105:73): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  244.576314] type=1400 audit(1458584992.105:74): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  244.576319] type=1400 audit(1458584992.105:75): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  299.312846] type=1400 audit(1458585046.842:76): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  360.432056] INFO: task parallel:2460 blocked for more than 120 seconds.
[  360.432065] parallel        D ffff8801afc13180     0  2460      1 0x00000004
[  480.432055] INFO: task parallel:2460 blocked for more than 120 seconds.
[  480.432065] parallel        D ffff8801afc13180     0  2460      1 0x00000004
[  486.937930] type=1400 audit(1458585234.466:77): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2556 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  486.937940] type=1400 audit(1458585234.466:78): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2556 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  486.938539] type=1400 audit(1458585234.466:79): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  486.938546] type=1400 audit(1458585234.466:80): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  542.757984] type=1400 audit(1458585290.286:81): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2584 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  542.757994] type=1400 audit(1458585290.286:82): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2584 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  542.758635] type=1400 audit(1458585290.286:83): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  542.758643] type=1400 audit(1458585290.286:84): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  550.839258] type=1400 audit(1458585298.366:85): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=kill peer="unconfined"
[  550.839267] type=1400 audit(1458585298.366:86): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=kill peer="unconfined"
[  550.839274] type=1400 audit(1458585298.366:87): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=kill peer="unconfined"
[  567.616550] type=1400 audit(1458585315.146:88): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2632 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  567.616560] type=1400 audit(1458585315.146:89): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2632 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  567.617231] type=1400 audit(1458585315.146:90): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  567.617238] type=1400 audit(1458585315.146:91): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  600.432057] INFO: task parallel:2460 blocked for more than 120 seconds.
[  600.432067] parallel        D ffff8801afc13180     0  2460      1 0x00000004
[  629.123358] type=1400 audit(1458585376.654:92): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2664 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  629.123367] type=1400 audit(1458585376.654:93): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2664 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  629.124062] type=1400 audit(1458585376.654:94): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  629.124070] type=1400 audit(1458585376.654:95): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  676.422678] type=1400 audit(1458585423.950:96): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2717 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  676.422688] type=1400 audit(1458585423.950:97): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2717 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  676.423334] type=1400 audit(1458585423.950:98): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  676.423341] type=1400 audit(1458585423.950:99): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  680.272425] type=1400 audit(1458585427.802:100): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  680.272434] type=1400 audit(1458585427.802:101): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  680.272439] type=1400 audit(1458585427.802:102): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  680.272443] type=1400 audit(1458585427.802:103): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  680.272448] type=1400 audit(1458585427.802:104): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  680.272452] type=1400 audit(1458585427.802:105): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  712.253171] type=1400 audit(1458585459.782:107): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  720.432059] INFO: task parallel:2460 blocked for more than 120 seconds.
[  720.432068] parallel        D ffff8801afc13180     0  2460      1 0x00000004
[  748.771922] type=1400 audit(1458585496.302:108): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2782 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  748.771932] type=1400 audit(1458585496.302:109): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2782 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  748.772802] type=1400 audit(1458585496.302:110): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  748.772809] type=1400 audit(1458585496.302:111): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  798.464056] type=1400 audit(1458585545.994:112): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2826 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  798.464067] type=1400 audit(1458585545.994:113): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2826 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  798.464753] type=1400 audit(1458585545.994:114): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  798.464761] type=1400 audit(1458585545.994:115): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  960.891649] type=1400 audit(1458585708.418:116): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  960.891659] type=1400 audit(1458585708.418:117): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  960.891664] type=1400 audit(1458585708.418:118): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  960.891669] type=1400 audit(1458585708.418:119): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  960.891673] type=1400 audit(1458585708.418:120): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  960.891679] type=1400 audit(1458585708.418:121): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[  960.891683] type=1400 audit(1458585708.418:122): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[ 1065.870542] type=1400 audit(1458585813.398:123): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[ 1141.158174] type=1400 audit(1458585888.686:124): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=kill peer="unconfined"
[ 1141.158181] type=1400 audit(1458585888.686:125): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=kill peer="unconfined"
[ 1141.158186] type=1400 audit(1458585888.686:126): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=kill peer="unconfined"
[ 1158.579326] type=1400 audit(1458585906.106:127): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2952 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[ 1158.579336] type=1400 audit(1458585906.106:128): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2952 comm="cups-deviced" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[ 1158.580160] type=1400 audit(1458585906.110:129): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"
[ 1158.580167] type=1400 audit(1458585906.110:130): apparmor="DENIED" operation="signal" profile="/usr/sbin/cupsd" pid=2168 comm="cupsd" requested_mask="send" denied_mask="send" signal=term peer="unconfined"

```


4. 
```
ls -l /dev/lp* /dev/parport* 
```
outputs:
```

crw-rw---- 1 root lp  6, 0 mar 21 19:26 /dev/lp0
crw-rw-r-- 1 root lp 99, 0 mar 21 19:26 /dev/parport0
```

5. 
```
ls -l /proc/sys/dev/parport/parport*/autoprobe*
```
outputs:
```

-r--r--r-- 1 root root 0 mar 21 19:33 /proc/sys/dev/parport/parport0/autoprobe
-r--r--r-- 1 root root 0 mar 21 19:33 /proc/sys/dev/parport/parport0/autoprobe0
-r--r--r-- 1 root root 0 mar 21 19:33 /proc/sys/dev/parport/parport0/autoprobe1
-r--r--r-- 1 root root 0 mar 21 19:33 /proc/sys/dev/parport/parport0/autoprobe2
-r--r--r-- 1 root root 0 mar 21 19:33 /proc/sys/dev/parport/parport0/autoprobe3

```

```
sudo cat /proc/sys/dev/parport/parport*/autoprobe* 
```
outputs:
```

CLASS:PRINTER;
MODEL:HP LaserJet 2100 Series;
MANUFACTURER:Hewlett-Packard;
DESCRIPTION:Hewlett-Packard LaserJet 2100 Series;
COMMAND SET:PJL,MLC,PCL,PCLXL,POSTSCRIPT;

```

6. 
```
lpinfo -v
```
outputs:
```

serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS4?baud=115200
network ipp14
network socket
network ipps
network https
file cups-pdf:/
network lpd
network ipp
network http
network smb

```

7. 
```
/usr/lib/cups/backend/parallel 
```
outputs nothing!

8. 
```
sudo /usr/lib/cups/backend/parallel
```
also outputs nothing!



I started Settings | Printer | Add printer | Enter URI
I pasted the: parallel:/dev/lp0
Then selected HP | "LaserJet 2100tn" as driver.
Test page and nothing gets printed, no error nothing.

Any idea what else to test?

---

### Post by slickymaster on 2016-03-21
*Moved to the ***Hardware*** sub-forum*

---

### Post by abcuser on 2016-04-04
bump

---

