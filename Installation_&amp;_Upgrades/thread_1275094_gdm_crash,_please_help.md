---
title: "gdm crash, please help"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by FiloSottile on 2009-09-25
I reinstalled ubuntu on my machine and after a lot of stupid troubles (erroneous bios, ecc) i reached to get gdm. :)
I enter my username, then my password, hit enter... 
The password becomes grey and normally i have to wait a second... but nothing happens  :(
It freezes on password... i can't enter anything but the mouse works, and i can choose from options to shutdown pc. :-\
What to do?  :confused:

---

### Post by rreese6 on 2009-09-26
bootup in recovery mode.
drop to root prompt
type:
su <yourname>
when asked for password enter it
if you get a $ sign prompt then password is ok.
if not then use
passwd <yourname> 
enter new password
reboot
log in

---

### Post by P1C0 on 2011-01-05
Today I came home after leaving ubuntu with a locked screen and I found the login screen without any graphics at all.
I was terminal like and it prompted me for a password.

What could have happened?

I did a remote update earlier in the day:
> bomber 4:4.4.2-0ubuntu1 => 4:4.4.5-0ubuntu1
  kdebase-runtime 4:4.4.2-0ubuntu4.1 => 4:4.4.5-0ubuntu1
  kdebase-runtime-data 4:4.4.2-0ubuntu4.1 => 4:4.4.5-0ubuntu1
  kdelibs-bin 4:4.4.2-0ubuntu4 => 4:4.4.5-0ubuntu1
  kdelibs5 4:4.4.2-0ubuntu4 => 4:4.4.5-0ubuntu1
  kdelibs5-data 4:4.4.2-0ubuntu4 => 4:4.4.5-0ubuntu1
  kdepimlibs-data 4:4.4.2-0ubuntu2.1 => 4:4.4.5-0ubuntu1
  kdepimlibs5 4:4.4.2-0ubuntu2.1 => 4:4.4.5-0ubuntu1
  krosspython 4:4.4.2-0ubuntu2 => 4:4.4.5-0ubuntu1
  libkdegames5 4:4.4.2-0ubuntu1 => 4:4.4.5-0ubuntu1
  libkworkspace4 4:4.4.2-0ubuntu14 => 4:4.4.5-0ubuntu1
  libplasma3 4:4.4.2-0ubuntu4 => 4:4.4.5-0ubuntu1
  libsolidcontrol4 4:4.4.2-0ubuntu14 => 4:4.4.5-0ubuntu1
  libsolidcontrolifaces4 4:4.4.2-0ubuntu14 => 4:4.4.5-0ubuntu1
  oxygen-icon-theme 4:4.4.2-0ubuntu2 => 4:4.4.5-0ubuntu1
  plasma-scriptengine-javascript 4:4.4.2-0ubuntu4.1 => 4:4.4.5-0ubuntu1
  python-kde4 4:4.4.2-0ubuntu2 => 4:4.4.5-0ubuntu1
 update-alternatives: run with --install /usr/lib/kde4/libexec/kdesu kdesu /usr/lib/kde4/libexec/kdesu-distrib/kdesu 50 

and I also found some interesting evidence of my 14 months old nephew playing with the keyboard (there are about 30-40 messages of the following kind :D):
> Jan  5 12:31:56 XXX kernel: [309447.018718] atkbd.c: Unknown key pressed (translated set 2, code 0x6d on isa0060/serio0).
Jan  5 12:31:56 XXX kernel: [309447.018726] atkbd.c: Use 'setkeycodes 6d <keycode>' to make it known.
....
Jan  5 13:23:36 XXX kernel: [312546.203214] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
Jan  5 13:23:36 XXX kernel: [312546.203220] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.

I rebooted the machine and all was good, I'm just tryingto figure out if there is a bug in order to report it, but don't really know what else to look for in the logs.

---

### Post by P1C0 on 2011-01-06
Mystery solved, it was my 14 month old nephew. My mother said he went crazy with the keyboard until numbers came up (terminal) :p

---

