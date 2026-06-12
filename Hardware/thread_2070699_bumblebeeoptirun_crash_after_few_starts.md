---
title: "bumblebee/optirun crash after few starts"
date: 2012-10-13
forum: Hardware
---

### Post by Meschi on 2012-10-13
Hello everyone!

I am new to this forum therefore I hope that I am not violating any rules in my post. If this is the case I would be glad if someone tells me ;).

First about my _system_:

I am running a notebook from packard bell (Modell: EasyNoteTX86) in dual boot configuration (windows 7 64 bit and ubuntu 12.04 LTS 64 bit) which uses the nvidia optimus technology :

```

uname -a
Linux EasyNote-TX86 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

``````

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
02:00.0 VGA compatible controller: NVIDIA Corporation Device 0df1 (rev ff)

```To use the nvidia card (Geforce GT 420M) only if needed I installed bumblebee sucessfully (at least I do think so) in the following way: 
I started with a fresh ubuntu 12.04 LTS system and used the following commands:
```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get purge nvidia-current
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install bumblebee

```I am not perfectly sure if i did everything right here but my intention was to get the bumblebee ppa, remove the old nvidia driver and get the new one from the x-swat ppa. It must have worked (in some way) because now I am able to start optirun (I had to edit the bumblebee.conf file as Ubuntu should need the options  "Driver=nvidia" "KernelDriver=nvidia").

Now the following _behavior_ occurs:
The time when an error happens is always a little bit different. Sometimes the error happens at the first optirun command but most of the time it happens on the 
second or third execution (and works as wished the times executed before). The effect of running optirun not succesfully always is fatal: The system stays alive for some time but then the desktop freezes or it changes to a text console like output. In every case the notebook has to to be turned off by pressing the power button because nothing else does work anymore.

By looking at the kernel.log file and with the [FONT=Courier New]optirun -vv[/FONT] command I found that for any reason optirun is not able to turn on the nvidia card again and that is must have to do something with ACPI. I do not have any idea how this could be fixed so maybe someone of you has a working idea :).

Here are the outputs and files after optirun has been run sucessfully:
[FONT=Courier New]optirun -vv[/FONT] [FONT=Courier New]glxspheres[/FONT] returns

```

[ 2892.926385] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 2892.926651] [INFO]Configured driver: nvidia
[ 2893.104483] [DEBUG]optirun version 3.0.1 starting...
[ 2893.104510] [DEBUG]Active configuration:
[ 2893.104517] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 2893.104523] [DEBUG] X display: :8
[ 2893.104529] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-current:/usr/lib32/nvidia-current
[ 2893.104535] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 2893.104542] [DEBUG] VGL Compression: proxy
[ 2896.906384] [INFO]Response: Yes. X is active.

[ 2896.906422] [INFO]Running application through vglrun.
[ 2896.906596] [DEBUG]Process vglrun started, PID 2416.
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 420M/PCIe/SSE2

[ 2940.473081] [WARN]Received Interrupt signal.
[ 2940.473130] [DEBUG]Socket closed.
[ 2940.504964] [DEBUG]SIGCHILD received, but wait failed with No child processes
[ 2940.504992] [DEBUG]Socket closed.
[ 2940.505003] [DEBUG]Killing all remaining processes.


```and the kernel.log relevant output is:

```

Oct 13 12:55:18 EasyNote-TX86 kernel: [   17.534965] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.593501] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.594879] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608119] Bluetooth: Core ver 2.16
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608136] NET: Registered protocol family 31
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608138] Bluetooth: HCI device and connection manager initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608140] Bluetooth: HCI socket layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608141] Bluetooth: L2CAP socket layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608145] Bluetooth: SCO socket layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.653643] Bluetooth: RFCOMM TTY layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.653650] Bluetooth: RFCOMM socket layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.653652] Bluetooth: RFCOMM ver 1.11
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.715890] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.715893] Bluetooth: BNEP filters: protocol multicast
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.044838] bbswitch: version 0.4.2
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.044845] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.044854] bbswitch: Found discrete VGA device 0000:02:00.0: \_SB_.PCI0.P0P2.PEGP
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.045135] bbswitch: detected an Optimus _DSM function
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.045142] bbswitch: Succesfully loaded. Discrete card 0000:02:00.0 is on
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.046882] bbswitch: disabling discrete graphics
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.047131] bbswitch: Result of Optimus _DSM call: 09000001
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.060021] pci 0000:02:00.0: power state changed by ACPI to D3
Oct 13 12:55:20 EasyNote-TX86 kernel: [   19.496194] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
Oct 13 12:55:52 EasyNote-TX86 kernel: [   50.470959] eth1: no IPv6 routers present
Oct 13 13:43:14 EasyNote-TX86 kernel: [ 2886.206868] bbswitch: enabling discrete graphics
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621578] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621589] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621611] pci 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621622] pci 0000:02:00.0: restoring config space at offset 0x9 (was 0x1, writing 0x2001)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621628] pci 0000:02:00.0: restoring config space at offset 0x7 (was 0xc, writing 0xae00000c)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621634] pci 0000:02:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xb000000c)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621640] pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xac000000)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621645] pci 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621651] pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100104)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621669] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621674] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621679] pci 0000:02:00.0: enabling device (0104 -> 0107)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621689] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621695] pci 0000:02:00.0: setting latency timer to 64
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079716] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079721] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079726] nvidia 0000:02:00.0: enabling device (0104 -> 0107)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079735] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079744] nvidia 0000:02:00.0: setting latency timer to 64
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079751] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079860] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.51  Tue Sep 18 17:16:56 PDT 2012
Oct 13 13:43:16 EasyNote-TX86 kernel: [ 2888.262576] ACPI Error: [\_SB_.PCI0.P0P2.PEGP.SPB_] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Oct 13 13:43:16 EasyNote-TX86 kernel: [ 2888.262583] ACPI Error: Method parse/execution failed [\_SB_.PCI0.P0P2.PEGP._DSM] (Node ffff880150c6f938), AE_NOT_FOUND (20110623/psparse-536)
Oct 13 13:43:17 EasyNote-TX86 kernel: [ 2889.324938] NVRM: GPU at 0000:02:00: GPU-3f83de1f-7515-c144-5792-600c2f807dab
Oct 13 13:43:45 EasyNote-TX86 kernel: [ 2916.900481] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Oct 13 13:43:45 EasyNote-TX86 kernel: [ 2916.900488] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
Oct 13 13:43:45 EasyNote-TX86 kernel: [ 2916.907573] atkbd serio0: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Oct 13 13:43:45 EasyNote-TX86 kernel: [ 2916.907578] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
Oct 13 13:43:46 EasyNote-TX86 kernel: [ 2917.435927] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Oct 13 13:43:46 EasyNote-TX86 kernel: [ 2917.435932] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
Oct 13 13:43:46 EasyNote-TX86 kernel: [ 2917.443274] atkbd serio0: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Oct 13 13:43:46 EasyNote-TX86 kernel: [ 2917.443277] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.675438] nvidia 0000:02:00.0: PCI INT A disabled
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.678411] bbswitch: disabling discrete graphics
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.679031] bbswitch: Result of Optimus _DSM call: 09000001
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.691202] pci_raw_set_power_state: 37 callbacks suppressed
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.691212] pci 0000:02:00.0: Refused to change power state, currently in D0
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.691518] pci 0000:02:00.0: power state changed by ACPI to D3

```These are the outputs and files after optirun has been run _not_ sucessfully:
[FONT=Courier New]optirun -vv glxspheres[/FONT] returns

```

[ 3481.735045] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 3481.735599] [INFO]Configured driver: nvidia
[ 3481.868127] [DEBUG]optirun version 3.0.1 starting...
[ 3481.868154] [DEBUG]Active configuration:
[ 3481.868160] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 3481.868167] [DEBUG] X display: :8
[ 3481.868172] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-current:/usr/lib32/nvidia-current
[ 3481.868178] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 3481.868184] [DEBUG] VGL Compression: proxy
[ 3482.613635] [INFO]Response: No - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please

[ 3482.613673] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please

[ 3482.613690] [DEBUG]Socket closed.
[ 3482.613719] [ERROR]Aborting because fallback start is disabled.
[ 3482.613740] [DEBUG]Killing all remaining processes.


```and the kernel.log output is (starting time is the same as above):

```

Oct 13 12:55:18 EasyNote-TX86 kernel: [   17.534965] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.593501] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.594879] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608119] Bluetooth: Core ver 2.16
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608136] NET: Registered protocol family 31
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608138] Bluetooth: HCI device and connection manager initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608140] Bluetooth: HCI socket layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608141] Bluetooth: L2CAP socket layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.608145] Bluetooth: SCO socket layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.653643] Bluetooth: RFCOMM TTY layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.653650] Bluetooth: RFCOMM socket layer initialized
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.653652] Bluetooth: RFCOMM ver 1.11
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.715890] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 13 12:55:19 EasyNote-TX86 kernel: [   17.715893] Bluetooth: BNEP filters: protocol multicast
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.044838] bbswitch: version 0.4.2
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.044845] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.044854] bbswitch: Found discrete VGA device 0000:02:00.0: \_SB_.PCI0.P0P2.PEGP
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.045135] bbswitch: detected an Optimus _DSM function
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.045142] bbswitch: Succesfully loaded. Discrete card 0000:02:00.0 is on
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.046882] bbswitch: disabling discrete graphics
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.047131] bbswitch: Result of Optimus _DSM call: 09000001
Oct 13 12:55:19 EasyNote-TX86 kernel: [   18.060021] pci 0000:02:00.0: power state changed by ACPI to D3
Oct 13 12:55:20 EasyNote-TX86 kernel: [   19.496194] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
Oct 13 12:55:52 EasyNote-TX86 kernel: [   50.470959] eth1: no IPv6 routers present
Oct 13 13:43:14 EasyNote-TX86 kernel: [ 2886.206868] bbswitch: enabling discrete graphics
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621578] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621589] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621611] pci 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621622] pci 0000:02:00.0: restoring config space at offset 0x9 (was 0x1, writing 0x2001)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621628] pci 0000:02:00.0: restoring config space at offset 0x7 (was 0xc, writing 0xae00000c)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621634] pci 0000:02:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xb000000c)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621640] pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xac000000)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621645] pci 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621651] pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100104)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621669] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621674] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621679] pci 0000:02:00.0: enabling device (0104 -> 0107)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621689] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2886.621695] pci 0000:02:00.0: setting latency timer to 64
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079716] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079721] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079726] nvidia 0000:02:00.0: enabling device (0104 -> 0107)
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079735] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079744] nvidia 0000:02:00.0: setting latency timer to 64
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079751] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
Oct 13 13:43:15 EasyNote-TX86 kernel: [ 2887.079860] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.51  Tue Sep 18 17:16:56 PDT 2012
Oct 13 13:43:16 EasyNote-TX86 kernel: [ 2888.262576] ACPI Error: [\_SB_.PCI0.P0P2.PEGP.SPB_] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Oct 13 13:43:16 EasyNote-TX86 kernel: [ 2888.262583] ACPI Error: Method parse/execution failed [\_SB_.PCI0.P0P2.PEGP._DSM] (Node ffff880150c6f938), AE_NOT_FOUND (20110623/psparse-536)
Oct 13 13:43:17 EasyNote-TX86 kernel: [ 2889.324938] NVRM: GPU at 0000:02:00: GPU-3f83de1f-7515-c144-5792-600c2f807dab
Oct 13 13:43:45 EasyNote-TX86 kernel: [ 2916.900481] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Oct 13 13:43:45 EasyNote-TX86 kernel: [ 2916.900488] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
Oct 13 13:43:45 EasyNote-TX86 kernel: [ 2916.907573] atkbd serio0: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Oct 13 13:43:45 EasyNote-TX86 kernel: [ 2916.907578] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
Oct 13 13:43:46 EasyNote-TX86 kernel: [ 2917.435927] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Oct 13 13:43:46 EasyNote-TX86 kernel: [ 2917.435932] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
Oct 13 13:43:46 EasyNote-TX86 kernel: [ 2917.443274] atkbd serio0: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Oct 13 13:43:46 EasyNote-TX86 kernel: [ 2917.443277] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.675438] nvidia 0000:02:00.0: PCI INT A disabled
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.678411] bbswitch: disabling discrete graphics
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.679031] bbswitch: Result of Optimus _DSM call: 09000001
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.691202] pci_raw_set_power_state: 37 callbacks suppressed
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.691212] pci 0000:02:00.0: Refused to change power state, currently in D0
Oct 13 13:44:02 EasyNote-TX86 kernel: [ 2933.691518] pci 0000:02:00.0: power state changed by ACPI to D3
Oct 13 13:52:43 EasyNote-TX86 kernel: [ 3453.705763] bbswitch: enabling discrete graphics
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122849] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122862] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122888] pci 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122900] pci 0000:02:00.0: restoring config space at offset 0x9 (was 0x1, writing 0x2001)
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122908] pci 0000:02:00.0: restoring config space at offset 0x7 (was 0xc, writing 0xae00000c)
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122915] pci 0000:02:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xb000000c)
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122921] pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xac000000)
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122930] pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122950] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122956] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122968] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.122976] pci 0000:02:00.0: setting latency timer to 64
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.177439] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.177444] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.177454] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.177463] nvidia 0000:02:00.0: setting latency timer to 64
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.177471] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=none,decodes=none:owns=none
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.177608] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.51  Tue Sep 18 17:16:56 PDT 2012
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.210776] ACPI Error: [\_SB_.PCI0.P0P2.PEGP.SPB_] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Oct 13 13:52:44 EasyNote-TX86 kernel: [ 3454.210783] ACPI Error: Method parse/execution failed [\_SB_.PCI0.P0P2.PEGP._DSM] (Node ffff880150c6f938), AE_NOT_FOUND (20110623/psparse-536)
Oct 13 13:52:45 EasyNote-TX86 kernel: [ 3455.320406] NVRM: GPU at 0000:02:00: GPU-3f83de1f-7515-c144-5792-600c2f807dab
Oct 13 13:52:49 EasyNote-TX86 kernel: [ 3459.373716] nvidia 0000:02:00.0: PCI INT A disabled
Oct 13 13:52:49 EasyNote-TX86 kernel: [ 3459.376601] bbswitch: disabling discrete graphics
Oct 13 13:52:49 EasyNote-TX86 kernel: [ 3459.377217] bbswitch: Result of Optimus _DSM call: 09000001
Oct 13 13:52:49 EasyNote-TX86 kernel: [ 3459.389502] pci 0000:02:00.0: Refused to change power state, currently in D0
Oct 13 13:52:49 EasyNote-TX86 kernel: [ 3459.389805] pci 0000:02:00.0: power state changed by ACPI to D3
Oct 13 13:52:52 EasyNote-TX86 kernel: [ 3462.885503] bbswitch: enabling discrete graphics
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307883] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307898] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307922] pci 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307934] pci 0000:02:00.0: restoring config space at offset 0x9 (was 0x1, writing 0x2001)
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307942] pci 0000:02:00.0: restoring config space at offset 0x7 (was 0xc, writing 0xae00000c)
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307949] pci 0000:02:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xb000000c)
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307956] pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xac000000)
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307964] pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307984] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.307990] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.308001] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.308009] pci 0000:02:00.0: setting latency timer to 64
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.359297] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.359301] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.359310] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.359317] nvidia 0000:02:00.0: setting latency timer to 64
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.359323] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=none,decodes=none:owns=none
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.359438] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.51  Tue Sep 18 17:16:56 PDT 2012
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.393352] ACPI Error: [\_SB_.PCI0.P0P2.PEGP.SPB_] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Oct 13 13:52:53 EasyNote-TX86 kernel: [ 3463.393359] ACPI Error: Method parse/execution failed [\_SB_.PCI0.P0P2.PEGP._DSM] (Node ffff880150c6f938), AE_NOT_FOUND (20110623/psparse-536)
Oct 13 13:52:54 EasyNote-TX86 kernel: [ 3464.458500] NVRM: GPU at 0000:02:00: GPU-3f83de1f-7515-c144-5792-600c2f807dab
Oct 13 13:53:00 EasyNote-TX86 kernel: [ 3470.681438] nvidia 0000:02:00.0: PCI INT A disabled
Oct 13 13:53:00 EasyNote-TX86 kernel: [ 3470.684386] bbswitch: disabling discrete graphics
Oct 13 13:53:00 EasyNote-TX86 kernel: [ 3470.685004] bbswitch: Result of Optimus _DSM call: 09000001
Oct 13 13:53:00 EasyNote-TX86 kernel: [ 3470.701129] pci 0000:02:00.0: Refused to change power state, currently in D0
Oct 13 13:53:00 EasyNote-TX86 kernel: [ 3470.701464] pci 0000:02:00.0: power state changed by ACPI to D3
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.498443] bbswitch: enabling discrete graphics
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921216] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921230] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921254] pci 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921266] pci 0000:02:00.0: restoring config space at offset 0x9 (was 0x1, writing 0x2001)
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921274] pci 0000:02:00.0: restoring config space at offset 0x7 (was 0xc, writing 0xae00000c)
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921282] pci 0000:02:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xb000000c)
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921288] pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xac000000)
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921297] pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921317] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921323] pci 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921335] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:53:03 EasyNote-TX86 kernel: [ 3473.921344] pci 0000:02:00.0: setting latency timer to 64
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3473.974971] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3473.974979] nvidia 0000:02:00.0: power state changed by ACPI to D0
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3473.974992] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3473.975004] nvidia 0000:02:00.0: setting latency timer to 64
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3473.975013] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=none,decodes=none:owns=none
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3473.975191] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.51  Tue Sep 18 17:16:56 PDT 2012
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3474.007894] ACPI Error: [\_SB_.PCI0.P0P2.PEGP.SPB_] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3474.007901] ACPI Error: Method parse/execution failed [\_SB_.PCI0.P0P2.PEGP._DSM] (Node ffff880150c6f938), AE_NOT_FOUND (20110623/psparse-536)
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3474.134068] ACPI Error: Wrong object type in field I/O 20 (20110623/exfldio-528)
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3474.134079] ACPI Error: Method parse/execution failed [\_SB_.PCI0.P0P2.PEGP._ROM] (Node ffff880150c6f898), AE_AML_INTERNAL (20110623/psparse-536)
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3474.134119] NVRM: failed to copy vbios to system memory.
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3474.139490] NVRM: RmInitAdapter failed! (0x30:0xffffffff:861)
Oct 13 13:53:04 EasyNote-TX86 kernel: [ 3474.139506] NVRM: rm_init_adapter(0) failed

```Thank you for taking the time to look at my question. I am looking forward to your answers!

Greetings, Meschi

---

