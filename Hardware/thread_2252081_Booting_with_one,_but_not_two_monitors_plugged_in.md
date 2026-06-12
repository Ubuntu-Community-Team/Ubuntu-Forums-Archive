---
title: "Booting with one, but not two monitors plugged in"
date: 2014-11-08
forum: Hardware
---

### Post by Nikolas_Honnef on 2014-11-08
Hey,

I have a problem with my new Asus GTX 970 on Ubuntu GNOME 14.10. Whenever I try to boot with a 2560x1440 monitor in DisplayPort and a 1920x1080 in HDMI, the DP monitor remains in standby and the HDMI monitor shows a black screen, then a grey screen and then stops showing the following text:

```
* Starting in-memory queueing server beanstalkd [ OK ]
* Restoring resolver state ... [ OK ]
* Starting uuid generator uuidd [ OK ]
* GNUstep distributed object mapper disabled, see /etc/default/gdomap
* Starting NTP server ntpd [ OK ]
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
* speech-dispatcher disabled; edit /etc/default/speech-dispatcher
saned disabled: edit /etc/default/saned
* Stopping System V runlevel compatibility [ OK ]
```

I can however switch to tty1 by pressing ctrl+alt+f1 and executing xstart results in the following output:

```
X.Org X Server 1.16.0
Release Date: 2014-07-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.13.0-32-generic x86_64 Ubuntu
Current Operating System: Linux Niko-PC 3.16.0-24-generic #32-Ubuntu SMP Tue Oct 28 13:07:32 UTC 2014 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-24-generic.efi.signed root=UUID=2ee55ba9-8931-4d57-9901-062dcbbb5507 ro quiet splash vt.handoff=7
Build Date: 06 August 2014  01:37:28PM
xorg-server 2:1.16.0+git20140806+server-1.16-branch.a793483e-0ubuntu0sarvatt (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.32.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Nov  6 01:53:00 2014
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE)
Fatal server error:
(EE) no screens found(EE) 
(EE) 
Please consult the The X.Org Foundation support 
    at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
(EE) 
(EE) Server terminated with error (1). Closing log file.
xinit: giving up
xinit: unable to connect to x server: Connection refused
xinit: server error
```

When I unplug one monitor before starting the PC everything works fine. I can even plug the 2nd monitor back in after Ubuntu has loaded and it correctly switches to dual-monitor. Also a windows installation on another HDD boots just fine with both monitors plugged in.

PC:
[LIST]
[*][COLOR=#000000][FONT=sans-serif]ASRock H77 Pro4/MVP
[/FONT][/COLOR]
[*][COLOR=#000000][FONT=sans-serif]Intel Core i5-3570K
[/FONT][/COLOR]
[*][COLOR=#000000][FONT=sans-serif]Asus GeForce GTX 970 STRIX OC
[/FONT][/COLOR]
[*][COLOR=#000000][FONT=sans-serif]Ubuntu GNOME 14.10 x64
[/FONT][/COLOR]
[*][COLOR=#000000][FONT=sans-serif]Nvidia driver 343.22 (from nvidia website or Xorg-Edgers, happens with both)[/FONT][/COLOR]
[/LIST]
[COLOR=#000000][FONT=sans-serif]
Thanks for any help!

Niko
[/FONT][/COLOR]

---

