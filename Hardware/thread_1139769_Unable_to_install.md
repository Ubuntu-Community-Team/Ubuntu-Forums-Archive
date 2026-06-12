---
title: "Unable to install"
date: 2009-04-27
forum: Hardware
---

### Post by TheShirey on 2009-04-27
I recently got a Dell 12" Mini from my job.  What a joke huh?  Anyways, I ran windows on it for abotu 2 hours before it took me 35 mins to shut it down.  I'm wanting to install Ubuntu on this machine to see if it will run any faster.  I have ran the Windows installation of Ubuntu and when I reboot I get a command prompt with this  **ubuntu@ubuntu:~$** .  It never loads into the GUI.  I have also tried booting from the CD-ROM to just try the environment and get the same thing.  Am I doing something wrong?

---

### Post by Barry Carroll on 2009-04-27
Which version of Ubuntu are you trying and is it 32 or 64 bit?  Do you notice your dell's screen flickering black about three times like it is trying to start the GUI?

The output from /var/log/Xorg.0.log might have some good diagnostic information that will help people to help you.  I see from other threads that this might be down to the mini 12 having the GMA500 graphics chip rather than the more common GMA950 one in netbooks.  Have a look here also: [http://ubuntuforums.org/showthread.php?t=1014534](http://ubuntuforums.org/showthread.php?t=1014534)

---

### Post by Meow27 on 2009-04-27
this question might sound strange, but how much video memory do you have?

---

### Post by brianchidester on 2009-04-27
This is indeed because you have the GMA500 graphics chipset as do all Dell Mini 12s. The version of ubuntu that ships with the system has the proprietary driver for this and therefore works fine. Also the latest Hardy release I believe also has it, as does Jaunty but not Intrepid yet.

---

