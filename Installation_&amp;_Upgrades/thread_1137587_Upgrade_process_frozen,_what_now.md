---
title: "Upgrade process frozen, what now?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by dr_alejandro on 2009-04-25
I spent the whole day upgrading from 8.10 to 9.04 after almost 5 hrs it finally finished downloading all packages. The computer then started to do the installation but after about 10 minutes it froze. It is simply not responding at the moment (more than an hr like that). What should I do?

What happens if I reboot? Would I need to start all over again (downloads and everything)?

---

### Post by fdrake on 2009-04-25
can u get yourself to the virtual terminal? press "Ctrl+Alt+F1" and login. If everything is frozen and you cannot login i don't think you can do much then... I would execute an hard-reboot.

---

### Post by radarmagnet on 2009-04-25
**Step A) has things somewhat working...

 I had about the same problem...
I didn't read the release notes saying to install all the updates before doing the upgrade...
<rant>then why show the UPGRADE button?!? duh!</rant>

Anyway, booted back up to the last 8.10 kernel. There was no 9.04 yet...

The machine didn't have keyboard or mouse in the greeter or X... so I logging into Ctrl+Alt+F1

1) killed killed gdm after 
sudo killall gdm
(probably not necessary)


2) network was down.
Not sure I needed it as everything has downloaded,
but I recovered eth0 by 
sudo cp /etc/network/interfaces.bak /etc/network/interfaces
sudo ifup eth0

3) ran apt-get dist-upgrade
... it said I need to fix up dpkg first.... so I ran it's command
sudo  dpkg --configure -a

4) ran apt-get disk-upgrade again
... it's running right now...
** there are prompts for some packages that I am answering y to (didn't work on a couple) so I started to answer Y... (love that unix!)

first error:
Proccessing triggers for python-support
Errors where encountered while processing at
at
ubuntu-standard
E: Sub-process /sur/bin/dpkg returned an error code (1)

5) fix network again (lost dhcp addr)
sudo ifdown eth0
sudo ifup eth0

6) ran
sudo apt-get dist-upgrade
fails with dependency errors ... same place
at
ubuntu-standard

6) run apt-get update (should have done this first :)
sudo apt-get update
just updated some indexes... (9.04 sources already installed?)

7) remove at/ubuntu-standard
sudo apt-get remove at
(it's removing both)

 8 .) reinstall them?
sudo apt-get install at ubuntu-standard
(more errors, the same as upgrade has)

9) ... 9.04 kernel was installed, at and ubuntu-standard not configured...
going to try a reboot...

A) looks mostly upgraded.. Network manager is hosed and doesn't "see" eth0...
wireless worked!? got eth0 up...
used synaptic! -
  removed at residuals, reinstalled it... good
  install ubuntu-standard... good

* don't remove network-manager 
sudo dpkg -r network-manager network-manager-gnome
remove their residuals with synaptic...
...reboot
...sudo ifup eth0
...reinstall w/syna... network-manager network-manager-gnome
...didn't need to do this... same problem...

B) NetworkManager did not see LAN/eth connection (wireless worked fine)...
changed /etc/NetworkManager/nm-system-settings.conf
[ifupdown]
managed=true

and rebooted... now n-m works.

so i'm close enough for tonight. haven't check dual display yet. video seems to have some glitches occasionally (shadow text) ... could be some wierd compiz thing.

I'll try to comeback and finish... someone else can convert to commandline for easy instructions:)

<rant> since all the pieces to continue the install are made, why not put a "recovery" boot so if the install locks up or machine loses power, that it will boot into init3 with a simple dpkg process like and continue. then remove it if the process completes.

If everything is downloaded, it shouldn't even need the network to finish.</rant>

---

### Post by dr_alejandro on 2009-04-25
I can  do "Ctrl+Alt+F1" but how do I login?  I wrote my username and pressed enter and got an error.

---

### Post by fdrake on 2009-04-25
> **dr_alejandro said:**
> I can  do "Ctrl+Alt+F1" but how do I login?  I wrote my username and pressed enter and got an error.

maybe you misspelled your password. first you type in the username and then at the second line it asks you for your password.

---

### Post by dr_alejandro on 2009-04-25
i never put the password. i wrote my username, hit enter and got an error message... prompt was gone and didnt let me type anything.

I just rebooted and was able to do login (like with Ctrl+Alt+F1). I'm now in my home directory. What can I do from here?

---

### Post by radarmagnet on 2009-04-25
See [post 3..]("http://ubuntuforums.org/showpost.php?p=7147008&postcount=3").
I don't recommend it yet, but I'm getting somewhere.

---

### Post by dr_alejandro on 2009-04-25
The problem might not be so bad but I'm not going to bother. I was considering installing the 64 bit version of 9.04 instead of upgrading the 32 bit version to 9.04. I'll do that.
All my important files are in backup and in my primary HD in which I have XP.
I'll simply install the 64 bit version of 9.04 in the HD I use for linux. I will need to deal with themes, plugins, etc. but i was going to do the 64 bit jump someday.

---

### Post by radarmagnet on 2009-05-08
update:
Still some strange things needing fixing.. To many to remember now.

I want to reiterate the BAD functionality of showing the upgrade button, when you HAVE to perform an update first.
This seems like it LEADS users that don't RTFM to perform the upgrade the wrong way.
Bad form... fix it.

---

### Post by wabbalee on 2009-05-08
I don't like doing dist-upgrades but to answer the OP:

> What happens if I reboot? Would I need to start all over again (downloads and everything)?

not exactly, if you can get to /var/cache/apt/archives and copy all the *.deb files to another partition or usb stick you have basically backed up your downloads. all you need to do is copy them back to that location (as a root) and restart the process. most likely these files will still be there. Your package manager will look in the cache first before it attempts to download. also very handy when you want to install on a second machine but don't want to go through the long process of downloading the same files again. If you use synaptic you can save the full state of the installed packages to a text file; use this file to read the markings on your (other) machine and you do not have to go through the manual process of selecting all your favorite software again.

---

