---
title: "Unable to run *buntu on Dell Inspirion 1501"
date: 2010-12-17
forum: Hardware
---

### Post by bluedalek on 2010-12-17
Hey All

Just trying to install *buntu on a Dell Inspirion 1501.  It has an AMD 64 X2 processor, and an ATI 1100 graphics card.

I am able to run the live CD and install the OS with no trouble.  I have tried Xubuntu 10.04 & Kubuntu 10.04 32 & 64bit versions.

I have also tried the alternate installer for Xubuntu.

After the system installs, I am able to run updates and install various software packages (nothing to do with graphics drivers) and upon restarting, the system gives me a grey screen.  No errors that I can find.

I have tried editing the GRUB with the following:

pci=nomsi

acpi=force irqpoll pci=nomsi

acpi=force irqpoll

Makes no difference, I still get the grey screen.  Am I missing something?

Thanks in advance!

---

### Post by sikander3786 on 2010-12-17
Did you install the proprietary drivers for you graphics card? I don't know if they are available via repostiroes or not. I am an Nvidia guy :-)

Did you try with 'nomodeset' or 'radeon.modeset=0' parameter in Grub menu?

As you said, it is only a grey screen or do you see any error messages before you get there?

---

### Post by bluedalek on 2010-12-17
Thanks for the quick reply!

No, have not installed any proprietary video drivers.

I'll try 'nomodeset' or 'radeon.modeset=0' and let you know.

No error messages, don't even get the splash screen.

---

### Post by sikander3786 on 2010-12-17
In the Grub menu, you need to replace the words "quiet splash" with "nomodeset" or "radeon.modeset=0" (without quotes).

Let us know about your progress.

---

### Post by bluedalek on 2010-12-17
thanks, it worked with the 'nomodeset' entry on the end of the 'quiet splash'.  Did not have to remove it.

Will see if issue returns, and if it does not work, will remove the 'quiet splash'

---

### Post by sikander3786 on 2010-12-17
That 'nomodeset' parameter is not a permanent solution. It just lets you boot to sort of safe graphics mode.

Once you are able to boot to the desktop, check under System > Administration > Additional Drivers and install the proper drivers. If available and installed, the issue shouldn't re-appear.

---

### Post by james_xxx on 2010-12-17
bluedalek,

There are **no** proprietary drivers available for your graphics card. Do NOT try to install any drivers from AMD's site.

The drivers that Ubuntu is using by default are your only real option.

It is very disappointing to see so many people unaware of this, as this has been the case for older ATI video adapters for a long time.

I have the very same laptop, apparently with the same hardware. It is presently running Fedora 14. I did have to add "radeon.modeset=0" to the grub menu (actually "**R**adeon.modeset=0" in Fedora). Also, I *believe* I also wound up adding "acpi=off", or something similar. Unfortunately, I do not have that laptop with me at the moment.

I do get an ACPI-related error each time I boot up, but despite this, it seems to run fairly well.

---

### Post by bluedalek on 2010-12-17
Hi James

When you have a chance, could you kindly post what you have in your Grub? I'm setting this up for a friend who is out of town, and would rather have it fixed once & for all, and not have to worry about it down the road.

Thanks in advance.

> **james_xxx said:**
> bluedalek,

There are **no** proprietary drivers available for your graphics card. Do NOT try to install any drivers from AMD's site.

The drivers that Ubuntu is using by default are your only real option.

It is very disappointing to see so many people unaware of this, as this has been the case for older ATI video adapters for a long time.

I have the very same laptop, apparently with the same hardware. It is presently running Fedora 14. I did have to add "radeon.modeset=0" to the grub menu (actually "**R**adeon.modeset=0" in Fedora). Also, I *believe* I also wound up adding "acpi=off", or something similar. Unfortunately, I do not have that laptop with me at the moment.

I do get an ACPI-related error each time I boot up, but despite this, it seems to run fairly well.

---

### Post by webb1976 on 2011-01-19
My cousin gave me his old Dell Inspirion 1501 laptop as well.

This morning I tried to install Ubuntu 10.04 LTS using a Live CD. The screen shows a couple of color lines and that's it (I know it is attempting to load because I can hear the CD drive running).

Will this method work for me as well???

---

### Post by webb1976 on 2011-01-19
My cousin gave me his old Dell Inspirion 1501 laptop as well.

This morning I tried to install Ubuntu 10.04 LTS using a Live CD. The  screen shows a couple of color lines and that's it (I know it is  attempting to load because I can hear the CD drive running).

Will this method work for me as well???

---

### Post by bluedalek on 2011-01-19
> **webb1976 said:**
> My cousin gave me his old Dell Inspirion 1501 laptop as well.

This morning I tried to install Ubuntu 10.04 LTS using a Live CD. The  screen shows a couple of color lines and that's it (I know it is  attempting to load because I can hear the CD drive running).

Will this method work for me as well???

You'll have to give it a try.  Been working for me without any problems so far.

---

### Post by webb1976 on 2011-01-19
Give what a try???? Installing using the "radeon.modset=0" at the boot menu?

---

### Post by bluedalek on 2011-01-19
> **webb1976 said:**
> Give what a try???? Installing using the "radeon.modset=0" at the boot menu?

All of the above.. give all of the steps listed in this thread a try.  The laptop is not mine, so I don't have it to reference. If the first thing you try does not work, try the next, and so on  :D

---

### Post by webb1976 on 2011-01-20
How do you add the paramter to grub, when I cannot boot to Ubuntu.... I get nothing at the login screen.
 
Is ther something you can type in at boot that will allow you to enter in manual boot settings??

---

### Post by webb1976 on 2011-01-20
I figured it out.....
 
I held down Shift during boot process to bring up grub menu.... I then added the command to boot...... Once it booted up I changed the /etc/default/grub file and then executed grub-update.
 
Rebooted fine.

---

### Post by webb1976 on 2011-01-21
Still working fine after several restarts...... Thanks guys

---

### Post by joeyvegas on 2011-02-10
I have the same problem with a Dell 1501. I used the radeon.modeset=0 line in the Ubuntu 10.10 netbook boot setup and it allowed me to install. I got through the whole install and then when it forces me to reboot, I get the grey screen again. Is there a way I can make the grub addition permanent? or a way I can edit the config during install? I'm stuck.

---

