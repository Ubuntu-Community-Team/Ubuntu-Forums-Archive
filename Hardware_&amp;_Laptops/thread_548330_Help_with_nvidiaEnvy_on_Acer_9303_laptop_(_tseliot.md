---
title: "Help with nvidia/Envy on Acer 9303 laptop ( tseliot im looking at you :P )"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by Guyver1 on 2007-09-11
installed feisty desktop x86 on the wifes acer aspire 9303 laptop last night.

one weird thing before i carry on, this laptop works perfectly, both in XP and vista, i;ve run some pretty demanding games on it (HL2, LOTRO etc) all with no problems, never had a hardware/driver problem.

on sticking in the Ubuntu install CD i noticed an error that read something like PCI error or PCI Bios error, followed by some strings of numbers/letters etc. it flashes up so quickly that i cant write it down (i will try and take a picture of it)

anyway onto the main issue.

the laptop has the nvidia GeForce Go 7300 with turbo cache.

unlike my alienware m9750 laptop the acer installed with propietry nvidia drivers, but they werent working properly as i couldnt get the resolution i wanted (1440x900). so i downloaded Envy and installed the latest drivers. all went well. rebooted, ran sudo nvidia-settings and changed the screen res and tweaked a few settings, saved the changes. no problem.

now everytime i turn hte laptop on i can work and use it for a few minutes and then i just hard locks, nothing, i have to turn the power off and turn it back on again for it to work.

I've now done a clean install, and got as far as installing envy again.

Question:

was the hard lockup caused by a conflict with hte old nvidia drivers not being removed before envy installed the new ones? how do i properly remove the old drivers and get a clean system to get envy to install the new ones?


cheers

---

### Post by Guyver1 on 2007-09-13
no-one knows how to clean out old nv/nvidia drivers?

---

### Post by w4ett on 2007-09-13
Use Envy to remove the old drivers before installing the new ones......

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select 'vesa' as the driver, then: run envy from the terminal:

```

sudo envy -t
```

Select item #8 (remove old driver...I think)...then reinstall the driver again

---

### Post by Guyver1 on 2007-09-14
ah thank you very much, i shall attempt to ruin the wifes PC this afternoon with this info :)

---

### Post by Guyver1 on 2007-09-14
didnt work,

no matter what i did latest nvidia drivers just mullered the system.
at 
had to revert back to the preinstalled drivers that ubuntu installed during the initial installation :( enabled them, it downloaded hte glx drivers, and its working :/

no idea why envy and the latest nvidia drivers are hard locking this laptop :(

---

### Post by verdomde on 2008-03-08
Hey there, i have the exact same problem on my aspire 9300,runs for a while, with the nvidia drivers, including through envy.
Its ok for a few minutes, but it'll suddenly freeze, especially when i start a gl screensaver.And maybe when i use the broadcomm wireless card. Its real frustrating.
So i guess my question is how do i

" revert back to the preinstalled drivers that ubuntu installed during the initial installation enabled them, it downloaded hte glx drivers,"

And will this enable the acceleration?
help?
p

---

### Post by egglestn on 2008-04-08
I have found that installing the Nvidia driver from the repositories was effective, but I also got the freeze problem, it seems to be a problem within the closed source driver, Unfortunately reverting to the open source driver prevents the fast eye candy of Compiz & Emerald. It seems to be an insoluble problem, and one that is well documented,

---

### Post by egglestn on 2008-04-08
I have just noticed that the lockups occur more when the machine is running on mains power than when it is running on battery. I havent studied too much, but given I have read that it is a power management thing,i shouldn't be too amazed.

---

### Post by bryston on 2008-04-28
I have an Acer 9304 and initially installed 7.04 and have just upgraded to 8.04.  I have had a few random lockups but nothing too serious.  Nothing yet on Hard though.  I use Envy with no probs. The few random lockups i have had i think are related to the envy loaded drivers as they never happened on the proprietry nv drivers.
I dont tend to install and uninstall too much so that might have something to do with it.  I have this tendency to just reload the entire operating system from scratch and go for the clean slate, not sure if this helps.

---

