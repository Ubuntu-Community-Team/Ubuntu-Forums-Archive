---
title: "HELP with shutdown after upgrade to 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by jeffrb on 2009-11-02
Hi,

Just finished upgrading to 9.10 from 9.04 -- an improvement over 9.04.

Problem:

Shutting down:

during the shut down process I get the following message:

*Deactivating Swap...
[350.020127} Buffer I/O error on device Loop0, logical Block 3106820
(then I get a blinking courser)

any suggestions, where should I look, etc.?

Toshiba Laptop
Pentium 1.5 Ghz
1 Gb ram

Jeff

---

### Post by RickSGM on 2009-11-02
Refer to this thread here:

[http://ubuntuforums.org/showthread.php?t=1306789](http://ubuntuforums.org/showthread.php?t=1306789)

It worked for me.  That's the only problem I had on the new install.  I didn't add any software, for I already had on the 9.04 what I wanted.  
By the way:  I installed 9.04 on my Dell Inspiron a few months ago, and upgraded this past weekend.  Everything looks ok.

---

### Post by jeffrb on 2009-11-02
> **RickSGM said:**
> Refer to this thread here:

[http://ubuntuforums.org/showthread.php?t=1306789](http://ubuntuforums.org/showthread.php?t=1306789)

It worked for me.  That's the only problem I had on the new install.  I didn't add any software, for I already had on the 9.04 what I wanted.  
By the way:  I installed 9.04 on my Dell Inspiron a few months ago, and upgraded this past weekend.  Everything looks ok.
Thanks, but I tried sudo shutdown -h and I still get messages and the computer fails to shutdown..

Thanks again

Jeff

---

### Post by RickSGM on 2009-11-02
Read farther down, about the bottom of the page.  Look on beyond the shutdown -h command.     You need to add the line to the halt script.  

It's post #14 onward.

---

### Post by jeffrb on 2009-11-07
> **RickSGM said:**
> Read farther down, about the bottom of the page.  Look on beyond the shutdown -h command.     You need to add the line to the halt script.  

It's post #14 onward.
Thanks for you help.  I did try "sudo shutdow -h now" from the console but the same thing happens.
Ubuntu starts the shutdown process and somewhere in the middle of the process the computer just goes idle.  I have to hit the power button on the computer to power off.  Note that I have a dual boot configuration on the compute--It will boot in Win XP or Ubuntu.  Everything worked OK until I updated to ubuntu 9.10. Otherwise everything else works perfectly. 

I manually downloaded ubuntu 9.10 and made a CD from the .iso and did a clean install on another hard drive.  No problems with the clean install works 100%.  

Thanks again for your help


Jeff

---

