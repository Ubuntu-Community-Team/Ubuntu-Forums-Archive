---
title: "Cant Suspend/Resume at all on Acer Aspire 7551-7422"
date: 2011-10-02
forum: Hardware
---

### Post by TuxIsAwesome on 2011-10-02
I am having some critical issues with this laptop, everything works, except for the damn suspend/hibernate functions. Quite frankly, this has got my whiskers in a twist and is making me wanna cry and rage uncontrollably.

Here's what happens.

1. I press Suspend
2. It seems to suspend properly
3. I press a button to wake it
4. It wakes, but it seems to also not wake. It appears that the backlight is off, but the HDD Led is showing some activity 

My Graphics card is an ATI Mobility Radeon HD 4250

I am using the FLGRX driver, version 11.9. The open source Radeon Drivers are not an option as they lack stuff I need. The last version of this driver crashed constantly and I really dont wanna have to go back to it. I don't believe suspend or hibernate worked either with 11.8 

Some solutions I have tried are

A. Installing the hibernate package and using those scripts (Same failure to resume)
B. Uninstalling and reinstalling FLGXR 11.9 (Same effect as before)
C. Adding flgxr into the section in /etc/default/acpi-support in order to unload it when it suspend (I dont know that this is actually doing this properly. Should it have "" marks around it?

I have classes coming up and I need to get this fixed one way or another.

If anyone has any insight, I would desperately love to hear about it.

---

### Post by 2F4U on 2011-10-03
Suspend and hibernate actions are written to log files located in /var/log and /var/log/pm-suspend.log is for actions connected to suspend and resume. You should look into this file and see if that reveals any problems.
If that doesn't show anything, open a terminal, set the variable $PM_DEBUG to true and do a suspend from from the terminal.

---

### Post by TuxIsAwesome on 2011-10-03
Edit: Guess what peeps!

I fixorzed it!

Apparently both fglrx and radeon were loading on boot, so the two were for a lack of better terms and to a more apparent guess, fighting over my system.

Changing this line in /etc/default/grub

From this
GRUB_CMDLINE_LINUX=""

To this
GRUB_CMDLINE_LINUX="nohz=off highres=off radeon.modeset=0 nomodeset"

Seems to have fixed it. I have mine booting in verbose-only mode so the splash screen is irrelevant.

However radeon still seems to load as I see it in the output of lsmod, but everything still suspends just fine.

And to add further onto the bright sides, my computer is insanely faster and much smoother now, even using full effects and KDE4.7, I am using less than 20% CPU!


How might I go about permanantly making this annoying as hell "radeon" module never load upon boot. I already added it to /etc/modprobe.d/blacklist.conf and I thought that would work, but it seems like it hasn't. Unless radeon really isn't loading at all and lsmod is just displaying it as other modules might call upon it.

So all in all, not loading the  "radeon" module had the following effects

-Console and Graphical display isn't corrupted on logout/suspend/hibernate/shutdown/reboot

-I can suspend (Yay)

-I can hibernate (Haven't tested, but yay anyway)

-Stuff runs smoother

-Everything just works better.

Thanks for the insight, but yet again I seem to have fixed it though my own tinkering and whatnot.

Now, last question. How to I change the prefix to solved on this thread?

---

