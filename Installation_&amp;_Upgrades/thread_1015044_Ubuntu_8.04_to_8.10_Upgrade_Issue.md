---
title: "Ubuntu 8.04 to 8.10 Upgrade Issue"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by jurfid on 2008-12-18
I have 8.04 on my HP2133 mini-note and would like to upgrade to (not reinstall) 8.10.  I followed the steps to show all releases in Update Manager, which worked as advertised.

Upon starting the upgrade process, the download was quite slow (likely my wifi @ work) so I canceled the upgrade.  No issues, everything aborted and all was well.

I tried again later, but decided to cancel it again, in hopes of finding a way to utilize the ISO or Bootable USB, instead of downloading everything again.  I found no such method, so I returned to wait patiently for the default network/web download method only to find...

The "Upgrade" button has disappeared from Update Manager.  I tried reinstalling the Upgrade Manager, nothing.  I tried waiting patiently for some other update, hoping to "awaken" the updater, nothing.  I tried switching between "Normal Releases" to "LTS Releases", nothing.  Please help.

---

### Post by overdrank on 2008-12-18
> **jurfid said:**
> I have 8.04 on my HP2133 mini-note and would like to upgrade to (not reinstall) 8.10.  I followed the steps to show all releases in Update Manager, which worked as advertised.

Upon starting the upgrade process, the download was quite slow (likely my wifi @ work) so I canceled the upgrade.  No issues, everything aborted and all was well.

I tried again later, but decided to cancel it again, in hopes of finding a way to utilize the ISO or Bootable USB, instead of downloading everything again.  I found no such method, so I returned to wait patiently for the default network/web download method only to find...

The "Upgrade" button has disappeared from Update Manager.  I tried reinstalling the Upgrade Manager, nothing.  I tried waiting patiently for some other update, hoping to "awaken" the updater, nothing.  I tried switching between "Normal Releases" to "LTS Releases", nothing.  Please help.

Hi and have you tried updating via the terminal to see any errors
```
sudo apt-get update && sudo apt-get upgrade
```
You can upgrade via the alternate cd also.

---

### Post by jurfid on 2008-12-18
I have not tried that.  I was hoping to be able to solve this issue without using the terminal, in an effort to learn to navigate through the OS via the GUI.  Also, this would help me to combat the critics who say you can't do anything in Linux without the console and knowing how to write code.

---

### Post by overdrank on 2008-12-18
> **jurfid said:**
> I have not tried that.  I was hoping to be able to solve this issue without using the terminal, in an effort to learn to navigate through the OS via the GUI.  Also, this would help me to combat the critics who say you can't do anything in Linux without the console and knowing how to write code.

Ok and I understand, but by stopping the upgrade you may have to use the command line. During a upgrade it is not wise to stop as it is downloading and installing. 
When you open update manager and use the check button do you get any errors.

---

### Post by jurfid on 2008-12-18
Yeah, I understand about running updates/upgrades, the situation was one of necessity (to an extent).  I don't get any errors using the GUI Upadate Manager, but I haven't tried any of the terminal options.  I'll report back when I get a chance at that, hopefully later tonight.

Thanks for your help.  I'm liking Ubuntu, but what I'm really pleased with is the community.  There's a bounty of knowledgeable people out there interested and willing to help.  Sincerely, thank you.

---

### Post by jurfid on 2008-12-18
I ran the command as recommended.  No errors came back.  The last line was as follows:

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So it appears that something is telling my system that it's 8.10... but it isn't.  Hrmmm... any further help would be appreciated.

---

### Post by Partyboi2 on 2008-12-18
Press Alt+F2 in the box that opens type or paste```
gksu "update-manager -c -d"
``` and see if the option to upgrade shows again.

---

### Post by jurfid on 2008-12-18
Worked like a charm!!!

So, for the sake of me learning what the heck I just did...
What the heck did I just do?

---

### Post by stderr on 2008-12-19
Cheers, I'll have to remember that command, could be very handy :D

update-manager is the GUI app used for updates. If you do

```
man update-manager
```

it will list the available switches, and you can see the affect of -c and -d. Putting man before any command will list a manual page if one is present. You can quit the manual page with q, and scroll with up and down. 

gksu is a command used for switching to root for GUI apps - see this ubuntu doc on [RootSudo]("https://help.ubuntu.com/community/RootSudo#Graphical%20sudo").

---

### Post by jurfid on 2008-12-19
So the upgrade proceeded as expected.  However, on the reboot, my system hangs on a black screen (just before the light-orange-brown screen) with the gnome "thinking" icon frozen.

It appears to be hanging while trying to load X, but I'm not smart enough about Linux yet to know for sure.  From research on the forums, the problem might be the xorg.conf file, but I can't boot in safe-graphics-mode to get in and edit it.

I have currently booted to the live "CD" from my USB drive and am in 8.10.  I want to edit the xorg.conf file on the hard drive, but I don't have permission to write to this drive.  Any help to this end or along another avenue would certainly help me out.

Thanks guys, in advance.

---

### Post by stderr on 2008-12-19
Hmm, booting frmo a live CD and mounting the drive as root should be ok... you'd then use a command such as 

```
sudo vim /etc/X11/xorg.conf
```

(replacing vim with your favourite command line text editor). You would need to use sudo though as the file is owned by root and you would otherwise only be able to read it.

You may stil be able to switch to a tty when booting normally as it hangs - try Ctrl+Alt+F1 and see if you get a text-based login. If that works, you can edit your xorg.conf, and type startx to try to launch a GUI. If that fails, you can Ctrl+Alt+F1 back to the tty, and you may also have some useful debugging info on the screen then :)

---

