---
title: "[SOLVED] Graphics Card/Display Help."
date: 2008-11-28
forum: Hardware
---

### Post by the badger on 2008-11-28
I've just installed xubuntu 8.10 on my desktop. the display is totally wonky, with a sort of squished in distorted view of the desktop. "Hardware Drivers" dialogue presents me with an option for "ATI/AMD proprietary FGLRX graphics driver" - but i am unable to successfully 'activate' it. when i click the green 'activate', a pop-up 'dowloading' dialogue comes up (after i enter my password) but the driver is not active. i've tried 'activating' this a number of times, but to no avail.

i've run through the system updates that were waiting, and restarted the computer, yet i am still unable to activate the graphics card driver. i checked in synaptic pkg manager, and the 'FGLRX' pkg is installed (as are the search results i got from 'nvidia' in synaptic -- i used to run ubuntu8.04 [*not* xubuntu] on this machine, and according to my notes i had enabled an nvidia driver. does this matter for what i'm doing now, or is the ATI/AMD driver a new/improved thing?).

pointing me in the right direction would be great. i can't seem to find the next step. thank you.

---

### Post by the badger on 2008-11-28
bump?

---

### Post by BunnyGirlDoom on 2008-11-29
Hi Badger.

I had this same problem on my Dell Inspiron 2650. It frustrated and baffled me for the longest time because every so often it woould boot up fine. It only happened when I had the hardware driver installed - which of course is the driver I wanted to use!

Anyway, I think I have solved it on my end. On a hunch I went into BIOS and peaked around. Figured it had to do something with startup. Anyway, my BIOS has a setting for - I think it was - detecting displays. CRT, LCD or Auto. Mine was set to auto. I set it to LCD since I don;t connect a CRT to it. Saved changes, exited BIOS and I haven't had the squished screen thing happen since. 

Hope this is useful!

---

### Post by the badger on 2008-11-30
Thanks BunnyGirlDoom, I'll go give this a try...

---

### Post by the badger on 2008-11-30
My bad.

So, it turns out it was just a screen res issue. I had simply *assumed* it was a driver issue since I have had to enable drivers in previous versions of Ubuntu (totally jumped to the more complicated conclusion...:roll:).

---

### Post by BunnyGirlDoom on 2008-12-02
Glad you got it sorted out!

Next problem: tackling memory and CPU management in Ubuntu :p I geuss I better start searching!

---

