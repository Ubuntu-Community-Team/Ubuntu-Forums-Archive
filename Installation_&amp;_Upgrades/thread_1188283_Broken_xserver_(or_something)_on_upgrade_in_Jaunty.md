---
title: "Broken xserver (or something) on upgrade in Jaunty"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by beakdan on 2009-06-15
Hey folks-

I'm on a Dell Latitude D630, and have been dual-booting XP since Hardy.  I upgraded to Jaunty a month ago, but hadn't done any updates since then.  Everything has seemed fine up until now.

I would classify myself as "smart but uneducated"; ie, I can follow things through logically, but theres a great deal that I don't know.

This morning, I began an upgrade on many, many (700+) packages.  The packages downloaded successfully, and began installing.

When I checked up on it, there was a warning on the screen saying:

Ubuntu is running in low-graphics mode.
The following error was encountered; you may need to update your configuration files to solve this.
(EE) config/hal: couldn't initialise context: (null)((null))

I'm then presented with a few options:

1) Run Ubuntu in low-graphics mode for just one session
     I have tried this, but no luck.  I get a notification "Stand by
     while the display restarts", but I just end up either back at the
     original error for config/hal, or at a command prompt

2) Reconfigure graphics
     This gives me 3 suboptions;
          a) use default (generic)confguration
          b) create new configuration for this hardware
          c) use backed-up configuration
     I've gone through all of those, none seems to produce any change in
     my symptoms

3) Troubleshoot the error
     my suboptions here are:
          a) review the xserver log file
          b) review the startup errors
          c) edit the configuration file
          d) archive configuration and logs
looking at a), things seem pretty well behaved at first (it finds my touchpad, keyboard, etc).  Things get hairy when it gets up to the screen, at which point I see the following warnings (multiple times, interspersed with other data):

(II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync

and

(WW) config/hal: device AT Translated Set 2 keyboard already added. Ignorind

and

(WW) Open ACPI failed (/var/run/acpid.socket) (connection refused)

and 

(EE) config/hal: couldn't initialise context: (null)((null))

There's some other things there, but those are the ones that "seem" like they may be relevant.

looking at b) I get the message:
GDM: Xserver not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth-nolisten tcp vt7
Error: Command could not be executed!

I don't intend to change my configs on my own, since I don't know what I'm doing.

4) Exit to console login
     Which is only somewhat useful, but at least not EVERYTHING is broken :)

I've restarted multiple times in this process, and on bootup, I initially see the normal splash screen, then the normal startup text.  It seems there's then some problem loading "kinit", because that's as far as the normal behavior goes; at "kinit" it seems to have trouble finding the file? (says "trying to resume from <name>".  After that I see a screwed-up version of the splash screen (ie colors and size are messed up), and then to the "low-graphics" warning as reported above.

Help!?

Thanks,
Dan

PS - full disclosure: I knocked my laptop over last night, but it woke up and worked fine this morning, and didn't give me any grief until the upgrade.

---

### Post by edvar on 2009-09-30
It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!

---

### Post by oakeley on 2009-11-27
Did anyone ever find a fix for this? I have the same problem. I checked the /etc/hal/fdi... folders mentioned in the last post and they all exist on my system. Does anyone have a clue how to get the Xserver working again. I would be quite happy just with the "apt-get..." command to force all the packages to do a clean install but I am not sure which packages are bust...
 
Many thanks for your help
 
Edward

---

