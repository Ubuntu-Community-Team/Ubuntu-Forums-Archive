---
title: "Someone please go wake up my pc card"
date: 2009-07-19
forum: Hardware
---

### Post by lumix on 2009-07-19
From Edgy to Jaunty my wifi pc card has failed to reawaken along with the rest of the kids after nap time (S3 naps, anyway).  How can I wake it up?  The only clue I have is that reinserting it works (but this is not a good solution, given the wear and tear factor).

---

### Post by hansdown on 2009-07-19
Hi lumix.

Can you post your hardware specs? Someone here can likely help.

---

### Post by lumix on 2009-08-03
Well it doesn't seem to matter what the hardware, as this is now the 3rd laptop (and again, third or fourth ubuntu distro) that does this.  I just did a brand new install of Jaunty on a Dell Latitude D600, and my last was a brand new install of Intrepid on an older Compaq Evo N600c.  These are as standard-issue as it gets, so I can't believe that no one else is experiencing this.

---

### Post by hansdown on 2009-08-04
I see they used different wi-fi cards at times.

[http://answers.yahoo.com/question/index?qid=20070910100241AAmGBqB](http://answers.yahoo.com/question/index?qid=20070910100241AAmGBqB)

Not sure how you feel about experimenting, so this second thread may have an easy solution.

The thread is not about waking the wireless, but the post at the bottom suggests a simple bios adjustment to keep the wifi on.

[http://ubuntuforums.org/showthread.php?t=962120](http://ubuntuforums.org/showthread.php?t=962120)

---

### Post by lumix on 2009-08-17
Ah, but again, I'm talking pcmcia, so I'm not using the builtin wifi.  

Two fudges to make the pc-card (cisco airo-net) wake up:

1) eject and insert

2) eject and insert ...er, pccardctl eject, pccardctl insert, that is.

Interestingly, pccardctl info *still* knows the card is there, but no lights.  AND, ifconfig -a shows both eth2 and wifi0 (same), but ifconfig up or down says no such device!

So wanting to go with fudge, I thought *simple, I'll just make a wakeup-pccard.sh and put it into /etc/acpi/resume.d*.  Well I forgot that this is Ubuntu-Linux, so nothing is ever as it would seem.  Though the script (which does option #2) works lovily, it doesn't run on suspend-wakeup.  Silly me, following the documentation...

So now I just have to start another hobby and figure out 

-what does Jaunty use for suspend
-what does *that* use for wake-up scripts

Sometimes I think, *maybe socialism does work.*

And other times...

...*thanks for the reply*

---

### Post by lumix on 2009-08-19
Figured it out.

---

### Post by hansdown on 2009-08-19
Glad you got it sorted lumix.

If you post the solution, other members can benefit, including myself.

---

