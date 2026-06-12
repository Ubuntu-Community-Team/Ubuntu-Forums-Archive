---
title: "Need debugging help - it just stops"
date: 2024-07-22
forum: Hardware
---

### Post by linwood2 on 2024-07-22
I have an intel NUC11TNHV5, which is an I5-1145G7, with 32gb good memory (G.Skill RipJaws), and a Samsung 980 Pro NVMe as system disk (500gb), with ubuntu 22.04.04 in a pretty vanilla setup.  It serves as the brains of a player piano system, running a custom QT application I wrote, as well as Kobe. Only devices hooked up are a monitor (with touchscreen via USB), several USB serial devices used for MIDI and similar functions, no in-chassis devices.  And all these devices were idle when it hangs. 

When the system is just sitting there it periodically just -- stops.  The screen saver is on (before this happens), there is nothing on the screen and it will not come up.  It is not accessible from the network.

If I reboot/reset, the syslog shows nothing helpful.   The last entry before the reboot is innocuous.  You can see it in the syslog below.  This has happened a half dozen times or so, I never see anything interesting.  The time between hangs is maybe 3-12 days.  There's no hint of any related issue like power problems (while this is not on a UPS I have a bunch of them in the house and they do not show any power event at the time). 

I have updated the uefi to current with no change in behavior.  I've reviewed all settings and see nothing unusual. No attempt at over-clocking or anything like that (not sure this one even can). 

The only consistent things are that the failure leaves no trail (at least I can find), and occurs when the system is idle.  Though it's idle 98% of the time so that's not terribly meaningful. 

I have zabbix running on the system (network/system monitor).  Polling stops when it hangs of course, but the last poll shows nothing unusual - negligable CPU, memory usage, etc. 

I have used this hardware for a year or so.  The only change that I can think of that seems related to the timing is moving from a hard wired ethernet to using wifi.  The piano is in a different place where I do not have ethernet readily available.  I do not get wifi errors however, and it's in an area with a very strong signal (wifi 6, circa -60dBm).  The AP shows a simple disconnect at the time of the hang, nothing unusual, good single. 

I'm looking for ideas.  Getting ethernet to this means running a wire down a hall and putting a switch in somewhere in the middle, but that is probably my next idea.  Ugly (literally). 

Anything else I can check?  Any other setting I can put in that might yield more information when it fails again?

Linwood

```

Jul 22 09:26:50 piano NetworkManager[550]: <info>  [1721654810.0279] dhcp4 (wlo1): state changed new lease, address=192.168.130.55Jul 22 09:30:01 piano CRON[56491]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
Jul 22 09:32:55 piano systemd[1]: Started Run anacron jobs.
Jul 22 09:32:55 piano systemd[1]: anacron.service: Deactivated successfully.
Jul 22 09:32:55 piano anacron[56529]: Anacron 2.3 started on 2024-07-22
Jul 22 09:32:55 piano anacron[56529]: Normal exit (0 jobs run)
Jul 22 17:00:37 piano systemd-modules-load[281]: Inserted module 'lp'
Jul 22 17:00:37 piano systemd-modules-load[281]: Inserted module 'ppdev'
Jul 22 17:00:37 piano systemd-modules-load[281]: Inserted module 'parport_pc'
Jul 22 17:00:37 piano systemd[1]: Reached target Swaps.
Jul 22 17:00:37 piano systemd[1]: Starting Flush Journal to Persistent Storage...

```

---

### Post by currentshaft on 2024-07-22
Disconnect unnecessary peripheral devices to rule them out. Connect to the computer remotely (e.g., over SSH) to rule out a graphical display issue. Check other logs besides syslog for additional clues.

---

### Post by linwood2 on 2024-07-22
Removing peripherals is hard as it makes the piano useless.  If this was reproducible reasonably quickly I would not worry, but that's further down on my list.

ssh won't help, since the network is gone (no ping, no arp response) when this happens, so if I was ssh'd in when this occurs, I will simply get disconnected. 

I browsed through logs without seeing anything relevant (generally speaking without seeing anything near the time of the hang). 

FWIW here's what's hanging on the USB bus: 

```

root@piano:/var/log# lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 18d1:5025 Google Inc. USB-C to 3.5mm-Headphone Adapter
Bus 003 Device 009: ID 0bda:1100 Realtek Semiconductor Corp. HID Device
Bus 003 Device 008: ID 1fd2:9102 Melfas LGDisplay Incell Touch
Bus 003 Device 007: ID 0bda:5411 Realtek Semiconductor Corp. RTS5411 Hub
Bus 003 Device 005: ID 2222:2222 MacAlly
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 002: ID 4348:562d WinChipHead USB Midi
Bus 003 Device 006: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

None of this stuff has changed by the way, the only change in environment (other than regular APT updates) is the switch from ethernet to wifi.

---

### Post by currentshaft on 2024-07-22
You said the screensaver is on when this happens. Is it possible the system is going into suspend/hibernation and failing to wake up?

Can you do a quick "systemctl suspend" to test the behavior?

---

### Post by linwood2 on 2024-07-22
So, we may have a "Bingo". 

systemctl suspend put it instantly into a sleep mode, took it off the network.  Touching the screen (like moving the mouse) did nothing.  I went and got a real keyboard and plugged it in, no reaction.  The power button light was flashing, I pushed it and it came back up to a login screen, but when I logged in it went blank (not black though) and hung.  I could log in via ssh and rebooted and it came up normally. 

So there's a couple things: First is I do not recall the power button flashing when the spontaneous hang occurs.  I am not certain (and this NUC is buried up under the piano so I have to crawl under and dig through a bunch of cables to see it so... not certain).  I may have to wait for the next even to know if this is the issue.

Also, I have the GUI set to blank the screen but not suspend the machine.  Which begs the question, other than the above command, what can put it into suspend mode if it's told not to suspend (and very infrequently, it may be days between me touching the screen at times, other days it is used a lot). 

But as 99% of my linux work is on non-qui servers I am pretty incompetent trying to debug it.... I'm not sure whether to ask "why would it suspend" or "why when it did would it not log in properly"?

And more to the point, I guess now I'll have to wait to see if the flashing button exists when it stops the next time.  Unless there's some trail in some log it went into suspect I can match to the last event?

---

### Post by currentshaft on 2024-07-22
Try these:

"gsettings list-keys org.gnome.settings-daemon.plugins.power" will show you the configured power settings.

"gsettings get org.gnome.settings-daemon.plugins.power <key>" will show you the values of those settings.

"journalctl -b | grep suspend" will show you all suspend events.

"sudo dmesg | grep suspend" will show you suspend events since the last boot.

---

### Post by linwood2 on 2024-07-22
> **currentshaft said:**
> Try these:

"gsettings list-keys org.gnome.settings-daemon.plugins.power" will show you the configured power settings.

"gsettings get org.gnome.settings-daemon.plugins.power <key>" will show you the values of those settings.

"journalctl -b | grep suspend" will show you all suspend events.

"sudo dmesg | grep suspend" will show you suspend events since the last boot.


The settings are: 


```
ambient-enabled true
idle-brightness 30 
idle-dim true
lid-close-ac-action suspend
lid-close-battery-action suspend
lid-close-suspend-with-external-monitor false
power-button-action interactive
power-saver-profile-on-low-battery true
sleep-inactive-ac-timeout 3600 
sleep-inactive-ac-type nothing
sleep-inactive-battery-timeout 1200 
sleep-inactive-battery-type suspend 

```

Since no battery, no cover, the one that concerns me is the 3600.   But that setting is different from what I see in the gui.  Do I need to be logged into the gui for these to work?  (I did this in an SSH session).  Hmmm... let me go check, will post again in a few. 

Assuming this goes back prior to the last reboot: 

```

ferguson@piano:~$ journalctl -b | grep suspend
Jul 22 20:33:44 piano kernel: Low-power S0 idle used by default for system suspend
Jul 22 20:33:44 piano kernel: nvme 0000:01:00.0: platform quirk: setting simple suspend

```

It would appear to only be the test I did by hand.  So... maybe not bingo.

---

### Post by linwood2 on 2024-07-22
Same answer in terminal in the GUI, but the GUI under power shows automatic suspend = off.  Plus the problem happens in days, not an hour.  So I don't think that 3600 is meaningful. 

And the journalctl doesn't seem to show it happened, so... I think no bingo.

---

### Post by linwood2 on 2024-07-23
I know a bit more.  Surprisingly it hung again after only a few hours.

The power button is not flashing, it is on, and unresponsive.  I had to power cycle it, holding power, pressing it, no combination I could find helped.  I didn't see a reset button (but it's way up in the piano wiring and not very visible). But this seems to eliminate at least a normal sleep/suspend type event.

I searched the whole output from journalctl and the last thing that happened in there is a new lease.  This time there was nothing after it, the prior time a new lease was 6 minutes (at least) before the hang.  So... not sure if it's relevant.  Lease time is 12 hours, which I think means it renews at 6, so that twice it was near in time to a lease renewal is a bit suspicious (the renewal was not due to disassociation/re-association, I checked). 

So at least as a working hypothesis this is occurring associated to a DHCP lease renewal.  Which is a bit bizarre, if it was a wifi issue i would think more likely during association not just IP renewal. 

I think I'm going to put a static IP in and see what happens.  if that doesn't work, I'll get a switch for the nearest ethernet port and run a cable down the hall and across the living room floor.

Unless anyone has any other ideas? 

```

Jul 23 02:17:01 piano CRON[8126]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Jul 23 02:17:01 piano CRON[8127]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 23 02:17:01 piano CRON[8126]: pam_unix(cron:session): session closed for user root
Jul 23 02:33:56 piano NetworkManager[572]: <info>  [1721716436.3268] dhcp4 (wlo1): state changed new lease, address=192.168.130.55
Jul 23 11:41:48 piano kernel: Linux version 6.5.0-44-generic (buildd@lcy02-amd64-103) (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #4
4~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Jun 18 14:36:16 UTC 2 (Ubuntu 6.5.0-44.44~22.04.1-generic 6.5.13)
Jul 23 11:41:48 piano kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-44-generic root=UUID=f2ad7e7f-ad07-430f-a4c7-5b7e931399ff ro quiet splash vt.handoff=7
Jul 23 11:41:48 piano kernel: KERNEL supported cpus:

```

---

### Post by oldfred on 2024-07-23
You said you updated UEFI firmware.
Check firmware settings, update often resets to defaults and may add new settings that need changes.
See if anything related to sleep or sleep states.

---

### Post by linwood2 on 2024-07-23
> **oldfred said:**
> You said you updated UEFI firmware.
Check firmware settings, update often resets to defaults and may add new settings that need changes.
See if anything related to sleep or sleep states.

I did when I updated, just didn't see anything like that, plus there's no sign that it is a sleep -- sleep makes the power light flash, in this case the power light is on steady as though still up.

I figure about 2 weeks if no hangs I'll blame the DHCP client.  If it hangs I'll hook up ethernet and see then.

---

### Post by linwood2 on 2024-07-25
Well, another beautiful theory destroyed by an ugly fact.   It hung again.  This time nothing network related near it (in fact nothing much near it at all).  The actual hang occurred at 06:17 +/-1.   Though it's possible that the log buffer is not flushed since I have to power cycle. 

I was going to run a wire and ethernet to it, but am starting to think maybe there's a physical issue.  I haven't disassembled it yet, and the piano was moved.  Maybe something is loose.  Going to find time to pull down a bunch of wires and remove the NUC and reseat all the boards.  

Unless someone else has a suggestion.

```

Jul 25 05:17:01 piano CRON[29849]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)
Jul 25 05:17:01 piano CRON[29850]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 25 05:17:01 piano CRON[29849]: pam_unix(cron:session): session closed for user root
Jul 25 05:24:26 piano snapd[589]: storehelpers.go:923: cannot refresh: snap has no updates available: "bare", "core20", "core22", "firefox", "gnome-3-38-2004", "gnome-42-2204", "gtk-common-themes", "snap-store", "snapd", "snapd-desktop-integration"
-- Boot 6e1096b168c449aaa34c2901a2e84fe5 --
Jul 25 11:30:44 piano kernel: Linux version 6.5.0-44-generic (buildd@lcy02-amd64-103) (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #44~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Jun 18 14:36:16 UTC 2 (Ubuntu 6.5.0-44.44~22.04.1-generic 6.5.13)
Jul 25 11:30:44 piano kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-6.5.0-44-generic root=UUID=f2ad7e7f-ad07-430f-a4c7-5b7e931399ff ro quiet splash vt.handoff=7
Jul 25 11:30:44 piano kernel: KERNEL supported cpus:
Jul 25 11:30:44 piano kernel:   Intel GenuineIntel



```

---

### Post by linwood2 on 2024-08-12
Well, I think I know where the problem lies.   I tried a variety of things, and nothing has helped other than running a wire and hooking up via ethernet and disabling wifi. 

I have opened it up and reseated all the cards including the ribbon cable that goes to wifi (at least I think that's what it was). 

While it's hard to prove a negative, it's been running with the ethernet cable about twice as long as it ever ran since I have been testing.

It's going to be REALLY hard to get an ethernet cable to this (on a slab, old house, can't get attach access in the wall adjacent).  The current wire just runs across the floor. 

I'll probably pick up a wifi-ethernet bridge.

I don't know if it's possible to get a replacement wifi module (and it's not obvious of course that the issue is in the physical module, it could be in the connections, or even a bug in the code that isn't recovering from some wifi condition). 

If anyone has any better ideas, please let me know.

---

### Post by him610 on 2024-08-12
IMHO, I don't think your network has anything to with your issues. You have intel comm chips.
> What kind of chips for network and wifi does intel NUC11TNHv5 have?

The Intel NUC11TNHV5 is a compact mini PC that comes with an 11th generation Intel Core processor. It has the following wireless and network capabilities:
- Wireless:
- The NUC11TNHV5 supports Wi-Fi 6 (802.11ax) wireless networking. This provides faster speeds and better performance than previous Wi-Fi standards.
- It has an Intel Wi-Fi 6 AX201 wireless adapter built-in. This is a dual band adapter that supports both 2.4GHz and 5GHz wireless networks.
- Bluetooth 5.2 is also supported for connecting wireless peripherals like mice, keyboards, headphones, etc.
- Network:
- For wired networking, the NUC11TNHV5 has a Gigabit Ethernet port. This provides fast and reliable wired network connectivity.
- The Ethernet port supports speeds up to 1000 Mbps.
- The NUC11TNHV5 uses Intel's I225-V Ethernet controller for the Gigabit Ethernet port.
So in summary, the key wireless and network chips in the NUC11TNHV5 are the Intel Wi-Fi 6 AX201 for Wi-Fi and the Intel I225-V for Gigabit Ethernet. These provide fast and capable wireless and wired networking capabilities in a compact mini PC form factor.

You might consider investigating CPU overheat or memory issues.

---

### Post by linwood2 on 2024-08-12
> **him610 said:**
> IMHO, I don't think your network has anything to with your issues. You have intel comm chips.


You might consider investigating CPU overheat or memory issues.

Because Intel comm chips never fail?  :P

I'm going to let this run another week or so and see.  That's going to be pretty damning, if with wifi off it doesn't crash.  This is also consistent since at my prior home it never crashed ,and it was wired with ethernet, not wifi. 

As I said, hard to prove a negative, but the long it runs without wifi the more convinced I am. 

I reseated the memory.  Since 100% of the failures were while the system was idle I really don't think it is overheating. I had it doing its player thing when I had guests over for 2-3 hours, where it would be working quite a bit harder, without issue.

---

