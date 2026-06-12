---
title: "sony vaio netbook vpcw150xb internal microphone don't works"
date: 2009-11-23
forum: Hardware
---

### Post by robertoaguiarlima on 2009-11-23
I recentily buy a new Sony Vaio Netbook VPCW150XB and install Ubuntu 9.10. Everything works fine, but the internal microphone isn't. 
I already tested a external microphone and it work's. I checked the volume control for the input devices and it is in maximum.
Can someone helpe me?

Thank's a lot!

---

### Post by robertoaguiarlima on 2010-01-05
Hi everyone. 
I solved this problem.
Here the steps for solution:

1.  update your ubuntu by running System->Administration->Update Manager
2. after updating, close the update manager, in some cases is necessary boot the netbook.
3. Open the application System->Administration->Synaptic Package Manager
4. Find and install the package linux-backports-modules-karmic, or give the command in a linux terminal: sudo apt-get install linux-backports-modules-karmic
5. Find and install the package  linux-backports-modules-alsa-karmic-generic, by the synaptic or give the command in a linux terminal: sudo apt-get install linux-backports-modules-alsa-karmic-generic
6. give the command in a linux terminal or press alt+F2: gksudo gedit /etc/modprobe.d/alsa-base.conf
7. In gedit go to the last line and put this new line : 
options snd-hda-intel model=auto
8. Boot the netbook
9.login and go to the application System->Preferences->Sound (audio) or right-click the sound icon in upper task bar and select preferences
10.go to the "In" tab and verify if mute option is unselected. Put the volume in the middle, or outmost a little above the low level.
10. thats all rigth. Yor internal microphone probably is working


Feel free to contact me! 

[email]aguiarlima.roberto@gmail.com[/email]

---

### Post by s13_mills on 2010-01-08
This fix confirmed working with VPCW120AL - I had to go through the additional step of opening alsamixer in terminal, changing the input source to "int mic" and turning up the mic and mic boost volumes in alsamixer also however!

Thank you very much for the help I had been banging my head against the wall with this - everything else on this comp worked just fine, and now the mic does too!

---

### Post by eddyojb on 2010-03-28
Thankyou for this, I previously had to switch boot with Windows everytime I wanted to use Skype or Rosetta Stone. Yet another reason for me to never return to windows and I'm even close to being MS (and stress) free!

---

### Post by openevan on 2010-04-15
robertoaguiarlima:  Many many thanks for the simple solution that you've posted to fixing the internal Mic problem!!

---

