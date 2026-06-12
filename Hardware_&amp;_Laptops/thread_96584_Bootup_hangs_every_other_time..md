---
title: "Bootup hangs every other time."
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by Doughsay on 2005-11-29
I'm happy with Ubuntu on both my desktop and my laptop, but it was understandably alot harder to set up on my laptop.  I'm running a Toshiba Portege M200 Tablet PC, And I have two problems left that I just can't figure out.

1:  During bootup, it completely hangs half the time while in the hotplug setup, it says "setting up ALSA card 0".  I can't ctrl-c out of it, the only way is to do a hard reboot with the powerswitch, but after doing that it will not hang again.  Only until the next time I shut the computer down properly does it happen again.  And the cycle repeats.  My sound works fine too.  No problems with sound...

2:  It's really hard to understand all this ACPI stuff, the scripts are scattered all over the filesystem.  My monitor blacks after a while...I don't know where to set this, even after turning off power management in xscreensaver, it still blanks after a while.  And it won't come back on.  I had to edit the resume.sh script and the lid.sh script to addin "toshset -bl on" to force the backlite for the toshiba screen back on.  I can now close the lid and it will turn back on afterwards.  I can suspend to ram and come back just fine.  Hibernate doesn't work, but that's a whole other story.  But anyway, the problem is that if I leave my computer for more that 15 minutes, I lose the screen.

So I hope somebody can help me, I've spent a lot of time on this myself and have read through many forums, but haven't found much.  Is there a good HOWTO somewhere explaining the ACPI scripts?

---

### Post by jakev383 on 2005-11-29
> **Doughsay]
1:  During bootup, it completely hangs half the time while in the hotplug setup, it says "setting up ALSA card 0".  I can't ctrl-c out of it, the only way is to do a hard reboot with the powerswitch, but after doing that it will not hang again.  Only until the next time I shut the computer down properly does it happen again.  And the cycle repeats.  My sound works fine too.  No problems with sound...
[/QUOTE]

I have almost the exact same problem, except on my Dell 600m it hangs on the starting of PCMCIA services, but **ONLY** if it's running on batteries. I myself am unable to get it to boot past this point (can't switch to other TTY's, either - complete lock-up) until I plug it into power and hard-reboot.  Then everything boots fine.  It also works as long as I hibernate, but every once in a while my laptop hangs when hibernating so I have to hard-reboot it and then if I don't have the power supply (I usually leave it at work) I can't use the thing until after I go back to work to plug it into the power supply and restart it. I know, take the power supply home with me.... But that would be too easy!  said:**
> 
2:  It's really hard to understand all this ACPI stuff, the scripts are scattered all over the filesystem.  My monitor blacks after a while...I don't know where to set this, even after turning off power management in xscreensaver, it still blanks after a while.  And it won't come back on.  I had to edit the resume.sh script and the lid.sh script to addin "toshset -bl on" to force the backlite for the toshiba screen back on.  I can now close the lid and it will turn back on afterwards.  I can suspend to ram and come back just fine.  Hibernate doesn't work, but that's a whole other story.  But anyway, the problem is that if I leave my computer for more that 15 minutes, I lose the screen.

There are some how-tos on here about the ACPI functions. Your laptop may not support them, and you need APM functions instead.  If you want to keep trying the ACPI stuff, the scripts that control almost all of the functions are in /etc/acpi.  The only one I ever changed was lid.sh so that when I closed it, it would hibernate instead of shutting off the screen.  You may try running the hibernate.sh script from the command line to see if there's errors (probably have to sudo it), or even try manually running the commands out of that file.
Hope that helps a little!

---

### Post by jakev383 on 2005-11-30
I'd started another thread about my boot-on-batteries problem, and someone suggested that I turn OFF the PNP controls in my BIOS.  My Dell didn't have any such option, but I did see one that said something about using USB keyboards/mice in OS's that do not support it.  I turned this option off, and the machine boots normally regardless of whether or not it's on batteries or AC power.  Might be something to look for in your situation, also. Maybe try turning off PNP controls in the BIOS and see if that clears anything up for you.  You may also want to look at your power options and see if there's anything in there about 'S2' or 'S3', which will be in regards to your suspend/hibernate stuff.

---

### Post by Doughsay on 2005-11-30
Thanks for both replies.  I'm using a Toshiba m200 tablet pc, and it's impossible to get into the BIOS.  Or at least I havent figured out how to yet.  In windows, it comes with some control panel tools that allow you to set various bootup options, but other than that, it boots very quickly, there's no "press DEL to enter setup" or anything like that.  As far as the ACPI stuff goes, I still havent found ay solutions, but I havent done too much searching online yet.  I'll come back if I still can't solve it.

---

### Post by jakev383 on 2005-11-30
[QUOTE=Doughsay]Thanks for both replies.  I'm using a Toshiba m200 tablet pc, and it's impossible to get into the BIOS.  Or at least I havent figured out how to yet.  In windows, it comes with some control panel tools that allow you to set various bootup options, but other than that, it boots very quickly, there's no "press DEL to enter setup" or anything like that.  As far as the ACPI stuff goes, I still havent found ay solutions, but I havent done too much searching online yet.  I'll come back if I still can't solve it.[/QUOTE]

From Toshiba's site:
# Press the [Esc] key while the system processes its Power On Self Test (POST). In order to use this method, the computer must be "off", meaning not in sleep/suspend or hibernate mode. Press the power button, then immediately press the [Esc] key (it doesn't hurt to hold the key down). When the POST finishes, you'll be prompted to press the F1 key to enter BIOS setup. Press the [F1] key to access the BIOS setup program.

---

### Post by Doughsay on 2005-12-01
Thanks alot for that info!  I looked through my whole owners manual looking for that...I must have missed it somewhere.  But no luck anyway.  Nothing there about PnP (very bare bios), but I did disable a few things to check.  Thanks for the help though...

---

### Post by spacemonkey on 2005-12-12
jakev383....excellent suggestion.  I have a similar dell 600m, and couldn't boot unless I was plugged in, I also couldn't resume from hibernation, which was forcing me to use windows.  I changed the USB emulation option in the bios, and everything worked perfectly.  I can boot and resume from hibernation.  Thanks!


After further testing....it seems to boot only about 50% of the time....and resume from hibernation is still spotty.  uhg.....

---

### Post by jakev383 on 2005-12-12
[QUOTE=spacemonkey]jakev383....excellent suggestion.  I have a similar dell 600m, and couldn't boot unless I was plugged in, I also couldn't resume from hibernation, which was forcing me to use windows.  I changed the USB emulation option in the bios, and everything worked perfectly.  I can boot and resume from hibernation.  Thanks![/QUOTE]

Glad it worked for you. It worked on mine for a few days, but now I'm back to where I started, I think. I'll probably dig into hotplug's documentation, and see if I can't get some results there. I'll keep everyone posted!

---

