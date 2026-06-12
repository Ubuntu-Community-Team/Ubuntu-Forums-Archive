---
title: "usb devices don't show up"
date: 2010-01-25
forum: Hardware
---

### Post by MichaelBurns on 2010-01-25
I have two flash drives and two mp3 players that I have been able to mount regularly until today.  Now the mp3 players are not mounting.  They do not even appear in "Places" for me to manually mount them.  After I connect the mp3 players, then the flash drives also don't appear when I plug them in, and their indicator lamps behave strangely.

I tried the "lsusb" command, but it just "freezes" the terminal.  That is, after pressing enter, the cursor goes below the command prompt, but it just never produces any output after several minutes.  Is that normal for "lsusb"?

This bit of output from "dmesg" is where I think that the problem starts:
```

[  659.456119] usb 1-2: new high speed USB device using ehci_hcd and address 5
[  659.642293] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[  659.644623] hub 1-0:1.0: hub_port_status failed (err = -32)
[  659.848154] hub 1-0:1.0: unable to enumerate USB device on port 2

```
I have no idea which usb device that I might have connected at that time.  From the rest of the output (which I will spare you, unless you ask for it), I would make the unqualified guess that, for some reason, the mp3 players are causing ubuntu to increment the usb port number to a port number that does not exist.  Then, every time I plug in a usb device after that, the computer looks for a port that doesn't exist.  If I restart the computer, then I guess the port numbers get reset, and everything works again for a while.

I have restarted the computer and then successfully mounted my flash drives.  The problem seems to be related to the mp3 players.  The mp3 players have always automounted before.  For some reason, today they are not automounting, and I'm getting this problem.  Since I'm running off of the live cd (jaunty) without a harddrive, I'm worried that this is somehow a hardware problem.  Since I shut down every night, the software should be effectively reset as if I am reinstalling ubuntu every day.

How can I figure out what is causing this problem?

---

### Post by MichaelBurns on 2010-01-25
Unfortunately (or perhaps fortunately) I cannot manage to repeat this problem on the third reboot of the day.  So, no further testing results are available.  "lsusb" produces output in about 1 sec.

---

### Post by MichaelBurns on 2010-03-10
This problem has recurred several times since I created this thread.  In particular, I have this problem today, so I decided to bump the thread to see if anyone would like to help me figure this out.

Again, "lsusb" does not respond; I let it run for over an hour to see if it finally would give me some output, but it didn't.  Neither Ctl-C nor Ctl-Z would return the command prompt.  I just closed the terminal by clicking on the "close" button.

Other than "dmesg" and "lsusb", what else can I do to try to figure this out?

---

### Post by MichaelBurns on 2010-03-21
bump

---

### Post by MichaelBurns on 2010-04-14
bump

---

### Post by apolloltiujr on 2010-04-14
I found a website. Try if help

Linux Driver

[http://members.driverguide.com/index.php?action=wizard_step_1](http://members.driverguide.com/index.php?action=wizard_step_1)

---

### Post by MichaelBurns on 2010-04-15
> **apolloltiujr said:**
> [http://members.driverguide.com/index.php?action=wizard_step_1](http://members.driverguide.com/index.php?action=wizard_step_1)Thanks for trying, apolloltiujr, but there are only so many times (i.e. once) that I can tolerate an obstructing, obnoxious solicitation to pay for an unwanted membership.  However, it did focus my approach.  Apparently, I need to address this from the ubuntu side by installing the appropriate driver for my device, or from the device side by modifying its firmware, or both.  I will prefer the driver installation, but I expect that to be buggy.  If I find a good, universal solution (like I assume you intended with that website), then I will try to remember to post it here.

---

### Post by MichaelBurns on 2010-06-28
bump

---

