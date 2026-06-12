---
title: "ubuntu showing blank screen after trying to load"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by jet29 on 2009-11-02
I have installed fresh 9.1 alongside win 7, it worked a few times and now when i choose option to boot to ubuntu it shows the logo and the screen goes blank,
 
I have to boot to windows and then reset and then the system boots to ubuntu,
what needs setting changing, i had no problem with previous version. I also got random kernel errors,
 
I have notice alot of people having problems with this version, i would like to use an alternative but for a new user it is offputting not nowing where to start and what settings to do, since i cant get to the graphical screen or terminal,
 
Please someone help or i'll have to go to win 7 or other linux distro!!

---

### Post by jet29 on 2009-11-02
Bump
 
It only runs when booing win 7 first and restarting then ubuntu loads, what is making it stuck? thanks

---

### Post by jet29 on 2009-11-02
anybody care to help!! I'm about to pull my hair out!!!

---

### Post by danmiddle2 on 2009-11-02
Not sure if this will help, but I am having a very similar issue, which may be related.

Whilst I haven't fixed it, I have made a little progress, which might help. I tried booting the liveCD and got a blank screen. I enabled the noapic nolapic and noacpi boot options on the LiveCD and this worked.

I then installed the system, rebooted and have the same blank screen issue as before.

I have tried editing the grub menu entry to apply the noapic/nolapic/noacpi options manually for a single boot, but this doesn't seem to work. This could be because Karmic uses Grub2 and I am not entering the parameters correctly.

I'll keep you posted if I get any further.

Dan

---

### Post by danmiddle2 on 2009-11-02
Ok, I am now into my system and this is what I did. Hopefully it will be of some use to you:

When you switch the machine on hit "esc" to get to the grub menu list (this may come up automatically on a dual boot system).

Scroll to the entry for linux and hit "e"
then you should see a line ending in "ro quiet splash" or something like that. Scroll to the end of that line and delete "quiet splash" and add "noacpi nolapic noapic nomodeset". (please google these as I don't accept any responsibility for issues. Then hit Ctrl+X to boot those parameters.

If that works, then play around with which one or combo it was that actually made it work on your system.

I read somewhere about nomodeset being to do with the Intel graphics drivers crashing.

Once you've worked out which ones were key... add them to your bootloader permanently.

Hope that helps with your issue too! Good luck!

---

### Post by jet29 on 2009-11-02
Excellent thanks to danmiddle2. 

I tried playing about with the initial file and adding those settings brings up the gui, and boots to ubuntu main screen!!

as a try i just deleted quiet splash and did not add the extra entries and this also worked and also i did each indidual entry on its own and its running with any of those entries also.

Once again thankyou very much dan, i really appreciate it.

Now i need to sort out the sleep/hibernation problem where the system locks up after trying to resume!

---

