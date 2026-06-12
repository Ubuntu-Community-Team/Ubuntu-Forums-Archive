---
title: "Monitor problems"
date: 2008-11-11
forum: Hardware
---

### Post by ihatecellphones0516 on 2008-11-11
a few weeks ago ubuntu stopped letting me use any resolutions beyond 640X480.  Every couple of days I try to take another stab at fixing it.  My latest attempt was as follows.

dan@dan-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for dan: 
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081111181757
dan@dan-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a
                  Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

dan@dan-desktop:~$ 

I honestly have no idea what is going on with this.

---

### Post by oldsoundguy on 2008-11-11
the Nvidia (and some other) drivers are currently messed up in 8.10  They WORK but not completely or not as they have a potential to do.  Some features have disappeared altogether (such as the ability to rotate a monitor using Nvidia (not sure about others).
And monitor recognition has totally disappeared.
I found I could get the resolution and wide screen support if I used the LEGACY drivers and not the new ones for Nvidia.  But that is it.  I would not even contemplate using any eye candy programs with the current driver weakness.

---

### Post by ihatecellphones0516 on 2008-11-11
thanks, that's good to know about.

so should I be using the 173 drivers?
or should I switch back to what came ubuntu (if so, how)?

---

