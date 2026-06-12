---
title: "Ubuntu has Gone Mad Following Upgrade"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by Ingla on 2006-01-26
Hello.

Something very strange has happened. I have had Ubuntu working fine for several months on a rather old hard disk. So, I decided to install it on a new one before I suffer a HD crash.

I installed it last night. The installation went perfectly. I then copied over some backup files from my previous installation, entered the IP's of my ISP's nameservers and connected. Everything was working great.

I did an apt-get update....went fine and the Automatic Update Manager came on to tell me new updates were available...as usual.

I installed all the updates from the Update Manager. I have not installed anything else at all. This is a clean installation.

It was late, so I turned off the computer and went to bed.


Today, when I booted into Ubuntu, the following crazy things occurred:

1. The CD ROM won't mount. Nothing happens at all. As mentioned, it worked fine yesterday before the upgrade. I tried several times to open it from the file browser, but I only get an error notice saying, " Unable to mount the selected volume  /dev/hdb already mounted or /media/cdrom0 busy"

I've tried many times, including using other CD's. It will not mount.

2. I couldn't connect to any site on the Internet. So, I checked around and found that my DNS nameservers had vanished. They had been replaced by the IP of my modem (which had been there originally by default).

I did a sudo gedit /etc/resolv.conf, changed to the correct server IP's again, SAVED THE FILE, and everything was fine (as far as the Internet was concerned).

Being somewhat suspicious, I rebooted the machine and checked in System>Administration>Networking>DNS Tab and, lo and behold, my nameservers were gone again. This happened a couple of times.

I set the system to let me log in as root with GDM, went in as root and tried to gedit /etc/resolv.conf. Access denied. (By the way, the Desktop did not look at all like the one on my previous installation when logging in as root...it had no icons and looked just like my user Desktop...only the terminal said I was root).

Next, I logged back in to my user, re-edited resolv.conf and saved it again. I also saved a copy to the Home Folder. I also made a backup of the saved folder in /etc/.  Then I rebooted.


When I came back in, the DNS nameserver IP's were gone again. So, I renamed resolv.conf and moved the copy I had saved in the Home Folder to /etc/. Everything looked OK. Rebooted again.

When I came back in, the nameservers were gone again from resolv.conf AND from the backup I had made of it!


I tried these things a couple of times in the Terminal, both as sudo and as root.

I've tried rebooting after checking "Save these Settings" on the logout screen and leaving it unchecked. Nothing makes any difference.

In summary:

1.I can't mount a CD (which I need).
2. Nothing I configure or save as root or sudo is saved beyond the current session.

Does anyone have any idea what has happened here or how to fix it?

WOW!!! While writing this and trying to preview the post, my nameservers have diappeared twice IN THE MIDDLE OF THIS SESSION!

Thanks very much.

---

