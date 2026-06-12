---
title: "Fujitsu T4010 Shutdown/Suspend/Hibernate/Logout Issue"
date: 2008-08-05
forum: Hardware
---

### Post by Linuturk on 2008-08-05
I own a Fujitsu Lifebook T4010.

I have most everything working beautifully in Ubuntu. I followed these documents:

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D)
[https://help.ubuntu.com/community/T4220](https://help.ubuntu.com/community/T4220)
[https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM](https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM)

So you know how my config has changed. This includes installing a special module, as described in the quoted text below:

> The Tablet Buttons

This only work for the 32bit gutsy. With 64bit you need to compile at your own. I tried the installer but it asks for the linux-wacom develpoment package which isn't in the reps.

there are gusty packages instead of compiling on your own visit here and follow the instructions [http://fjbtndrv.wiki.sourceforge.net/packages](http://fjbtndrv.wiki.sourceforge.net/packages) You can also compile yourself or download there own installer

When installed do this in terminal

sudo nano /etc/modules

then add this:

fujitsu_laptop

Either reboot or do:

 modprobe fujitsu_laptop

 sudo fscd

You see fsc_buttons in green letters and the buttons are working.

If you install the binaries from the ubuntu repository, everything should be set up to have fscd start at login. The problem is that the file /etc/udev/rules/65-fsc_btns.rules sets the /dev/event[0-9] devices to be owned by the group 'users', but (at least for me) you aren't a member of the 'users' group by default. After adding yourself to the 'users' group, fscd should start when you log into Gnome. 

Now, here is the problem I'm having. 

About 1/2 the time I go to Suspend, Hibernate, Shutdown, or even Logout, my screen will go blank, and the system simply stays on. 

Sometimes during this process, there will be disk activity that eventually quits. Then end result of this is always the same. The system never actually powers off, and I have to manually hold the power button to shutdown.

I've attempted changing ttyl's, restarting X via Control + Alt + Backspace, and cycling the brightness on the system (which does nothing because the screen is off)

I need suggestions as to what logs to look into, and how to figure out this issue. It doesn't happen on a consistent basis, so there must be something I'm doing to prompt this behavior.

---

### Post by Linuturk on 2008-08-12
1 week bump. I need some help :(

---

### Post by Proj on 2008-08-12
Hi, I'm new with Linux and don't really know much about how it works but I've encountered the same problem. The cause was a program called "hibernate" which I installed just out of curiosity. After I unistalled it through the Synaptic Package Manager the computer works fine! I'm using Ubuntu 8.04 Hardy.

---

### Post by Proj on 2008-08-14
Hm, even with that "hibernate" program removed i have the same problem. The screen goes blank on shutdown/reboot/suspend. But not every time, as mentioned. 
I'm running on 8.04 Hardy and the only configuration I've done so far is installing the Wacom drivers and adding the Wacom lines to xorg.conf. I had no problems shutting down the computer before this so the problem must be lying somewhere in the wacom installation/configuration.

---

