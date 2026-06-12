---
title: "USB problems"
date: 2008-11-17
forum: Hardware
---

### Post by darrenc on 2008-11-17
I've recently installed ubuntu 8.10 on my desktop system (clean install, previously using 6.4) and I'm having some USB issues I can't figure out.  Seemingly just randomly, the system loses contact with every USB device except my mouse.  I have a wifi adapter plugged into one port, and a hub plugged into the other.  On the hub, I have my mouse, an external hard drive and my printer.  When it goes, everything goes all at once - wifi drops, and the external hard drive and printer lights on the hub go out.  The mouse stays lit and continues to work.  It happens sometimes several times per day, and then sometimes it goes 2 or 3 days without happening at all.

Looking through logs, I find something similar to the following (this is from the most recent time it happened):

```
Nov 17 13:15:18 ubuntu -- MARK --
Nov 17 13:20:20 ubuntu kernel: [144338.084108] usb 4-1: USB disconnect, address 11
Nov 17 13:20:20 ubuntu kernel: [144338.405081] usb 4-1: new high speed USB device using ehci_hcd and address 12
Nov 17 13:20:35 ubuntu kernel: [144353.496194] usb 4-4: USB disconnect, address 4
Nov 17 13:20:35 ubuntu kernel: [144353.496201] usb 4-4.3: USB disconnect, address 5
Nov 17 13:20:35 ubuntu kernel: [144353.500590] usblp0: removed
Nov 17 13:20:35 ubuntu kernel: [144353.501209] usb 4-4.4: USB disconnect, address 6
Nov 17 13:20:35 ubuntu kernel: [144353.517599] sd 2:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Nov 17 13:20:35 ubuntu kernel: [144353.517736] lost page write due to I/O error on sdc1
Nov 17 13:20:35 ubuntu kernel: [144353.517759] lost page write due to I/O error on sdc1
Nov 17 13:20:35 ubuntu kernel: [144353.517775] lost page write due to I/O error on sdc1
Nov 17 13:20:35 ubuntu kernel: [144353.517789] lost page write due to I/O error on sdc1
Nov 17 13:20:35 ubuntu kernel: [144353.517802] lost page write due to I/O error on sdc1
Nov 17 13:20:36 ubuntu kernel: [144353.993037] usb 4-4: new high speed USB device using ehci_hcd and address 13
Nov 17 13:20:40 ubuntu kernel: [144358.663902] __ratelimit: 378 callbacks suppressed
Nov 17 13:20:46 ubuntu kernel: [144364.207785] __ratelimit: 6638 callbacks suppressed
Nov 17 13:20:51 ubuntu kernel: [144369.324036] usb 4-1: new high speed USB device using ehci_hcd and address 14
Nov 17 13:20:52 ubuntu kernel: [144369.735541] __ratelimit: 3303 callbacks suppressed
Nov 17 13:20:57 ubuntu kernel: [144375.236129] __ratelimit: 4038 callbacks suppressed
Nov 17 13:21:02 ubuntu kernel: [144380.307812] __ratelimit: 5869 callbacks suppressed
Nov 17 13:21:06 ubuntu kernel: [144384.656024] usb 4-4: new high speed USB device using ehci_hcd and address 15
Nov 17 13:21:08 ubuntu kernel: [144385.843187] __ratelimit: 3303 callbacks suppressed
Nov 17 13:21:13 ubuntu kernel: [144391.349091] __ratelimit: 4509 callbacks suppressed
Nov 17 13:21:22 ubuntu kernel: [144399.993088] usb 4-1: new high speed USB device using ehci_hcd and address 16
Nov 17 13:21:37 ubuntu kernel: [144415.340062] usb 4-4: new high speed USB device using ehci_hcd and address 17
Nov 17 13:21:52 ubuntu kernel: [144430.677088] usb 4-1: new high speed USB device using ehci_hcd and address 18
Nov 17 13:22:08 ubuntu kernel: [144446.009098] usb 4-4: new high speed USB device using ehci_hcd and address 19
Nov 17 13:22:23 ubuntu kernel: [144461.341077] usb 4-1: new high speed USB device using ehci_hcd and address 20
Nov 17 13:22:38 ubuntu kernel: [144476.677109] usb 4-4: new high speed USB device using ehci_hcd and address 21
Nov 17 13:22:54 ubuntu kernel: [144492.021071] usb 4-1: new high speed USB device using ehci_hcd and address 22
Nov 17 13:23:09 ubuntu kernel: [144507.361100] usb 4-4: new high speed USB device using ehci_hcd and address 23
Nov 17 13:23:24 ubuntu kernel: [144522.693207] usb 4-1: new high speed USB device using ehci_hcd and address 24
Nov 17 13:23:40 ubuntu kernel: [144538.025109] usb 4-4: new high speed USB device using ehci_hcd and address 25
Nov 17 13:23:55 ubuntu kernel: [144553.357114] usb 4-1: new high speed USB device using ehci_hcd and address 26
Nov 17 13:24:10 ubuntu kernel: [144568.689115] usb 4-4: new high speed USB device using ehci_hcd and address 27
Nov 17 13:24:26 ubuntu kernel: [144584.020018] usb 4-1: new high speed USB device using ehci_hcd and address 28
Nov 17 13:24:41 ubuntu kernel: [144599.352026] usb 4-4: new high speed USB device using ehci_hcd and address 29
Nov 17 13:24:56 ubuntu kernel: [144614.684035] usb 4-1: new high speed USB device using ehci_hcd and address 30
Nov 17 13:24:57 ubuntu kernel: [144615.001146] [drm] Num pipes: 2
Nov 17 13:24:57 ubuntu kernel: [144615.104187] __ratelimit: 2091 callbacks suppressed
Nov 17 13:24:57 ubuntu kernel: [144615.104211] seahorse-agent[5942]: segfault at b70d7480 ip b70d7480 sp bf9350dc error 4 in libnss_files-2.8.90.so[b70dc000+a000]
Nov 17 13:24:57 ubuntu kernel: [144615.114210] gnome-screensav[6007]: segfault at b6b5e480 ip b6b5e480 sp bf93c4ec error 4 in LC_CTYPE[b6b63000+3f000]
Nov 17 13:25:00 ubuntu kernel: [144617.790719] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov 17 13:25:00 ubuntu kernel: [144617.790729] apm: disabled on user request.
Nov 17 13:25:02 ubuntu bonobo-activation-server (darren-18179): could not associate with desktop session: Failed to connect to socket /tmp/dbus-glqxqh3xIv: Connection refused
Nov 17 13:25:04 ubuntu kernel: [144622.425488] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 17 13:25:06 ubuntu kernel: [144624.394854] Bluetooth: Core ver 2.13
Nov 17 13:25:06 ubuntu kernel: [144624.395562] NET: Registered protocol family 31
Nov 17 13:25:06 ubuntu kernel: [144624.395572] Bluetooth: HCI device and connection manager initialized
Nov 17 13:25:06 ubuntu kernel: [144624.395581] Bluetooth: HCI socket layer initialized
Nov 17 13:25:06 ubuntu kernel: [144624.411346] Bluetooth: L2CAP ver 2.11
Nov 17 13:25:06 ubuntu kernel: [144624.411354] Bluetooth: L2CAP socket layer initialized
Nov 17 13:25:06 ubuntu kernel: [144624.485889] Bluetooth: RFCOMM socket layer initialized
Nov 17 13:25:06 ubuntu kernel: [144624.485928] Bluetooth: RFCOMM TTY layer initialized
Nov 17 13:25:06 ubuntu kernel: [144624.485934] Bluetooth: RFCOMM ver 1.10
Nov 17 13:25:12 ubuntu kernel: [144630.016017] usb 4-4: new high speed USB device using ehci_hcd and address 31
Nov 17 13:25:27 ubuntu kernel: [144645.348015] usb 4-1: new high speed USB device using ehci_hcd and address 32
Nov 17 13:25:42 ubuntu kernel: [144660.680015] usb 4-4: new high speed USB device using ehci_hcd and address 33
Nov 17 13:25:58 ubuntu kernel: [144676.012016] usb 4-1: new high speed USB device using ehci_hcd and address 34
```

As you can see in the log, in the same second it reports that the usb was disconnected and reconnected, though obviously it's not actually being physically disconnected, and the mouse continues to work throughout all this.  Aside from the loss of all the USB devices, the system otherwise continues to function normally, but the USB devices never come back until I reboot the system.  Unplugging and replugging them has no effect.

Then when I go to reboot the system, it never shuts down.  It just goes into a continuous loop of "unable to enumerate the device on usb port...", and cycles through the ports until I finally just hit the power switch to reboot.  And I'm not just being impatient - I left it one day for over 4 hours while I ran some errands and it was still stuck in the same loop when I returned.

The system is dual-boot, so I know the hardware isn't faulty.  It has no problems at all when using the other OS.

Any suggestions on where to start trying to track this down?

Thanks.

---

### Post by Interpreter on 2008-11-23
+1 for a weird "unable to enumerate USB device on port X" problem when trying to hibernate or making use of the machine in general.

---

### Post by qhaz on 2008-12-09
I have exactly the same problem as you "darrenc"

have you found any solution/workaround yet?

---

### Post by nicov2 on 2008-12-22
i've had the same problem, too, and i've also noticed the "unable to enumerate usb" line on boot-up. sometimes it'll even display that line several to many times in a row. i haven't seen any solutions or workarounds for this yet.

---

### Post by maddox on 2008-12-23
I have the same problem "unable to enumerate USB device on port..." with one of my USB devices, a USB IR RECEIVER for Skystar HD 2.

kernel  2.6.27-11-generic

does anyone knows howto solve this?

thanks

---

### Post by serapis5 on 2008-12-27
Like darrenc and nicov2, I was getting the same "unable to enumerate USB device on port 2" during startup.  In my case, it's an old USB device, Microsoft Digital Sound System 80, which linux actually recognizes and supports (lsusb and dmesg | tail do not show the error once linux is actually booted).  The error disappears when I unplug the USB and just use analog, but it has caused a lot of grief for both Ubuntu and Open Solaris.  the only workaround I have been able to come up with is to unplug this device while I install.  If I plug it back in after installation, I get the error on bootup, but it doesn't crash my system.  However, that's only in linux.  Open Solaris just hates it, pure and simple, (I'm not particularly enamored of that OS anyway).  Hope this helps, but sorry that I didn't have an actual solution for anyone.

---

