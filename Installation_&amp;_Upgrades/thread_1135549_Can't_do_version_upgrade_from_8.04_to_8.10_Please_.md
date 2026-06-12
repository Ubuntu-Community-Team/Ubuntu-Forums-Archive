---
title: "Can't do version upgrade from 8.04 to 8.10: Please help"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Leopardson on 2009-04-24
[B]EDIT: De ****? Everything is working fine all of the sudden!
[/B]I'm not complaining**. **Apparently, while I was playing a game of Netwalk, Linux suddenly repaired itself. WTF?

**Edit: (Got edit working)** * Is it possible to do an Ubuntu 8.04-8.10 or 8.04 to 9.04 via external download?*

Hi, I just did the 7.10 to 8.04 upgrade, and it worked fine. Fixed a few programs.

I want to go from 8.10 to 9.04, but Adept isn't working this time

I press Fetch Updates first, it fetches the updates, I type in the konsole "sudo apt-get upgrade", but it didn't find any.
I went back to adept, had to fetch the updates again for some reason. I clicked the Distribution Upgrade button.

First time, it got the release notes, then tried to download the upgrade tool, but gave me an error message saying it couldn't connect, and to check my internet connection.

Obviously, my internet is working. :D

Now, it can't even get the release notes, even though it can fetch the updates.

How can I fix this and get to 8.10?
Also, is there another way to do it without doing it from a CD/DVD/USB/FLASH drive?
I pretty much am limited to the internet.


Also, I don't like KDE. How can I switch to the latest Gnome and remove the K from Kubuntu?

---

### Post by Leopardson on 2009-04-24
(Edit wouldn't work)

I tried restarting.

When I type in sudo apt-get upgrade, it acts as if it didn't find any upgrades.
Full Upgrade is disabled in Adept, even after I fetch the updates.

When I type in sudo apt-get dist-upgrade, it also gets nothing.

---

### Post by cariboo on 2009-04-24
I'm not sure if Kubuntu uses update manager, but if does, open a terminal and type:

```
sudo update-manager -d
```

---

### Post by Coreigh on 2009-04-24
Kubuntu uses Adept-manager, which is very like update-manager.
Try this in a terminal window:```
sudo apt-get update
```followed by:```
sudo apt-get dist-upgrade
```
Then run Adept-manger and try the upgrade button.

EDIT: Keep in mind this is a very busy time for upgrades since Jaunty was just released and that may add to the difficulty.

---

### Post by Leopardson on 2009-04-24
> **Coreigh said:**
> Kubuntu uses Adept-manager, which is very like update-manager.
Try this in a terminal window:```
sudo apt-get update
```followed by:```
sudo apt-get dist-upgrade
```Then run Adept-manger and try the upgrade button.

EDIT: Keep in mind this is a very busy time for upgrades since Jaunty was just released and that may add to the difficulty.

When I do "sudo apt-get dist-upgrade", I get this:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by Leopardson on 2009-04-24
I can for some reason get past the release notes, which took a couple tries.

But no matter what I do, when I try to use the version upgrade, I get the same "Upgrade tools  could not be downloaded. Please check your internet connection" thing.

---

### Post by Leopardson on 2009-04-24
Edit is broken again. Brings me to a 404 error page.

Anyway, every time I start up, I have to use "sudo dpkg-reconfigure xserver-xorg" at the fullscreen console, as every time, the X server fails to start without being reconfigured.

I'm using an ATI Radeon HD 3650 with the latest catalyst drivers.

---

### Post by Leopardson on 2009-04-24
...aand after playing a game of netwalk, everything works again.
WTF?

Linux self-repair FTW.

---

### Post by tchalvakspam on 2009-04-24
My recommendation:
torrent the alternate install iso (this took me 5 minutes, there are so many people active with it today)
boot up from the liveCD to check for problems.
reboot back into the normal os and upgrade from the CD directly.

---

