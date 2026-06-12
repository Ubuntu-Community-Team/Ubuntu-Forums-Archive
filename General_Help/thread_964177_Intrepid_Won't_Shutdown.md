---
title: "Intrepid Won't Shutdown"
date: 2008-10-30
forum: General Help
---

### Post by Matthileo on 2008-10-30
Whenever I shutdown or restart the computer it freezes.
Sometimes it freezes on the orange progress bar and then goes to a blank screen and does nothing, and other times instead of a blank screen it has some text that says
```

* something something something (i don't remember, but it's one line)
* Shutting down ufw...          [ok]
* Shutting down ALSA... 

```
And then it hangs and I have to do a hard shutdown.

EDIT
--HARDWARE-- (if relevent)
Dell XPS m1530 Laptop
Intel Dual Core 2.5 ghz 
NVidia 8600m gt 
4gb ram
320 gb HDD
Dual boot vista and intrepid.

---

### Post by nitrousoxide82 on 2008-10-30
I have a similar setup on my desktop (just with an ATI card instead) and 64-bit Kubuntu Intrepid did the same. I have an Intel motherboard with G33/ICH9 chipset. I have switched over to GNOME-based Ubuntu (I don't see myself embracing KDE 4 just yet), and as far as I could see this has yet to happen. I have noticed that Kubuntu had a different kernel version number (2.6.27-3 for Kubuntu, 2.6.27-7 for Ubuntu), so maybe doing a full update (if not done already) might help?

---

### Post by dcstar on 2008-10-30
> **Matthileo said:**
> Whenever I shutdown or restart the computer it freezes.
Sometimes it freezes on the orange progress bar and then goes to a blank screen and does nothing, and other times instead of a blank screen it has some text that says
```

* something something something (i don't remember, but it's one line)
* Shutting down ufw...          [ok]
* Shutting down ALSA... 

```
And then it hangs and I have to do a hard shutdown.
.........

I have the same issue with it installed in a VMWare VM, so I doubt it is specific to your hardware.

Report it as a bug (if it hasn't already been reported).

---

### Post by Matthileo on 2008-10-30
> **dcstar said:**
> I have the same issue with it installed in a VMWare VM, so I doubt it is specific to your hardware.

Report it as a bug (if it hasn't already been reported).

After posting I found a bug report in launchpad.
I found a fix, but now I have no sound.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274995)

---

### Post by m0ridin on 2008-10-31
I'm havinge the same issue

AMD x64, ubuntu release

i'll just have to keep checking the bug report, I just get a blank screen right after the graphical.

---

### Post by m0ridin on 2008-10-31
Poster 'Suzan' in the launchpad bug report had a tip that worked for me:

open terminal

sudo gedit /etc/init.d/alsa-utils

scroll down to where you see stop)

insert this at the top right after the stop)  :
ifconfig eth0 down

or if you use wireless/both at times, insert this instead/in addition:
ifconfig wlan0 down

worked like a charm for me

Good luck!

---

### Post by woolyninja on 2008-10-31
^ Yep, worked for me too!  Thank you sir!

---

### Post by djwheels on 2008-11-01
Stopping the network interfaces fixed the problem for me on a Thinkpad X31.

---

### Post by dcstar on 2008-11-01
> **m0ridin said:**
> I'm havinge the same issue

AMD x64, ubuntu release

i'll just have to keep checking the bug report, I just get a blank screen right after the graphical.

I have found that manually killing the **amixer** process allows things to continue.

---

### Post by zyxnull on 2008-11-02
I fixed it by just enabling "Audio Settings Management (alsa-utils)" on services

---

### Post by augias on 2008-11-02
neither adding the ifconfig command to alsa-utils nor killing my eth0 from terminal (in fact this hangs terminal indefinitely) nor enabling alsa-utils, nor adding the apci rule in /etc/modules works.

this is quite a bad bug and i'm scared for my hardware after so many hard shut downs with the power button. I don't wanna go back to hardy either, i've got too much custom software, settings and users on this machine. plus intrepid is actually a very nice update on my machine (except for this bug) 
*weep*

---

### Post by carloshiga on 2008-11-03
> **zyxnull said:**
> I fixed it by just enabling "Audio Settings Management (alsa-utils)" on services

I did it but now I got no sound... and the problem is still here.

---

### Post by lovinglinux on 2008-11-03
Here is a better solution

[http://ubuntuforums.org/showpost.php?p=6098072&postcount=6](http://ubuntuforums.org/showpost.php?p=6098072&postcount=6)

---

### Post by babloo75 on 2008-11-24
i face this problem too but not with shutdown but with restart option.
has anyone got the solution about it..
and i have eth0 instead of eth1
will substituting 0 for 1 help me in this terminal command?

---

### Post by asmit21 on 2008-12-17
> **m0ridin said:**
> Poster 'Suzan' in the launchpad bug report had a tip that worked for me:

open terminal

sudo gedit /etc/init.d/alsa-utils

scroll down to where you see stop)

insert this at the top right after the stop)  :
ifconfig eth0 down

or if you use wireless/both at times, insert this instead/in addition:
ifconfig wlan0 down

worked like a charm for me

Good luck!


Dude, that was awesome, I added both
ifconfig eth0 down
ifconfig wlan0 down
after the "stop)"
and ****waaaalaaaa***, perfect shutdown.
I am curious to why this has affected the sound anyways, for alsa is the sound utility and why the networking has anything to do with it not shutting down properly.

I know, "It works, so who cares?", but I am just that kind of person, I think this is the key to fixing this sort of bug!

~Aaron

---

### Post by asmit21 on 2008-12-17
> **babloo75 said:**
> i face this problem too but not with shutdown but with restart option.
has anyone got the solution about it..
and i have eth0 instead of eth1
will substituting 0 for 1 help me in this terminal command?

It would not hurt anything to add both!
ifconfig eth0 down
ifconfig eth1 down

Just in case!

you will not screw you system up unless you remove lines you should not!

---

