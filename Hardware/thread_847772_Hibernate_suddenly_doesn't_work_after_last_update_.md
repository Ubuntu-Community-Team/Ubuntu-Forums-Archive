---
title: "Hibernate suddenly doesn't work after last update sleep never did"
date: 2008-07-02
forum: Hardware
---

### Post by pstasho on 2008-07-02
Hi all, 

I'm a windows convert and am loving Ubuntu so far.  I have this new issue in which hibernate suddenly doesn't work since my last update but worked previously.  When I try to hibernate, it looks as though all goes fine but when I boot up the OS just boots to startup instead of restoring the pre hibernate state.  Any one else having this issue since their last update?  What gives?

Dell Inspiron D430 with Gutsy

I've also noticed that sleep doesn't work, although it never did but I would like to fix this as well.  When my lt sleeps after 40 mins, I try to wake it but it seems that within 30 seconds of doing so the system just shuts down.  I notice before the shutdown there's a message saying that the computer had problems sleeping.

---

### Post by pstasho on 2008-07-13
ping...anyone??

---

### Post by cdtech on 2008-07-13
As far as the suspend goes.........

You may need to edit "/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux" and replace "/usr/sbin/pm-suspend $QUIRKS" with "/etc/acpi/sleep.sh force" somewhere around line 74.
It worked for me!

Hope it helps.

---

### Post by pstasho on 2008-07-13
Excellent!  That seems to have worked for suspend!  This is awsome as I never had suspend working before!

Now, could someone please help me with getting hibernate to work??

---

### Post by empty_tank on 2008-07-13
see [http://ubuntuforums.org/showthread.php?t=850755](http://ubuntuforums.org/showthread.php?t=850755)

This is how i solved my hibernate issue.

good luck.

---

### Post by pstasho on 2008-07-13
Thanks empty_tank but no such luck:(

I only get the flashing cursor with blank screen when trying to hibernate.  I'm also noticing that my caps lock and hdd lights flash simultaneously.  Another thing I noticed when looking for my swap on the partition editor is that my swap and extended are the same exact size and seem to occupy the same space.  Is this normal??

---

### Post by pstasho on 2008-08-01
Ok, so since no one has been posting here I decided to go out and do some looking for myself.  There are two possible reasons which hibernate can not be working, that I have found.  One is the UUID of my swap partition "magically" changed, which seems to happen.  This is not the case for me.  

The other is that my laptop monitor is not identified correctly in xorg.conf.  I believe that this is the issue.  I notice that when I boot up my monitor does flash a couple of times, ever so briefly, but that makes me think that the right display drivers aren't being applied and that a generic driver is being applied.  When I do look up my display settings, I get that my monitor is a generic monitor.  

Anyone know how I can apply the correct monitor in xorg.conf and/or where I can find this information in xorg.conf?

BTW here's my output for my montor info when running:  lspci -v

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Dell Unknown device 0201
        Flags: bus master, fast devsel, latency 0
        Memory at eff80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

---

### Post by cdtech on 2008-08-01
> **pstasho said:**
> Thanks empty_tank but no such luck:(

I only get the flashing cursor with blank screen when trying to hibernate.  I'm also noticing that my caps lock and hdd lights flash simultaneously.  Another thing I noticed when looking for my swap on the partition editor is that my swap and extended are the same exact size and seem to occupy the same space.  Is this normal??

I've always had issues with my hibernate and suspend since my upgrade to Hardy. I changed the file as mentioned above for my suspend to work when my laptop lid is closed as far as the hibernate I just use an alias within my .bash_aliases file:
```
alias hibernate='sudo /etc/acpi/hibernate.sh force'
```
and type it in the termianl.

I don't know if this has been fixed as this works ok for me at the moment.

---

### Post by pstasho on 2008-08-02
Thanks for the reply cdtech!  Where is the .bash_aliases file?  I checked out ~ but I only see .bashrc, .bash_history, and .bash_logout.

---

### Post by Gagle on 2008-08-03
> **pstasho said:**
> Thanks for the reply cdtech!  Where is the .bash_aliases file?  I checked out ~ but I only see .bashrc, .bash_history, and .bash_logout.

You can set your aliases in the .bashrc file also.
Some other distros may have a separate file for aliases,or maybe he created a alias file for convenience .

You can also create a panel launcher.

With linux, all options are open.   :guitar:

regards,

G.

---

### Post by pstasho on 2008-08-03
Ok so the alias for typing in hibernate at the command line worked.  But it only worked to the extent of running the hibernate script:(  I still was unable to properly enter into the hibernation state.  I still get the same results as what I have posted above.  This really points me in the direction of the hibernate script and my hardware not being used/identified correctly.

Anyone have input to my idea of my monitor identification in xorg.conf?

---

