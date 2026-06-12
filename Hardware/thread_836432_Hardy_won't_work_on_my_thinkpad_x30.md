---
title: "Hardy won't work on my thinkpad x30"
date: 2008-06-21
forum: Hardware
---

### Post by rad_sci_guy on 2008-06-21
I've tried fresh install as well as upgrade from gutsy several times over the past 2 months to try and get hardy to run on my ibm thinkpad x30.  It will always freeze up. (everthing visible on the screen but nothing response, cursor doesn't move and I can only hard shutdown with power button).

I've sent a bug report with no response.  I've read all the forum posts regarding x30 problems but no solution works.  It's too bad because hardy runs perfectly on my desktop and my wife's acer laptop too.

Does anyone have any idea what could be causing this?  There is no pattern to the freezing at all.  I have the intel i810 graphics drivers and am running the wifi through a pcmcia card from d-link.  The system is working flawlessly with Gutsy so this is very puzzling.

Any help is greatly appreciated.
:confused:

---

### Post by pietjanjaap on 2008-06-22
remove wifi and network, and try again?
search on your videocard?
search on other hardware?

---

### Post by rad_sci_guy on 2008-07-15
I've tried hardy again since my initial problem and the problem still persists.  I've even tried it without the wifi card plugged in and not running any programs and I still get a random freeze up occurring.  I've had to switch back to Gutsy for my thinkpad which runs perfectly.

I hope that 8.10 will contain some fixes for these laptops that keep locking up on people.

---

### Post by francesco44 on 2008-07-20
I experienced the terrible "FREEZE" on my X30 also. Fortunately my production machine is a X31 running under XP. I prefer (infinetely) Hardy....but it seems inpossible to use it professionaly. There is many post and many bug reports on this freeze problem. Your post clearly states that there is a sort of "computer dependency". What surprise me is the amount of answers in the forum giving all sort of different answers.:

-unplug your wifi
-use Opera or FF2 instead of FF3
-go back to the previous Kernel.....

I hope that amongst the infine set of possible answer....one will do the job.

My experience is as following: since the install of Hardy....many month with random freeze. This stopped with the "before the last one kernel update". Then came back with the last kernel update. I am not the only one in that case, according to other post. But this maybe an effect of randomness.

---

### Post by tennvic^ on 2008-08-09
Seams to be solved on [http://ubuntu-utah.ubuntuforums.org/...d.php?t=409247](http://ubuntu-utah.ubuntuforums.org/...d.php?t=409247)
with a X31, may be it helps on a X31

Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

I have a similar pb after upgrading from gutsy.

tennvic

---

### Post by rad_sci_guy on 2008-08-21
Thanks Tennvic

That addition to the blacklist seemed to fix my Thinkpad for the time being.  I've run it all day without any freeze up. 

Hopefully the word spreads for others suffering from this problem

:)

---

### Post by rad_sci_guy on 2008-08-24
Well unfortunately my laptop has now frozen up 3 more times since trying the blacklist fix earlier.  Once again the freeze is random and without any warning.

:(

---

### Post by rad_sci_guy on 2008-08-24
I've been searching the forums for the last couple of days for a solution to the hardy freeze.  I came across a fix where you enter the following in the menu.lst file that affects the system startup.

highres=off nohz=off irqpoll

here's a link to the thread that I found the solution in.  The post that has the instructions is #29

[http://ubuntuforums.org/showthread.php?t=779231&highlight=highres%3Doff&page=3](http://ubuntuforums.org/showthread.php?t=779231&highlight=highres%3Doff&page=3)

My system seems to have taken (hopefully for good this time) to the fix.  I've turned the system on and off and let it run for a good few hours without a system freeze.  This fix also seems to speed up my startup with the ubuntu orange bar.  Initially the orange bar would pause for a good 15-20 seconds then proceed to extend to the end.  Now it doesn't pause at all.

I'll report back after a few more days to let everyone know if my laptop is still freeze free.

---

### Post by rad_sci_guy on 2008-08-26
Just an update.

I've been running my laptop for the last 3 days without a single freeze up after applying the highres fix.
:)

---

### Post by nickgaydos on 2008-08-26
Thats a good thing! :-)

---

