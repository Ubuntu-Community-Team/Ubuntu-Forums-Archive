---
title: "Keyboard not working touchpad ok after routine update"
date: 2012-08-07
forum: Hardware
---

### Post by rpete on 2012-08-07
Hi, after accepting recommended updates (didn't pay attention to which ones), the next time I booted up the keyboard didn't work.  I have Ubuntu 10.04 LTS on a Dell XPS M1530.   I am willing to reinstall and have the 10.04 CD to do that but cannot boot from CD because cannot get into BIOS because nothing happens when I press F12.  Touchpad works fine.  Am able to use the onboad keyboard from System-Preferences-Assistive Technologies and can use terminal. Ran apt-get install updates but didn't help.

Any ideas?  Need to change keyboard?  

Richard

---

### Post by cortman on 2012-08-07
> **rpete said:**
> Hi, after accepting recommended updates (didn't pay attention to which ones), the next time I booted up the keyboard didn't work.  I have Ubuntu 10.04 LTS on a Dell XPS M1530.   I am willing to reinstall and have the 10.04 CD to do that but cannot boot from CD because cannot get into BIOS because nothing happens when I press F12.  Touchpad works fine.  Am able to use the onboad keyboard from System-Preferences-Assistive Technologies and can use terminal. Ran apt-get install updates but didn't help.

Any ideas?  Need to change keyboard?  

Richard

It sounds to me like an incomplete update. In the terminal, run

```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

This should install any remaining upgrade packages.

---

### Post by rpete on 2012-08-07
Hi, tried both commands.  Output="Reading package lists...Done Building dependency tree Reading state information...Done Calculating upgrade...Done 0 upgraded, 0 newly install, 0 to remove and 0 not upgraded"  

What about accessing BIOS in order to boot from LiveCD?

---

### Post by cortman on 2012-08-07
Press F8 to get to the boot menu, and boot from the live CD.

---

### Post by rpete on 2012-08-07
Cortman, in my original post I noted that I couldn't get into the BIOS because I couldn't press F12.  On startup the screen reads "BIOS Press F12"  But my keyboard doesn't work!  

That's the main problem.  Whether I boot from the live CD is a choice I can make once I get the keyboard working.

---

### Post by cortman on 2012-08-07
> **rpete said:**
> Cortman, in my original post I noted that I couldn't get into the BIOS because I couldn't press F12.  On startup the screen reads "BIOS Press F12"  But my keyboard doesn't work!  

That's the main problem.  Whether I boot from the live CD is a choice I can make once I get the keyboard working.

Whoops, sorry! I missed that very obvious fact. :oops: 
But if the keyboard isn't working to get into the BIOS menu, that's unfortunately a keyboard/hardware problem, not an OS problem...

---

