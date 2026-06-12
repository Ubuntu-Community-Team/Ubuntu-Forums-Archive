---
title: "Ongoing sluggishness: cupsd, programs, host resolution"
date: 2008-08-21
forum: General Help
---

### Post by Bucky Ball on 2008-08-21
Okee doke, Hi all.

I have posted about separately about these 3 issues and received little to no response for any of them, but thought I would post the lot and see if some problem, picture, solutions emerge in anyone's mind. Fingers, toes and eyes crossed at this end.

1/ Sometimes, not all times, as Ubuntu is booting, it pops out of the splash and progress bar to a recovery boot looking screen, where it is hanging at 'starting internal printer cupsd'. Hangs there for a bit, then gives the okay (for everything) and carries on booting as normal and there I am at the desktop.

2/ All times, once I am at the desktop, icons along the top tool bar on the right take forever to appear and the desktop is effectively 'dead' for about 40 seconds, give or take. Then they appear and all looks normal. But looks can be deceiving. Click an icon to start a program, another 40 seconds later (sometimes longer) the program opens, ready for business. Sluggish, and consequent program opening is equally so. All working normally when things are up and running.

3/ Whenever I enter the terminal and use a 'sudo' command, I get the error below. I have used this as an example, but basically, take your pick. Any sudo will do it.
```
skulker@HPLappy:~$ sudo fdisk -l
sudo: unable to resolve host HPLappy
[sudo] password for skulker:
```Bottom line:
1/ Sometimes hangs on the error at boot then as normal.
2/ Programs sluggish as hell to open
3/ Host resolution with sudo commands

Does this combination of events point to one particular cause or 3 seperate enigmas?

As you would imagine from the specs below, this laptop is fast for my purposes and was rocket-like before this stuff started happening. Can't think of anything I have tweaked to cause this (I use this machine for uni so can't afford for anything to break mid-semester - usually only get serious tweak-wise during the holidays).

As I say, all offers welcome, all digits crossed in the hopes of someone having any advice with this as it is slowing down my productivity, the opposite of why I use this thing in the first place! lol

Cheers ... :)

ps: last thing I do remember playing about with was samba - could this be the one culprit for said problems?

---

### Post by fahadsadah on 2008-08-21
I can easily fix the sudo problem:```
echo "127.0.1.1 HPLappy" | sudo tee -a /etc/hosts
```.

Are you using the laptop as a printer server? If not, you can fix the first problem: ```
sudo aptitude remove cupsys
```

---

### Post by Bucky Ball on 2008-08-21
Well, that fixed the sudo problem, as you suggested, thanks! :)

As for your second fix, I am presuming by print server you're meaning are other computers going through mine to get to the printer. No, that is not the case, but will removing cupsys remove my cups configuration, thus my access to the printer?

Incidentally, the fixing of the first problem seemed to fix the speed problem (seemed to) also, so double thanks. I will reboot and see if the normal speed is back from the get go (usually opening a program the first time is very slow, closing then reopening is sometimes back to normal speed so maybe it had worked out the host the second time around).

:)

---

### Post by fahadsadah on 2008-08-21
Cool! I'm so glad to hear I fixed your problems.

You can remove cupsys. All you need for printing to another machine is cups.

---

### Post by Bucky Ball on 2008-08-21
What do you make of this? What I got when I ran the command to remove cupsys:

```

skulker@HPLappy:~$ sudo aptitude remove cupsys
[sudo] password for skulker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  bluez-cups cups-pdf cupsys-driver-gutenprint hal-cups-utils hplip 
  kubuntu-kde4-desktop ubuntu-desktop xubuntu-desktop 
The following packages are unused and will be REMOVED:
  gnustep-back-common gnustep-base-common gnustep-common gnustep-gui-common 
  libffcall1 
The following packages will be REMOVED:
  cupsys 
0 packages upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 12.3MB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: cupsys but it is not installable
  kubuntu-kde4-desktop: Depends: cupsys but it is not installable
  bluez-cups: Depends: cupsys but it is not installable
  hplip: Depends: cupsys (>= 1.1.20) but it is not installable
  cupsys-driver-gutenprint: Depends: cupsys (>= 1.2.5) but it is not installable or
                                     cups (>= 1.2.5) which is a virtual package.
  hal-cups-utils: Depends: cupsys but it is not installable
  xubuntu-desktop: Depends: cupsys but it is not installable
  cups-pdf: PreDepends: cupsys (>= 1.1.15) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
abiword
bluez-cups
cups-pdf
cupsys-bsd
cupsys-driver-gutenprint
deskbar-applet
f-spot
foomatic-db-hpijs
gnome-applets
gnome-games
gnome-games-data
gnome-utils
hal-cups-utils
hpijs
hplip
hplip-data
hplip-gui
kubuntu-kde4-desktop
libdeskbar-tracker
libgnome2.0-cil
libgnomecups1.0-1
libgnomeprint2.2-0
libgnomeprintui2.2-0
libgtksourceview1.0-0
min12xxw
python-gnome2-desktop
system-config-printer-common
system-config-printer-gnome
system-config-printer-kde
tomboy
ubuntu-desktop
xubuntu-desktop

Downgrade the following packages:
gnome-panel [1:2.22.2-0ubuntu1.1 (hardy-updates, now) -> 1:2.22.1.2-0ubuntu3
(hardy)]

Leave the following dependencies unresolved:
abiword-common recommends abiword-gnome | abiword
gnome-panel recommends gnome-applets (>= 2.12.1-1)
Score is 1890

Accept this solution? [Y/n/q/?]
```

Looks kinda straight forward, but there seems to be a lot of things depending on cupsys. I am in danger of breaking anything else with this process? It does look like it might fix a few other problems I was perhaps unaware of though ... :)

---

### Post by Bucky Ball on 2008-08-22
Hmmm. Also, the desktop computer seems to be throwing the same ´unable to resolve host' error. Tried the previous fix you suggested (changing the computer name details of course), but didn´t work.

```
anna@Lounge:~$ sudo fdisk -l
sudo: unable to resolve host Lounge
```This is what I tried:

```
echo "127.0.1.1 Lounge" | sudo tee -a /etc/hosts
```

Something I am missing? Could this problem be related to my router(s)?

---

