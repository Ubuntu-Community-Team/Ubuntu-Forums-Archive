---
title: "Newbie upgraded 7.10-&gt;8.04 and now suffers crash"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by beneix on 2009-10-12
I have ran 7.10 for around 2 years on a Toshiba Portege 2000 laptop and everything's been fine.  Now I decided to take the plunge and upgrade to 8.04.  After the upgrade, Ubuntu freezes shortly after boot-up.

I get this far:

[LIST]
[*]Enter user details
[*]Desktop is shown
[*]Top menu and bottom bar shown, including menus and top right-hand icons
[*]An icon appears top right saying a crash has been detected
[*]Shortly (3-5 seconds) after that, the whole machine freezes and both mouse and keyboard become unresponsive.
[/LIST]

I have tried starting in failsafe mode and also failsafe Terminal.  Both freeze after approximately the same amount of time.  I have tried ‘Alt + SysRq + K’ but no reaction. I have tried Alt + SysRq, and ‘R’ ‘E’ ‘I’ ‘S’ ‘U’ ‘B’ -- that does something but the system does not come back to a responsive state.

There are no attached devices to unplug.

I would appreciate help in trying to isolate the problem -- I thought I would be able to look at some log files in the failsafe Terminal mode but before I get a chance, the system freezes...

---

### Post by zvacet on 2009-10-12
Boot in recovery mode and type 

```
sudo dpkg --configure -a
```
```
sudo apt-get -f install
```
```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```

---

### Post by beneix on 2009-10-19
> **zvacet said:**
> Boot in recovery mode and type 

```
sudo dpkg --configure -a
```
```
sudo apt-get -f install
```
```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```
Thanks zvacet.  First of all a disclaimer: I am rather new to Linux so go easy on me...
 
I tried your suggestion.  Unfortunately, I was not aware that the last command would need a network connection so the system started trying to download stuff when I only had a wireless connection (which wasn't working in recovery mode) and was just hanging on trying to get onto the net.  A couple of days later, I managed to connect via wired ethernet and retried the same commands.  This time, I got the message that there was nothing to update.
 
Please let me know if you have any other ideas, or if there are some files that I should clear out before I try your commands again -- since it did seem that they would have worked the first time if I only had a working Internet connection.
 
Thanks.

---

### Post by us3598 on 2009-10-19
What kind of system are you running. Please include processor, RAM, and any other OS's or partitions on your hard drive.

---

### Post by mikeuhlik on 2009-10-19
Here is a guide about EOL Upgrades It Means End OF Life Upgrades the 7.10 Is EOL This Might Help.

[Guide Is Here For EOL Upgrades]("https://help.ubuntu.com/community/EOLUpgrades")

Mike :guitar:

---

### Post by beneix on 2009-10-20
> **us3598 said:**
> What kind of system are you running. Please include processor, RAM, and any other OS's or partitions on your hard drive.

It's a Toshiba Portege 2000 with a 750 MHz Mobile Pentium III Processor-M, 512 MB of RAM and a 20 GB (original Toshiba) hard drive.  Only one partition, no other OS's.  I have used either the in-built 802.11b card or a PCMCIA Netgear card -- both work.  When I got the freeze, I tried disabling both but neither seem to cause the crash.

As I mentioned, I haven't had any problems for two years on 7.10 but as soon as I upgraded to 8.04 I got the freeze after the desktop had loaded (and subsequently also when starting in failsafe mode).

I could of course try a fresh reinstall but that would be quite a hassle, so grateful for any help.

---

### Post by slakkie on 2009-10-20
Try to boot from a live CD and mount your root partition:

```

mkdir /mnt/root
mount /dev/sda1 /mnt/root
# or
mount /dev/hda1 /mnt/root

```

Then have a look in the log files located in /mnt/root/var/log.
You'll be interested in:

* kern.log
* daemon.log
* Xorg.0.log (or Xorg.failsafe.log)
* syslog
* debug.log

See if you can find anything in those logs related to your problem.

Best of luck!

---

