---
title: "Trying to get Focusrite Liquid Saffire 56 working with jack under 14.04"
date: 2014-04-26
forum: Hardware
---

### Post by Safira-San on 2014-04-26
Hi everyone,

Apologies in advance if this thread is in the wrong place, and for my complete ineptitude with Ubuntu! I've almost frustrated myself to tears trying to get this to work and any help would be greatly appreciated.

I have a Focusrite Liquid Saffire 56 connected to my PC with a PCI FireWire card (VIA chipset). It works perfectly under Windows and OSX (which I am triple-booting on the same machine, along with Trusty Tahr). I know that this interface works with Ubuntu because I had it working with 12.10 before I did a completely fresh install of Ubuntu 14.04 yesterday. Unfortunately, having followed what I believe are all the right instructions, jack still will not start with firewire or freebob drivers. This is what I get in both instances:

```
[COLOR=#FF0000]13:44:32.699 D-BUS: JACK server could not be started. Sorry[/COLOR]
Sat Apr 26 13:44:28 2014: Starting jack server...
Sat Apr 26 13:44:28 2014: JACK server starting in realtime mode with priority 10
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Sat Apr 26 13:44:32 2014: ERROR: firewire ERR: FFADO: Error creating virtual device
Sat Apr 26 13:44:32 2014: ERROR: Cannot attach audio driver
Sat Apr 26 13:44:32 2014: ERROR: JackServer::Open failed with -1
Sat Apr 26 13:44:32 2014: ERROR: Failed to open server
Sat Apr 26 13:44:32 2014: Saving settings to "/home/rosanna/.config/jack/conf.xml" ...
[COLOR=#ff0000]13:44:38.528 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

```
Here is a list of things that I have done to try and get this to work:
1. Downloaded FFADO 2.1.0 and modified the configuration file as per [http://www.ffado.org/?q=node/2062](http://www.ffado.org/?q=node/2062)
2. Compiled FFADO
3. Installed jackd
4. Started ffado-dbus-server
5. Added my user to the audio group
6. Killed PulseAudio and prevented it from respawning
7. Checked the 60-ffado.rules file, which is in the right place and has correct content
8. Checked the blacklisting for FireWire devices (it's all set correctly)
9. Added the right priority and memory allocation so that the output of ulimit -r -l is:

```
rosanna@rosannas-pc:~$ ulimit -r -lreal-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited

```

I know that my device is seen because the output of ffado-test ListDevices is
```
=== 1394 PORT 0 ===  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00130e0401802b56  0x0000130E  0x00000006   Focusrite - LIQUID_SAFFIRE_56
no message buffer overruns

```

The output of ffado-diag is:

```
FFADO diagnostic utility 2.1.9999-2500============================
(C) 2008 Pieter Palmers
    2009-2010 Arnold Krille




=== CHECK ===
 Base system...
  kernel version............ 3.13.0-24-generic
    Preempt (low latency)... False
    RT patched.............. False
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
  /dev/fw* permissions:
crw-------  1 root root  251, 0 Apr 26 13:07 /dev/fw0
crw-rw----+ 1 root audio 251, 1 Apr 26 13:17 /dev/fw1
  User IDs:
uid=0(root) gid=0(root) groups=0(root)
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu 4.8.2-19ubuntu1) 4.8.2
   g++ ............... g++ (Ubuntu 4.8.2-19ubuntu1) 4.8.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.10.4 for Qt version 4.8.6
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ........... Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
   libraw1394 ........ 2.1.0
     flags ...........  -lraw1394  
   libavc1394 ........ 0.5.4
     flags ...........  -lavc1394 -lrom1394 -lraw1394  
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.36.0
     flags ........... -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include  -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  
   dbus-1 ............ 1.6.18
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -ldbus-1  
 Prerequisites (static at compile-time)...
   gcc ............... gcc (Ubuntu 4.8.2-19ubuntu1) 4.8.2
   g++ ............... g++ (Ubuntu 4.8.2-19ubuntu1) 4.8.2
   PyQt4 (by pyuic4) . Python User Interface Compiler 4.10.4 for Qt version 4.8.6
   jackd ............. Cannot create thread 1 Operation not permitted
     path ............ /usr/bin/jackd
     flags ........... Package jack was not found in the pkg-config search path.
   libraw1394 ........ 2.1.0
     flags ...........  -lraw1394  
   libavc1394 ........ 0.5.4
     flags ...........  -lavc1394 -lrom1394 -lraw1394  
   libiec61883 ....... 1.2.0
     flags ...........  -liec61883 -lraw1394  
   libxml++-2.6 ...... 2.36.0
     flags ........... -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/x86_64-linux-gnu/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/x86_64-linux-gnu/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include  -lxml++-2.6 -lxml2 -lglibmm-2.4 -lgobject-2.0 -lsigc-2.0 -lglib-2.0  
   dbus-1 ............ 1.6.18
     flags ........... -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include  -ldbus-1  
 uname -a...
   Linux rosannas-pc 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Hardware...
   Host controllers:
05:01.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 46) (prog-if 10 [OHCI])
    Subsystem: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (8000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f7100000 (32-bit, non-prefetchable) [size=2K]
    Region 1: I/O ports at c000 [size=128]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: firewire_ohci


   CPU info:
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 58
Stepping:              9
CPU MHz:               2700.000
BogoMIPS:              6807.11
Virtualisation:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              6144K
NUMA node0 CPU(s):     0-3
 Configuration...
  IRQ information
Hardware Interrupts:
--------------------
 IRQ    0: PID:  None, count:      [18, 0, 0, 0], Sched None (priority None), drivers: ['timer']
 IRQ    1: PID:  None, count:       [1, 0, 1, 0], Sched None (priority None), drivers: ['i8042']
 IRQ    8: PID:  None, count:       [0, 1, 0, 0], Sched None (priority None), drivers: ['rtc0']
 IRQ    9: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['acpi']
 IRQ   12: PID:  None, count:       [4, 0, 0, 0], Sched None (priority None), drivers: ['i8042']
 IRQ   16: PID:  None, count: [316, 15, 54380, 8], Sched None (priority None), drivers: ['ehci_hcd:usb1', 'firewire_ohci']
 IRQ   17: PID:  None, count:    [47, 16, 13, 0], Sched None (priority None), drivers: ['snd_hda_intel']
 IRQ   23: PID:  None, count:   [136, 15, 8, 10], Sched None (priority None), drivers: ['ehci_hcd:usb2']
 IRQ   41: PID:  None, count:       [0, 0, 0, 0], Sched None (priority None), drivers: ['xhci_hcd']
 IRQ   42: PID:  None, count: [7086, 14918, 6685, 9034], Sched None (priority None), drivers: ['ahci']
 IRQ   43: PID:  None, count:      [15, 0, 0, 0], Sched None (priority None), drivers: ['mei_me']
 IRQ   44: PID:  None, count: [3534, 89, 101, 47], Sched None (priority None), drivers: ['snd_hda_intel']
 IRQ   45: PID:  None, count:  [32755, 23, 8, 4], Sched None (priority None), drivers: ['eth0']
 IRQ   46: PID:  None, count: [75190, 8276, 8227, 7586], Sched None (priority None), drivers: ['nvidia']


Software Interrupts:
--------------------




=== REPORT ===
FireWire kernel drivers:


The new FireWire kernel stack is loaded. 
If running a kernel earlier than 2.6.37 and problems are experienced, either 
try with the old Firewire kernel stack or upgrade to a newer kernel 
(preferrably 2.6.37 or later).



```

If anyone with more knowledge of scary things like this feels like pointing me in the right direction, I would be eternally grateful. If you need any other information, please let me know and I'll try and post it as quickly as possible.

Thank you so much.

---

