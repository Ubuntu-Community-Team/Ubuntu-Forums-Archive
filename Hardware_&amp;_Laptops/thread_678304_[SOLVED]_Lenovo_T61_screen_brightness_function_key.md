---
title: "[SOLVED] Lenovo T61 screen brightness function keys"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by nowhere@cox.net on 2008-01-25
I have my new T61 running just about perfectly. I have a couple issues left I need some help with. When I use the function keys to increase and decrease the screen brightness, the OSD pops up and moves correctly but it does not in any way actually affect the brightness. Also, when I pull the plug and move to battery power, the power management sets the brightness to my requested 50%, the OSD pops up at 50% but again the brightness does not change.

If I ctrl-alt-F1, change the brightness with the function keys it works and when I ctrl-alt-F7 back it sticks.

I'm betting there is a simple fix for this and I know you all know it! :)

Any advice would be appreciated.

Eric

---

### Post by thedaylights on 2008-01-26
I just read on [here]("http://www.tuxfiles.org/linuxhelp/shell.html") that ctr+alt+[F1-F7] opens up a virtual terminal. Maybe this is the problem.

> Pressing Ctrl+Alt+F1 takes you to the first virtual terminal, Ctrl+Alt+F2 takes you to the second virtual terminal, and so on. So, you can switch the virtual terminals by pressing Ctrl, Alt and the function key with the number of the desired terminal.

---

### Post by oofnik on 2008-01-26
Hm, I'm trying to remember exactly what I did for my X60 tablet which was doing the same thing. I'm pretty sure it consisted of disabling a certain kernel module, one of the generic ACPI ones, which had a bug that caused it to conflict with the IBM ACPI module. Now the slider doesn't change when you hit the keys, but the brightness does, so it works out a little better.

I just checked my bookmarks and found it here: [http://luke.no-ip.org/x60tablet/](http://luke.no-ip.org/x60tablet/)
Scroll down to the brightness control entry. It says to disable the 'video' kernel module from loading on boot. Good luck.

---

### Post by nowhere@cox.net on 2008-01-26
Thanks for the try but you are right, blacklisting the video suppressed the OSD but still isn't affecting the brightness. I'll keep looking!

Thanks for the info,

Eric

---

### Post by nowhere@cox.net on 2008-01-27
Here's another interesting piece of info that may help diagnose the problem. If I suspend on AC power and resume on battery then the brightness come up with the adjusted dimmer setting appropriate for battery power.

Any clues?

Thanks,
Eric

---

### Post by nowhere@cox.net on 2008-01-31
Anyone have any ideas on this?  I haven't been able to locate any ideas so far...

Thanks,
Eric

---

### Post by Iceman404 on 2008-01-31
I've been looking for a solution to this as well. So far, no luck, but thanks for sharing your F1-F7 trick! I wouldn't be able to change it otherwise. I'll post anything here if I find anything.

---

### Post by nowhere@cox.net on 2008-02-28
Just bumping to see if a few weeks has revealed an answer. In reading some of the HOWTO's on installing on a T61, it seems that it might be related to this version of the nvidia driver. Anyone know if this is true or have some insight on the release schedule of nvidia drivers?

Thanks,
Eric

---

### Post by cujo on 2008-02-28
I found a fix for mine.  Basically the nvidia drivers that your distro supplies are broken in this regard.  If memory serves, you can just use generic non-nvidia drivers and the brightness controls will work, but that's not any fun.

I downloaded the newest drivers from the nvidia site and had a miserable time getting them to work.  Stuck again.

Then I stumbled upon envy.  It is a tool that will install the newest drivers and it worked like a charm.  It even works through a gui for the terminal-fearing folks.  There are some potential hang-ups (something about removing if you upgrade to a new distro release), but so far I've had no problems.  Just remember to backup your xorg.conf file just in case!

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by nowhere@cox.net on 2008-03-05
Thanks Cujo,

I will look into this. In the mean time I also found a solution. 

i had to modify acpi scripts in order for brightness control to work.
Change /etc/acpi/thinkpad-brightness-down.sh to read:

```
#!/bin/bash
manufacturer=`dmidecode --string system-manufacturer`
case "$manufacturer" in
    LENOVO*)
        echo down > /proc/acpi/ibm/brightness
        exit
    ;;
    *)
        . /usr/share/acpi-support/key-constants
        acpi_fakekey $KEY_BRIGHTNESSDOWN
    ;;
esac
```

and thinkpad-brightness-up.sh is the same as above with "up" instead of "down"


I have been wondering if I had the latest drivers. I have a Vista partition on my machine and went to nvidia's site to get the latest drivers for the Quadro 140NVS but there were no drivers on their site.

I currently have 100.14.19 installed. Synaptic is NOT offering me anything newer...

---

### Post by nowhere@cox.net on 2008-03-06
OK this is frustrating. I changed the scripts as listed and it worked find immediately. I reboot and it no longer works. The scripts are still intact.  Anyone know why it won't work now?

Eric

---

### Post by neurostu on 2008-03-07
So I just changed the scripts and nothing happend ;-(

---

### Post by brohken on 2008-03-09
this doesnt work for me either. im glad the mute button works now (just had to update bios) but it seems that brightness is the last major issue. def an issue with the driver because the brightness works with Vesa

---

### Post by neurostu on 2008-03-09
So I tried to run these two commands directly in the terminal... with and without sudo
```

echo down > /proc/acpi/ibm/brightness
    &
echo up > /proc/acip/ibm/brightness 

```
I get a permission denied message, even when I try sudo....
Could this "permission denied" problem be why the brightness isn't changing?

---

### Post by nowhere@cox.net on 2008-03-10
chmod 777 brightness doesnt seem to make a difference. No brightness change after even though the permissions are wide open...

```
gemorgan@Legolas:~$ ls -l /proc/acpi/ibm
total 0
-rw-r--r-- 1 root root 0 2008-03-10 11:54 beep
-rwxrwxrwx 1 root root 0 2008-03-10 11:54 brightness
-rw-r--r-- 1 root root 0 2008-03-10 11:54 cmos
-rw-r--r-- 1 root root 0 2008-03-10 11:54 driver
-rw-r--r-- 1 root root 0 2008-03-10 11:54 ecdump
-rw-r--r-- 1 root root 0 2008-03-10 11:54 fan
-rw-r--r-- 1 root root 0 2008-03-10 11:54 hotkey
-rw-r--r-- 1 root root 0 2008-03-10 11:54 led
-rw-r--r-- 1 root root 0 2008-03-10 11:54 light
-rw-r--r-- 1 root root 0 2008-03-10 11:54 thermal
-rw-r--r-- 1 root root 0 2008-03-10 11:54 video
-rw-r--r-- 1 root root 0 2008-03-10 11:54 volume

```

The thing that kills me is that it worked when I first modified the scripts. The quit later (I'm pretty sure right after the reboot of the laptop).

I have read some posts about this being a driver issue and people solved it by using envy to install the latest nvidia driver but I can't tell if I already have the latest driver or not. nvidia's site does not even list a driver for windows or linux for the quadro 140NVS card.  I have also read a few horror stories about using envy too.

hmmm.....

Eric

---

### Post by neurostu on 2008-03-10
So i'm pretty sure that it has to do with the drivers as well. Reading that people used to be able to do this makes me think that the newer driver (the one in the ubuntu repos) might be the problem.

I'm pretty anal about keeping my system stable and until I am really sure that envy won't screw up my system when a system update occurs I'm just going to deal with pressing CTRL+ALT F1 and then changing the brightness there.


So you have a T61? What other T61 related customizations have you done?  Do you have suspend/hibernate working?

---

### Post by nowhere@cox.net on 2008-03-10
I have suspend working but not hibernate since I never use it. I use suspend 20x per day. 

Here is how I got it working:

[URL="http://ubuntuforums.org/showthread.php?t=679583"]http://ubuntuforums.org/showthread.php?t=679583
[/URL]

Eric

---

### Post by neurostu on 2008-03-10
Do you ever get a bunch of weird USB messages when you suspend or resume?

Also do you ever get weird screen resolutions during shutdown? (like a screen that is titled 8 times)

---

### Post by nowhere@cox.net on 2008-03-11
When I suspend, the machine switches to terminal mode right  before entering sleep mode and lists many messages about the states of various devices such as USB and such but this is not a problem on my system. It then goes to sleep and the little moon shaped sleep LED stays lit. 

I have not had any graphics problems from suspending. 

It is funny though, when I ask Vista to sleep, every so often, it doesn't shut the machine all the way down but just shuts the screen off. If I am not paying close attention, I can shove the notebook in it's sleeve with the CPU, HD and fans still running which is definitely NOT good. Stupid Vista. This has never happened with Gutsy.

Eric

---

### Post by neurostu on 2008-03-11
I have had the gutsy suspend only make it half way. The moon never stops blinking (1 time in 20).

Other times I can't get it to wake up. This is probably b/c I do something weird like open the screen and then close it again very quickly.  After things like this sometimes i have to hard reset.

---

### Post by nowhere@cox.net on 2008-03-11
Ok,

The envy website gives instructions on how to handle kernel updates and it seems to be pretty simple so I have installed envy and the latest nvidia driver. I removed the additions to my acpi scripts for up and down brightness and rebooted. The brightness keys now work as well as everything else. I think I have a little bit better performance on 3D as well judging from the smoothness of the rotating cube desktop effect.

The only quirk is that the the lowest brightness setting is reached 4 notches before the lowest OSB meter setting so the last four clicks down and the first four clicks up have no effect. No big deal at all.

Thanks for the help. I'll post again in a few days to report if anything was broken on my T61 from using envy and the latest nvidia drivers.

Eric

---

### Post by neurostu on 2008-03-11
So you upgraded to envy, on a scale of 1 to 10 how difficult was it to get envy working?

Have you looked at your framerate when you run glxgears?

Are you using desktop effects? If so do you see an improvement?

---

### Post by nowhere@cox.net on 2008-03-11
If 10 is the most difficult I would say it was a 0. Yep, ZERO! I dl'ed the .deb package, followed the two lines to install and selected envy on the Applications menu. There is one other step if you do not have the universe and multiverse repo's enabled but that is documented too. 

Envy uninstalled the old driver and installed the new driver from the nvidia web page with one click of the mouse then asked to reboot. I did and it works fine so far.

One annoyance tho is that now that the dimming and brightening is working, the battery manager will dim the screen on inactivity but that actually changes the brightness setting and to restore it you have to FN-up back up to max brightness. I just disabled the dim on inactivity....

Eric

---

### Post by neurostu on 2008-03-12
Have you tried dual head support with the new driver?

If you have how is it working out for you?

---

### Post by nowhere@cox.net on 2008-03-12
I have never used dual monitors.

Eric

---

### Post by neurostu on 2008-03-12
I have yet to test the current nvidia driver for dual head, but I will be using my laptop for presentations and if using the envy driver is the difference between being able to connect to a projector or not then I will definately install envy

---

### Post by nowhere@cox.net on 2008-03-12
Remember, all envy does is install the official nvidia driver from nvidia's website...

Eric

---

### Post by neurostu on 2008-03-12
right I know that... but the drivers might support dual head differently.

---

### Post by neurostu on 2008-03-22
So I took the plunge and installed Envy.  It works great and the dual head support was fantastic! Thanks for the advise.

---

### Post by nowhere@cox.net on 2008-03-26
Great! I'm glad I was actually able to help someone in the forums! 

Eric

---

