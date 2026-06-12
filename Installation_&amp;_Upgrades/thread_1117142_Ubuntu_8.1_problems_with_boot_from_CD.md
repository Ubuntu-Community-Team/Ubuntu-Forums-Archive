---
title: "Ubuntu 8.1 problems with boot from CD"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by trebory6 on 2009-04-05
Ok, I am new here(and to Ubuntu), so please cut me some slack if I posted this in the wrong place or something.

But anyways I have booted my computer from the CD, but none of the options work at all.  What happens is that I press enter, and the highlighted option stays highlighted, and I can not go up and down through the menu for about 30 to 60 seconds, then I can select it again, and still, the same results. I have tried the parameters from here: [URL="https://help.ubuntu.com/community/BootParametersBootParametersURL], but none of them work.  Mainly because when I hit f6, it doesn't have all the parameters listed.

Also, I have checked the MD5SUM and it was ok.
And here is some information that might be needed:
I downloaded the 8.10 Desktop edition from Ubuntu.com
I then burned the .iso image onto a disk using the recommended program, InfraRecord
I will provide any other necessary information.

Can anyone tell me what's wrong and/or how to fix this?

---

### Post by Mr A Mouse on 2009-04-05
Hi, Trebory,

What kind of hardware are you trying to boot on?

---

### Post by trebory6 on 2009-04-05
It still has windows on it, but I plan on overwriting all the Windows stuff and using it solely for Ubuntu.  But would the DXdiag work? Because I am unsure of the specifics of the hardware.

---

### Post by Mr A Mouse on 2009-04-10
Sorry for the long delay.

OK, as a side note, I had problems with 8.10 erasing the Windows partition on my computer, and I'm given to understand this is a known issue. Make sure you have all of your stuff on your Windows partition backed up. 

As for the hardware, the make and model would be the best place to start. If nothing else, while running Windows, right-click on your "My Computer" icon--this should give you some basic info about your computer.

---

### Post by trebory6 on 2009-04-12
Well, I honestly would like to get rid of everything that is already on there, so that there is no trace of windows at all on the computer, so no backups would be necessary.

And, Here is what it said:

It's an eMachines T3504 with an Intel Celeron CPU 3.0GHz and 1.10 GB of RAM.

Does that help any?

---

### Post by trebory6 on 2009-07-19
I still need to know why it isn't booting.

---

### Post by Possum Films on 2009-07-19
That's a pretty strange problem you are having.

Updating your BIOS may help (there are usually instructions on how to do this on the computer manufactures' website).

You may also want to try the latest version of Ubuntu (9.04) instead of 8.10.

---

### Post by presence1960 on 2009-07-19
sounds like a problem with your iso or cd. Did you MD5SUM the iso? see here:[ MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

make sure the MD5SUM matches the Ubuntu hashes exactly. if it doesn't match exactly your iso is no good.

Did you burn the iso as an image to cd at the slowest possible speed (4x is perfect)?

Do you have a USB keyboard? If so you need to go into BIOS and enable Legacy support for USB.

I know you said you did those other things but double checking won't hurt as will burning a new CD once the iso is verified as matching the hashes.

---

