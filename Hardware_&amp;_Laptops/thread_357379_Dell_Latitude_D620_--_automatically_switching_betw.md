---
title: "Dell Latitude D620 -- automatically switching between docked &amp; undocked state"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by diamond on 2007-02-09
I have a Dell Latitude D620 that I work on. Most of the time I use it in a docking station, but sometimes I need to run it on its own.

The trickiest part of this seems to be swtching the screen from the external screen resolution to the resolution for the built-in LCD. I have a 24" widescreen Dell 2407WFP monitor hooked to the docking station, and I run it at 1920x1200. But the built-in LCD can only go up to 1440x900.

Because this machine uses the intel 945GM chipset, I have to use 915resolution to set the Video BIOS for the resolution I want. So when I'm docked, my /etc/default/915resolution file looks like this:

```

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=5a
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1920
YRESO=1200
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=

```

When I'm undocked, I need to make the following changes:
```

MODE=5c

XRESO=1440
YRESO=900

```

I also have to make a change to my xorg.conf file, so it uses the correct monitor.

This all works, but it's a pain, because I can't just pull the machine out of the dock, open it up, and turn it on. I have to log in in single-user mode, make the appropriate changes to the above files, and then reboot before I can use X in the right resolution. And then I have to do it all again before I run in the dock.

So I'm trying to figure out if there's a way to automate this process. My first thought is that I might be able to write a udev rule to detect the presence or absence of the docking station, and run a bash script to edit the 915resolution and xorg.conf files appropriately. Does this sound sensible? Any ideas on what specifically udev should look for to detect whether or not the docking station is there?

Or is there an even better solution to all of this?

---

### Post by veloce on 2007-02-09
I have a d520 and have a similar setup.  What I did was run 915resolution in auto mode.  This edited the xorg.conf file and put the allowable resolutions in it.  Does this not work for your system?

Then I switch to the lower resolution before changing screens.

I am trying to get both screens working as the same time using Xinerama but having a lot of difficulty. One thing I have come across is a set of scripts that run at boot time and allow you to select the xorg.conf file to use for this session.  I haven't used it yet because I haven't got the dual head setup working.  The reference is:

[http://www.fmi.uni-passau.de/~zimmerma/xlayout_chooser/](http://www.fmi.uni-passau.de/~zimmerma/xlayout_chooser/)

Veloce.

---

### Post by diamond on 2007-02-09
> **veloce said:**
> I have a d520 and have a similar setup.  What I did was run 915resolution in auto mode.  This edited the xorg.conf file and put the allowable resolutions in it.  Does this not work for your system?

Can you post a copy of your 915resolution file for me to look at?

---

### Post by veloce on 2007-02-09
Sure, my /etc/default/915Resolution

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=
YRESO=
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=

Veloce.

---

### Post by diamond on 2007-02-09
> **veloce said:**
> Sure, my /etc/default/915Resolution

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=
YRESO=
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=

Veloce.

Oh.

I had tried the "auto" mode before, but I didn't leave XRESO and YRESO blank. Maybe that's why it didn't work.

I'll give this a try.

---

### Post by diamond on 2007-02-09
No, that didn't work. It went to 1600x1200, not 1920x1200.

I'm using a Dell 2407WFP flatscreen, and from what I've read I understand that linux has a hard time getting this monitor to correctly report its maximum resolution. It clearly *can* display quite nicely at 1920x1200, but you have to force it to do so with the 915resolution configuration file.

Perhaps if I could manually add both the 1920x1200 and 1440x900 modes to the video BIOS, then Xorg will be able to display the higher resolution when it can, and gracefully degrade to 1440x900 when it can't.

Is it possible to add more than one mode with the 915resolution config file?

---

### Post by RandomJoe on 2007-02-09
Not the most elegant solution, but I used to do this with my C840 laptop and docking station.  I found that the NIC in the docking station had a specific PCI ID.  I wrote a script that runs on boot - early in the process - and checks for that PCI ID.  If it sees it, it copies "docked" versions of the appropriate files into place.  If not, it copies "undocked" versions.  I did X config, network configs (whether to enable wireless or not), and modified my CPU scaling setpoints.

As I said, not terribly elegant but I didn't have to keep swapping them manually.

Unfortunately, the D-Port "port replicator" docking station for the D-series doesn't have a separate NIC in it like the C-Ports did.  I haven't yet checked to see if there is another device or property that can be detected that is only present when docked.  (My D-series is a work machine, so seldom used in Linux.)  The more full-blown D-Dock should have something as it allows adding PCI cards.

---

### Post by tpearson@alltel.net on 2007-04-26
I have a D610  using a 1905FP as external.   What I had to do was while docked
swith to highest setting System----Preference---Screen Resolution set to make resolution 1280x1024  and then check option to make default for this computer.  Once I did this when I take out of dock and reboot i get maximum setting for Laptop 1024x768

---

