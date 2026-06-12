---
title: "CPU Frequency Monitor puts CPU on 40% standard"
date: 2009-08-19
forum: Hardware
---

### Post by Jarige on 2009-08-19
I've got a little problem. Since I put the CPU Frequency Monitor on my panel (gnome) I experienced lags when doing different kinds of things. It was only after a while that I found out that CPU Frequency Monitor was maxing my CPU to 40% (800Mhz) of what it can do (2.0Ghz dual core). Everytime Ubuntu boots, I've got to change it again to 2.0Ghz. How can I put it on there permanently?
My computer will probably boot faster after that... At least gnome would load faster (it takes a pretty long time to load gnome now).
Can anybody help me with this?

---

### Post by Jarige on 2010-02-25
Bumping up an old thread. I have the same experience on my netbook. I do want it to default on the 100%...

---

### Post by shihkster1015 on 2010-02-25
> **Jarige said:**
> Bumping up an old thread. I have the same experience on my netbook. I do want it to default on the 100%...

you can install cpu frequency adjuster to the panel in GNOME. Just add to panel. 
Then you can choose ondemand and it should scale your CPU for you

---

### Post by Jarige on 2010-02-25
Yeah, that's what it defaults to on my netbook, but I want it to default to 100%...

---

### Post by shihkster1015 on 2010-02-25
Sorry mate i musta read it wrong

Here's what you can do

open the click the scaling icon and choose the highest clock speed you see.
then authorize the program and it should be set to that speed for the session.

and why would you want it to default to 100% the whole time?

---

### Post by Jarige on 2010-02-25
Yeah, but the problem is that it does that only that session, like you said...
I want it to be permanent, since I do this every boot, and I feel my netbook is much more responsive after doing so... And it doesn't automaticly go to a higher level on 'ondemand'. It mostly keeps on 800Mhz using it fully...

---

### Post by shihkster1015 on 2010-02-25
I'm not sure if there is anyway to permanently keep the cpu clocked at max. And your computer wouldn't boot faster even if you clocked it to maximum in Ubuntu because the speed of the CPU is determined by the BIOS.

And did you update to the newest version of ubuntu? It  loads pretty fast, usually less than a minute.

What kind of laptop/netbook are you using?

---

### Post by Jarige on 2010-02-25
Well its not the boottime, since at boottime it will be at 100% automaticly. Its more the overal responsivness of the netbook that improves. I noticed the biggest difference when watching Youtube films with Flash player. Those where considerably faster when putting the CPU at 100%...

---

### Post by shihkster1015 on 2010-02-25
Hmm, i'm sorry mate. You'll probably will have to set it every time you log in. I dont know anyway to keep it clocked up

---

### Post by Jarige on 2010-02-25
Thats a pity, but maybe someone else knows what to do :)
Never give up hope...

---

### Post by michaelmast on 2010-02-25
My suggestion is to open the click the scaling icon and choose the highest clock speed you see, then authorize the program and it should be set to that speed for the session.

---

### Post by chewearn on 2010-02-25
Assuming you are using Ubuntu Karmic or Jaunty, see here:
[http://ubuntuforums.org/showthread.php?t=1209386](http://ubuntuforums.org/showthread.php?t=1209386)

Note: prior Ubuntu version has a different method of setting max CPU, so please reply if you are using those.

---

### Post by Jarige on 2010-02-25
You didn't read the whole post, but that is not the solution. I want it to default to 100%, not to do it every session...

---

### Post by nanohead on 2010-02-25
I just tried the method in the linked post above.   I'll let you know if it works

---

### Post by Purkinje on 2010-02-25
I too would like to know how this is done. Instead of having to set the CPUs to 100% every session, it would be really nice if it did this automatically.

If there isn't an option, is it possible to write a script that would perform that operation at startup?

---

### Post by chewearn on 2010-02-25
A while back, I did a test install of Jaunty and use the link I gave in post #12 to set the CPU to 100%. It did work for my system (AMD Athlon 64 / GeForce4 chipset).

---

### Post by Jarige on 2010-02-26
This works for me :)
Thank you :D

I will mark this topic solved...

---

