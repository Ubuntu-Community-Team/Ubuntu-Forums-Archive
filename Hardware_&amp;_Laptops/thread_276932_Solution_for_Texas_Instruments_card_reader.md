---
title: "Solution for Texas Instruments card reader"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by olaf-g on 2006-10-13
I have a HP nc6120 notebook running dapper. Every piece of hardware worked nicely out of the boy except the card reader. But now I made it work.

Prerequisites:
[LIST]
[*]kernel 2.6.15-25 (tested)
[*]fakephp kernel module
[*]sdhci kernel module
[*]knowledge about init scripts
[/LIST]

First figure out the PCI address of the card reader:
```
lspci | grep 'Texas Instruments PCIxx21'
```
You will get something like this:
```

0000:02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:02:06.1 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

```

The Cardbus of cause does not interrest us but the FlashMedia Controller. So on my machine it sits on 02:06.3

Now just take the following init script, lets call it sdhci and adjust it to your needs (replace the 02:06.3 by your machine's value) and copy it to /etc/init.d

```

#!/bin/sh

# Get lsb functions
. /lib/lsb/init-functions

case "$1" in

start)
        log_begin_msg "Configuring card reader"

        modprobe fakephp || return 1
        setpci -s 02:06.3 86.b=90
        setpci -s 02:06.3 4c.b=02 # FlashMedia SD disable
        setpci -s 02:06.3 04.b=06 # SDHCI Mem+ BusMaster+
        setpci -s 02:06.3 88.b=01 # SDHCI DMA enable
        modprobe sdhci || return 1

        log_end_msg $?
	;;

stop)
        log_begin_msg "Shutting down card reader"

        modprobe -r sdhci
        lsmod | grep -q sdhci && return 1
        setpci -s 02:06.3 88.b=00 # SDHCI DMA disable
        setpci -s 02:06.3 04.b=07 # SDHCI Mem- BusMaster-
        setpci -s 02:06.3 4c.b=00 # FlashMedia SD enable
        setpci -s 02:06.3 86.b=d0
        modprobe -r fakephp

        log_end_msg $?
	;;


*)
    log_success_msg "Usage: /etc/init.d/sdhci start|stop"
    exit 1
    ;;
esac

exit 0

```

Fire it up: sudo /etc/init.d/sdhci start and try to insert a card. monitoring /var/log/messages and dmesg might give you hints. My dmesg comes up with this:
```
[17179602.788000] sdhci: ============== REGISTER DUMP ==============
[17179602.788000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179602.788000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179602.788000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179602.788000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179602.788000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179602.788000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179602.788000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179602.788000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179602.788000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179602.788000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179602.788000] sdhci: ===========================================
[17179602.840000] mmc0: SDHCI at 0xd000a000 irq 233 DMA
[17179602.940000] sdhci: ============== REGISTER DUMP ==============
[17179602.940000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179602.940000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179602.940000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179602.940000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179602.940000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179602.940000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179602.940000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179602.940000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179602.940000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179602.940000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179602.940000] sdhci: ===========================================
[17179602.992000] mmc1: SDHCI at 0xd000b000 irq 233 DMA
[17179603.088000] sdhci: ============== REGISTER DUMP ==============
[17179603.088000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179603.088000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179603.088000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179603.088000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179603.088000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179603.088000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179603.088000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179603.088000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179603.088000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179603.088000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[17179603.088000] sdhci: ===========================================
[17179603.140000] mmc2: SDHCI at 0xd000c000 irq 233 DMA

```

Everything is on DMA and not PIO... nice, eh.

If everything works out nicely add it to your system v initialization.

If you run into problems when hibernating/suspending just add the sdhci service to blacklist.

Hope it works for you, too

Cheers

Olaf

---

### Post by phen on 2006-10-14
thanks olaf, i'll try that the weekend :) that's what was left for 100% compatibility

---

### Post by jonasren on 2006-10-20
Thanks! After switching from 64bit to the 32bit distribution my card reader did not function. Now it is working perfectly. :)

---

### Post by nalmeth on 2006-10-20
Would this work for the pci slots aswell??
I've never gotten my working wireless card to work in linux, and I'm sure it's the Texas Instruments PCI slots.
You point out this fix is for a card reader, it looks like storage media?
Would this work to enable these PCI slots
$ lspci | grep 'Texas Instruments PCI*'
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1420
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1420

---

### Post by olaf-g on 2006-10-27
I'm happy to hear that it works for other's, too. Anyway, upgrading to edgy should fix it as it uses kernel 2.6.17 which initializes our little friend correctly.


@nalmeth:

Hmm... I guess it won't work for your device. This hack is specific for this very FlashMedia Controller.

Just try to google for your device and linux - that's what I did.

Good luck


Olaf

---

### Post by Vladtux on 2006-10-29
Hey dude your tip help to fix my problems with the card reader thnxks!!! :mrgreen: 


This is my hardware and Kernel

2.6.17-10-generic ubuntu edgy :)
laptop HP 6131us

The rest work perflectly:

Keys multimedia.
wireless (ndiswrapper).
suspend.
acceleration (no test)


Thnxks Again..

Vlad

---

### Post by magicker71 on 2006-12-16
Works great, thanks so much!  I am running Edgy but still had to use this script on my Com
paq v2000 laptop.

Just in case there's any complete Linux idiots like me trying this, after saving this into the /etc/init.d directory I had to type

chmod +x /etc/init.d/sdhci

to make the script executable.

---

### Post by i.wanna.corndog on 2006-12-19
Hmmm...worked great to get my SD cards read, but did not work for the XD card my Olympus takes. Any clues? Oh, and I'm a newbie at Linux, how do I add it to my system initialization?

Thanks,
Dan

---

### Post by i.wanna.corndog on 2006-12-21
Okay I checked /var/log/messages and here's what I get when I insert an XD card:

```
Dec 21 11:49:44 curiouslystrong kernel: [17181906.476000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
Dec 21 11:49:44 curiouslystrong kernel: [17181906.476000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
Dec 21 11:49:44 curiouslystrong kernel: [17181906.476000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
Dec 21 11:49:44 curiouslystrong kernel: [17181906.892000] tifm_7xx1: xd card detected in socket 2

```

Any clues as to what I do next? I am assuming the sdhci is only for SD cards, so what would be the next step in getting XD cards working?

Thanks,
Dan

---

### Post by cisoprogressivo on 2007-02-05
> **i.wanna.corndog said:**
> Okay I checked /var/log/messages and here's what I get when I insert an XD card:

```
Dec 21 11:49:44 curiouslystrong kernel: [17181906.476000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
Dec 21 11:49:44 curiouslystrong kernel: [17181906.476000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
Dec 21 11:49:44 curiouslystrong kernel: [17181906.476000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
Dec 21 11:49:44 curiouslystrong kernel: [17181906.892000] tifm_7xx1: xd card detected in socket 2

```

Any clues as to what I do next? I am assuming the sdhci is only for SD cards, so what would be the next step in getting XD cards working?

Thanks,
Dan
exactly the same problem :(

---

### Post by tacm on 2007-02-23
any chance of walking a noob throught this??

---

### Post by macogw on 2007-02-24
Or much shorter that fixes it...
add this to /etc/modules

tifm_core
tifm_7xx1
tifm_sd

i posted that in the bug report and on the wiki cuz that's how you fix it.

---

