---
title: "b43 broadcom driver not able to load/find"
date: 2011-10-29
forum: Hardware
---

### Post by RonnieJ on 2011-10-29
Hey guys... I have now for 7 days tried getting this wireless card working. Its able to run with the STA drivers but since I need monitor mode I need the b43 drivers...

I have been trying to follow this guide: [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) but without luck... im not able to install the: "firmware-b43-installer". I get this message from synaptic:

Package firmware-b43-installer has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

running: lspci -vnn | grep 14e4 gives me
05:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
and as I can read it should be supported...

I havent been able to get the b43 drivers showing in the additional drivers list... what to doooo?! Please help...

I am running ubuntu 11.04

---

### Post by hansdown on 2011-10-29
Hi, RonnieJ.

Can you paste this into a terminal?

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source

```

---

### Post by RonnieJ on 2011-10-29
It says its already installed

---

### Post by hansdown on 2011-10-29
Before I suggest reinstalling, could you restart your computer?

---

### Post by RonnieJ on 2011-10-29
Sure... I have now restarted... not sure what I should be looking for... I still cant install the package and under additional drivers only the STA is visible...

---

### Post by trundlenut on 2011-10-29
you also need a package called b43-fwcutter installed as well.

---

### Post by RonnieJ on 2011-10-29
I have b43-fwcutter installed...

---

### Post by hansdown on 2011-10-29
Glad you fixed it, RonnieJ.

---

### Post by RonnieJ on 2011-10-29
No no hehe... its not fixed... I have installed the fwcutter but that haven't changed anything... Im not sure what to do? :S

---

### Post by trundlenut on 2011-10-29
It won't show up under additional drivers.  What I got on my machine was that network manager said that the hardware wasn't ready as firmware is missing.

What server are you using for updates etc, it may be worth getting it to look for the best server for you.

---

### Post by RonnieJ on 2011-10-29
How can I see what server it is using?

---

### Post by trundlenut on 2011-10-29
> **RonnieJ said:**
> How can I see what server it is using?

In the update manager go to settings and in one of the tabs it will show you what mirror you are using and offer to find the best one.

Unfortunately my Ubuntu is rather borked at the moment so I'm having to use XP and I can't remember exactly where the option is.

---

### Post by RonnieJ on 2011-10-29
Hmm theres alot of links in there... but the main server seems to be (under other software)

[http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/)

---

### Post by trundlenut on 2011-10-29
right rebooted into Ubuntu.  Once you click on settings, on the Ubuntu Software tab click on the drop down next to Download From and choose other then hit the "select best server" button in the top right corner and let it work its magic.

---

### Post by hansdown on 2011-10-29
I've been trying to help someone in another thread.

It seems, that the B43 works in 11.04, but the STA, works best for 11.10.

---

### Post by RonnieJ on 2011-10-29
I have just upgraded to 11.10 to see if that helped and now the wireless is working out of the box.. im still having some issues putting the wireless in monitor mode but im trying som things as we speak..

---

### Post by hansdown on 2011-10-29
> **RonnieJ said:**
> I have just upgraded to 11.10 to see if that helped and now the wireless is working out of the box.. im still having some issues putting the wireless in monitor mode but im trying som things as we speak..

Good work, RonnieJ.

I'm back up, and running, now.

---

