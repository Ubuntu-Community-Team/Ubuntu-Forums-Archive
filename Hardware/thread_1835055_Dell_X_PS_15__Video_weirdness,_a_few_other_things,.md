---
title: "Dell X PS 15  Video weirdness, a few other things, and Firefox weirdness."
date: 2011-08-28
forum: Hardware
---

### Post by Coder68 on 2011-08-28
[SIZE=2]I have installed Ubuntu 11.04 onto my Dell XPS 15 laptop and it works for the most part.  I have video weirdness. While I type this I am unable to see what I am typing sometimes. It goes blank and then goes back to black. I get black boxes over my icons sometimes too. (See screen shot) 

When I go to mouse over my wireless notification pop up, it goes away and then if I mouse away it comes back. I have a full high def screen. I wonder of that is the issue. Now I am getting lines in my typing and bold unbold actions. 

This is unusable for school as it sits!  I have removed the Nvidia driver and that only made it worse. I got video tearing so that if I moved a dialog box I would get a 100 copies!  

Firefox is so dog slow that it is all but useless. (It is useful when it is not being slow.) I click on something and it can take 10-15 seconds to respond.   I have a quad core @2.2 and 8 Gigs of RAM. So that is not the issue. I am running the 64 bit version of Ubuntu desktop 11.04.   It is in dual  boot mode with Windows 7. I hate to have to go back to Windows 7 as my main OS...

Now the font went tiny as heck!

Any ideas on how to fix these issues?  

Thank you, 
coder68

p.s. I have tried several suggestions from various sites and posts...
[/SIZE]

---

### Post by lovinglinux on 2011-08-29
Try version 173 of the nvidia driver.

---

### Post by Coder68 on 2011-08-31
Well, it appears that my sytem has the driver for nvidia, but is not using it. "Activated but not in use" It appears to be running on the intel video card. Which is fine for me since I do not game, but the black bars and weirdnesses have to go. 

The resultes of cat /var/log/Xorg.0.log | grep nvidia is a null output.

Looking for intel stuff yeilds the following:

(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,

Any thoughts?

C68

---

### Post by Coder68 on 2011-09-20
Bump.

I do not care about the add on video card, as I do not game or use this for video out. 

I do, however, use this for school and VM's so I need this to not have all this weirdness.

Anyone have any ideas how to fix the Intel video issues?

Thanks,

C68

---

### Post by Coder68 on 2011-09-21
With the Intel video card being so prevalent, I am shocked and disappointed that Ubuntu has not come out with a stable driver. To much moving forward to fast????

Dang it!

If nobody has any other ideas, I will have to install Win7 Pro onto this  laptop. It is a dual boot, but Ubuntu broke the Windows boot partition.  :sad: I wont bother to fix it, I will just use Pro on the entire disk.

At least I get better battery life in Windows 7. Not sure why that is because my other laptop gets way better battery life under Ubuntu. Maybe because it is not an quad core i7?

Getting desperate! I need to get this up and running for class... we are five weeks in!!!!!!!!!!!!!!!

C68

---

### Post by Coder68 on 2011-09-22
Bump, bump.

---

### Post by Coder68 on 2011-09-23
Dang it.

Back to Windows 7 I go.

---

### Post by jocheem67 on 2011-09-23
I've got a dell xps15 with hybrid graphics. It's pretty important that you read the latest news on this non-supported stuff ( by nvidia that is ).There are hacks >> bumblebee, acpi_call, vga_switcheroo...I'm using acpi_call to turn off the nvidiacard.
I run ubuntu and before arch with no troubles on just the intel graphics. 
Start with getting rid of the nouveau and nvidia modules...

---

### Post by Coder68 on 2011-09-30
Well, after I posted that I gave up I figured what the heck, I will just install the latest kernel and see what happens. Kernel 3.1 RC4 fixed the video issues with the Intel "card". I do get some weird boot-up stuff, but it does not seem to cause any stability issues or break anything.

I was not worried about Ubuntu compatibility. I bought this for the quad core 17 and 8 gigs of RAM. If Ubuntu did not run, it was a loss, but not the end of the world. I was glad when everything else worked fine under Ubuntu. I just had the video issue that made it unusable. But that seems fixed now.

What ACPI call do you use to turn off the Nvidia card? I really need to  boost my battery life. It is half as long in Ubuntu as it is in Windows. Go figure.  I do not use that card since I do not game or use  this laptop for videos. Just school and VM's.

Thank you,

C68

---

