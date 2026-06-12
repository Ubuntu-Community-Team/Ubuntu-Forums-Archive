---
title: "Gnome freezing"
date: 2008-07-17
forum: General Help
---

### Post by Dekafox on 2008-07-17
This has happened a few times after a patch a few weeks ago, and usually only after several days uptime. Usually I only first realize it happened after trying to start WoW under WINE, since the first symptom I've noticed is it being unbearably slow to bring up the program itself(on the order of 5 minutes compared to 10 seconds) and no sound when it does. After this point terminals won't start normally, I couldn't get Firefox to start, and trying to use alt-F2 to start anything in a console or trying to launch the system monitor freezes the GUI.  Nautilus windows also won't start up properly.

I can ctrl-alt-backspace to restart GNOME, but when I login, nothing seems to happen for about 15-30 seconds, and then a little grey square appears in the upper left corner. I see no text in it, though when I mouse over it I get a text selection icon.

I tried a compiz --replace when I was lucky enough to have had a terminal up already(as the GUI freeze only affects programs started after the freeze happens), and it freezes up partway through.

I'm running the x64 distro, system specs are a AMD X2 4600 AM2 on a Gigabyte GA-M57SLI-S4 motherboard, 4GB RAM, nVidia 8800GT vidcard with GDDR3 memory, though I can't remember the exact amount right now. I'm only running Compiz at the Normal effects level, no floating cube or anything.

I found this in the log, and I think it was from my ctrl-alt-backspacing or my compiz restart attempt:

```
Jul 15 19:05:13 Iacon gdm[5665]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 15 19:05:56 Iacon gdm[17111]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 15 19:06:14 Iacon gdm[17216]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Jul 15 19:06:14 Iacon gdm[17216]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
Jul 15 19:06:14 Iacon gdm[17264]: Gtk-WARNING: Ignoring the separator setting 
Jul 15 19:07:29 Iacon gdm[17216]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 15 19:08:12 Iacon gdm[17343]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Jul 15 19:08:12 Iacon gdm[17343]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
Jul 15 19:08:12 Iacon gdm[17388]: Gtk-WARNING: Ignoring the separator setting
```

Anyone know anything I can try to fix this?  This is getting really annoying now, since the only fix when it happens so far is a full restart of the machine.

*edit*  just tried running a compiz --replace through alt-F2... it looks like it worked, but did no good, as the console still freezes on launch.

*edit 2* found this in /var/log/messages:
Jul 17 19:02:54 Iacon kernel: [86023.694258] firefox[15359]: segfault at 7f143a1c7e8a rip 7f143cac7871 rsp 7fff45dd7340 error 4

One of the previous times it happened I saw a similar error 4 segfault in compiz.real:
Jul 8 18:15:47 Iacon kernel: [389208.345244] compiz.real[6019]: segfault at 12f59 rip 40fee0 rsp 7fff6abf6120 error 4

---

### Post by Dekafox on 2008-07-26
Well it seems like no one's willing to help, but just in case:

Wasn't up for long this time(power outage)  I brought it back up, installed a wine patch while I read some stuff, then tried to launch WoW, and the same situation cropped up again.  the messages log gives this:

```
Jul 26 06:08:11 Iacon kernel: [  718.007181] compiz.real[6061] trap stack segment rip:40fee0 rsp:7fffccd59e20 error:0
```

I'm beginning to wonder if it's an issue with wine though, since these freezes only seems to trigger or at least become noticeable when I try to launch WoW.

Doesn't look like anyone cares, but I'll keep an eye out and see when it happens next for some clues, in the hope that MAYBE there's SOMEONE out there who's seen this before, or runs into this in the future.

---

### Post by Dekafox on 2008-07-31
Again triggered the same time both times today.  I tried killing and restarting gdm from the console, forcing a reload on it and X11-common, and neither helped.  I did discover that the grey box I see when it freezes loading the gdm is in the exact same place a usable console shows up if I run xinit from a console.  Does THIS give anyone any ideas?

I mean come on, I know I'm still relatively new to Linux, but it would be appreciated if I knew someone was even READING this?  It's beginning to get really frustrating.  Even a "I don't know" or a couple commands or further places to look would be appreciated!

*points at name of the forum*  This is a help forum after all, and I see lots of other topics that get answers, but I've been having this problem for over a month and not a single person has made a single suggestion on what to do next.  Some help forum.:(

---

### Post by Dekafox on 2008-09-15
Sorry for the tone of my previous post but I was rather frustrated.  I still don't know what's triggering it, but I have my suspicions based on the cause.

Pulseaudio locking up seems to be the root cause of the freeze.  If I alt-F2 and do "killall -9 pulseaudio" performance returns to normal, and then once I restart the pulseaudio process everything is all hunky-dory again.

As to what's triggering the freeze, I'm still not sure, but I am routing the WoW audio through padsp, so something in there seems to be at fault.

---

### Post by normeo on 2008-10-02
I have this problem, I loose sound and i click the power button and i am unable to get the shutdown/logoff/restart menu, nothing happens. I am sometimes unable to move/minimize windows. If and I mean if i can get onto the applications menu and click terminal that loads but just the windows and it is greyed out and have to force quit (same thing if i double click the volume control icon). I will usually try and Alt+Ctrl+Backspace to drop to login and restart from there as i have done a hard reboot and screwed the filesystem once before and reinstalled. I have noticed it happens quite a bit when running flash content in firefox but also when running various other applications like open office. I have noticed this happens alot with nvidia hardware. But there seems to be no solution

Sorry i don't know how to format this any better

my hardware:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


The offending error as much as I can figure as seen in /var/log/messages

compiz.real[5947]: segfault at 03250316 eip 08055a80 esp bfccfe10 error 4

I have currently disabled compiz because it was doing my head in, I am quite confident it is compiz. Im going to re-enable it so when it crashes i can gather some more evidence.

---

