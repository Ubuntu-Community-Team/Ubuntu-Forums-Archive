---
title: "No alert sound / bell / beep in Karmic"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by tonyyarusso on 2009-11-05
I did a fresh install of Karmic.  My sound in general works.  However, I no longer have any alert sounds for things like irssi hilights.  I understand this is because pcspkr was blacklisted, and everything was supposed to be converted to the Gnome Alert sound as configured in the sound preferences.  While I can play the alert sound in the preferences dialogue to choose one, I never hear it while actually using the system.

---

### Post by prisim on 2009-11-16
Interesting on the comment of pcspkr being blacklisted.  I use SKYPE and the new beta from the repositories performs much better than the default SKYPE with Jaunty.  Since I only have a headset I can never hear a call coming in unless I was close to the computer.  Using 'beep' from the repositories enabled SKYPE to run a script and play a tune whenever a SKYPE call came in and this was a definite improvement.

With the move to Karmic I initially wondered if the PC speaker had a problem,  a little Googling found I needed to enable the PC speaker beeps with 'sudo modprobe pcspkr'.  This enable the 'beep' command again.  However it appears I still need to find how to remove it from the blacklist as on each reboot the PC Speaker beep is quiet until ' sudo modprobe pcspkr' is run again.

Rich

---

### Post by RodGer GR on 2010-01-23
I have the same problem. Is there any new idea. My sound works fine, I can hear the different alert sounds available in 'sound preferences' but I never really hear an alert sound when I should.

---

### Post by Zta on 2010-02-01
I've got the same problem too.  /usr/bin/beep doens't produce the "nice pulseeaudio bing" as described in /etc/modprobe.d/blacklist.conf.
On the other hand, if I modprobe pcspkr it gives the oldschool beep.

I'll add pcspkr to /etc/modules (and possibly remove it from the blacklist) to have this module loaded automatically as I prefer a "horrible oldschool beep" over "nice pulseaudio nothing" ;)

---

### Post by h6w on 2010-02-01
I have no alert sound at all.  I've tried 'sudo modprobe pcspkr' and commenting it out of /etc/modprobe.d/blacklist.conf but I don't get either a 'nice pulseaudio bing' or an 'oldschool beep' :-(

Audio is otherwise working perfectly.

Any other ideas?

---

### Post by h6w on 2010-02-01
I just managed to get it working by unmuting the "Beep" section in alsamixer.

Steps to fix:
1) Open a command terminal (Applications->Accessories->Terminal)
2) Type "alsamixer" at the command line and press enter.
3) Use the left and right arrow keys to move across to the "Beep" control.
4) Press the 'm' key to unmute it.  The box should change from 'MM' to '00'
5) Press the up and down arrow keys to select the volume for the beep.
6) Press escape to exit alsamixer, and enjoy. :-)

---

### Post by cbl016 on 2010-02-22
This is what fixed it for me.

First remove "blacklist pcspkr" from /etc/modprobe.d/blacklist.conf and then run "gconf-editor" in a terminal and set 
/desktop/gnome/peripherals/keyboard/bell_mode to "on" and then reboot

---

### Post by moorecf on 2010-07-04
I am running UBUNTU 10.04.   

I have tried "alsamixer" and there is no "Beep" available !!! 

I have tried: 
First remove "blacklist pcspkr" from /etc/modprobe.d/blacklist.conf and then run "gconf-editor" in a terminal and set
/desktop/gnome/peripherals/keyboard/bell_mode to "on" and then reboot
and it does not help.   

When I install from my UBUNTU 9.10 CD, the code:
====================================================
#include <stdio.h>
int main(int n, char *a[]){
printf("Fred BEEP%c\n",7);
}
====================================================
works fine. 
However, when I upgrade ot UBUNTU 10.04, the alert beep does not work 
from the command line.

---

### Post by COKEDUDE on 2010-12-24
> **h6w said:**
> I just managed to get it working by unmuting the "Beep" section in alsamixer.

Steps to fix:
1) Open a command terminal (Applications->Accessories->Terminal)
2) Type "alsamixer" at the command line and press enter.
3) Use the left and right arrow keys to move across to the "Beep" control.
4) Press the 'm' key to unmute it.  The box should change from 'MM' to '00'
5) Press the up and down arrow keys to select the volume for the beep.
6) Press escape to exit alsamixer, and enjoy. :-)

Does the beep line sometimes have a different name?

---

