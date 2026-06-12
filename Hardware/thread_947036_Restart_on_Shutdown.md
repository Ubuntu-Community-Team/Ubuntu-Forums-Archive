---
title: "Restart on Shutdown"
date: 2008-10-13
forum: Hardware
---

### Post by MyStx on 2008-10-13
I am currently on a Toshiba Satellite M305D-S4840, with Ubuntu 8.10 (Intrepid Ibex).

When I click on shut-down, instead of fully powering down, the laptop keeps restarting automatically.

I keep having to push the power button during system reset to fully power down the machine.

All help is greatly appreciated....

---

### Post by gazer22 on 2008-10-14
I can only add my own issue here.

Same symptom, but it's a desktop running Ubuntu 8.04 (Hardy Heron).

I've tried using "sudo poweroff -f" and "sudo shutdown -P now" from the command-line, and each time the machine will restart instead.

---

### Post by Sef on 2008-10-14
Go into the BIOS and change the power management setting.  That's what I did to resolve a similar problem - 'Reboot = Shutdown'.

This is from the old [post #7]("http://ubuntuforums.org/showthread.php?t=108405&highlight=PowerManagement"):

>  I went into the powermanagement and changed 'Startup after Power Failure' to ON from Auto.

So do the same or something similar.

---

### Post by gazer22 on 2008-10-14
> **Sef said:**
> Go into the BIOS and change the power management setting.  That's what I did to resolve a similar problem - 'Reboot = Shutdown'.


Hopefully not hi-jacking MyStx's thread, but tried all of the Bios reboot settings (on/off/last) to no avail.

---

### Post by MyStx on 2008-10-14
> **gazer22 said:**
> Hopefully not hi-jacking MyStx's thread, but tried all of the Bios reboot settings (on/off/last) to no avail.

Unfortunately, I've tried the BIOS, and experiencing the same symptoms.  Any power down automatically results in a restart.  Otherwise, Ubuntu is running flawlessly.

Grazer, keep me posted on your findings.  If I find anything, I will message you as well.

Thanks!

---

### Post by gazer22 on 2008-10-14
Okay, here are some weird-ism's from my messages log (easily viewed using gnome-system-log !)

Starts with the fact that it says it was restarted, when in fact this followed a "Shutdown," which didn't actually shutdown...

The rest are just un-familiar to me, and may or may not have anything to do with the situation...

```

Oct 14 09:46:57 computer syslogd 1.5.0#1ubuntu1: restart.
Oct 14 09:46:57 computer kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20070126]
Oct 14 09:46:57 computer kernel: [    0.000000] Kernel command line: root=UUID=xxxxxxxxxxxxxxxx-removed-xxxxxxxxx ro quiet splash
Oct 14 09:46:57 computer kernel: [   16.273453] AppArmor: AppArmor initialized
Oct 14 09:46:57 computer kernel: [   16.273456] Failure registering capabilities with primary security module.
Oct 14 09:46:57 computer kernel: [   16.537736] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 14 09:46:57 computer kernel: [   16.847120] pnpacpi: exceeded the max number of mem resources: 12
Oct 14 09:46:57 computer kernel: [   16.847170] pnp: PnP ACPI: found 14 devices
Oct 14 09:46:57 computer kernel: [   16.847172] ACPI: ACPI bus type pnp unregistered
Oct 14 09:46:57 computer kernel: [   16.847174] PnPBIOS: Disabled by ACPI PNP
Oct 14 09:46:57 computer kernel: [   16.847327] PCI: Using ACPI for IRQ routing
Oct 14 09:46:57 computer kernel: [   16.847331] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 14 09:46:57 computer kernel: [   21.523491] ieee1394: SelfIDs failed root check
Oct 14 09:46:57 computer kernel: [   21.523493] ieee1394: Error in SelfID stage, resetting
Oct 14 09:53:42 computer exiting on signal 15

```

It then re-started after being told to shutdown...

---

### Post by gazer22 on 2008-10-16
I might be narrowing my issues down to problems with a hard drive (which holds the root partition, of course).

A test that worked pretty well: Boot from a Live CD and then power down.  Worked like a charm for me.  This eliminates motherboard-type problems (but not HD issues).

I'm currently checking the drives and thinking about doing a full re-install of Ubuntu.

---

### Post by gazer22 on 2008-10-16
Well, the hard drives didn't have anything obviously wrong with them.  (e2fsck didn't find anything wrong).

Went ahead with a re-install of Ubuntu.

Painful, but that appears to have fixed the Restart-On-Shutdown problem.

I'm guessing it was some weird configuration setting somewhere, but couldn't find it.

---

### Post by MyStx on 2008-10-22
Sorry for the delay, I was traveling on business.

I finally got frustrated and installed Ubuntu v8.04 instead of v8.10. I was able to power down without any problems.  

I've reinstalled v8.10, and I'm combing through launchpad to see if it's something simple that we're over-looking?

---

### Post by gazer22 on 2008-10-22
Hmm, I haven't touched 8.10, but still had the problem.

I was trying to get Wake-On-Lan working, which involved a bunch of annoying adjustments to startup and shutdown scripts, as well as messing with ethernet drivers.

I'm guessing that something went awry in that process, even though I changed everything back.

Are you saying that with a clean install of 8.04 your shutdown works but with 8.10 it doesn't?  That'd definitely be cause for concern.

One (admittedly painful) way to check for differences is to compare your /etc directory on the two different installs.

Here's how I've done that in the past, with a fresh install in the /etc directory and a backed up one in /backup/etc:
```
sudo diff -rq /etc /backup/etc > etc_diff.txt
```

etc_diff.txt will then contain a list of all of the files in the /etc directory tree which differ from /backup/etc.  I then go check the files one at a time either using "diff" or the more visual "meld."

It's definitely a bit of work though...

---

