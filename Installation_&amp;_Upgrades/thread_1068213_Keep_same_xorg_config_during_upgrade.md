---
title: "Keep same xorg config during upgrade"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by ghostmunch on 2009-02-12
I want to upgrade to Intrepid and keep the same xorg.conf file that is with my Hardy installation.

Here's why. My monitor is an off brand called X2gen that didn't have any compatibility with linux so I had to hand configure xorg.conf. I want to keep this monitor because it's a pretty good monitor(I like that it's big and has a high resolution) and I got it cheap.

I can't reconfigure xorg.conf after install or even start installing because I only have this one monitor which doesn't even show a command prompt if xorg.conf isn't configured.



Is there a way to preserve the xorg.conf file during an upgrade?

I would be using a dvd to upgrade.

---

### Post by ghostmunch on 2009-02-14
I've done some more research through google.com and have found others with similar questions, but no solutions that look like they would work.

---

### Post by ghostmunch on 2009-02-14
To show some background on this topic here are some references to the original problem.

[Question about x2gen problem here on ubuntuforums]("http://ubuntuforums.org/showthread.php?t=788560")

[Question about x2gen monitor problem on linuxquestions.org]("http://www.linuxquestions.org/questions/fedora-installation-39/monitor-driver-needed-428698/")

---

### Post by Mark Phelps on 2009-02-14
> **ghostmunch said:**
> Is there a way to preserve the xorg.conf file during an upgrade? 
I would be using a dvd to upgrade.

You could do the following:
1) Copy the current xorg.conf to external media (USB stick)
2) Do the upgrade -- and let the system replace the xorg.conf
3) Don't boot into a desktop, boot into a command line
4) Save the new xorg.conf under a different name
5) Copy the old xorg.conf as xorg.conf, making it the default config file again
6) Reboot, but into a desktop this time
7) Use an editor (Gedit, Nano) to open both xorg.conf files and see what's different between the two.
8) You could then experiment, either by updating the "old" file with stuff from the "new" file, or by pasting the "old" stuff into the "new" file and making it the default.

If X won't start, use Alt-F1 or Alt-F2 to go back to command line and edit with Nano.

---

### Post by ghostmunch on 2009-02-17
Thanks Mark

>  Mark Phelps said:
You could do the following:
1) Copy the current xorg.conf to external media (USB stick)
2) Do the upgrade -- and let the system replace the xorg.conf
3) Don't boot into a desktop, boot into a command line
4) Save the new xorg.conf under a different name
5) Copy the old xorg.conf as xorg.conf, making it the default config file again
6) Reboot, but into a desktop this time
7) Use an editor (Gedit, Nano) to open both xorg.conf files and see what's different between the two.
You could then experiment, either by updating the "old" file with stuff from the "new" file, or by pasting the "old" stuff into the "new" file and making it the default.

If X won't start, use Alt-F1 or Alt-F2 to go back to command line and edit with Nano.

X does start but my monitor does not detect it. I couldn't even get to the command line after an install or upgrade.

It's funny that I had and old CRT monitor that worked right away with ubuntu. I used that monitor with my current install of Ubuntu and configured the xorg.conf for this flat screen manually. Now Ubuntu works with the flat screen but my CRT monitor has been given away.

I am going to see if I can find some one with a CRT monitor that I can borrow to configure xorg.conf. 

It would be an interesting challenge if some one has a work around for this.;)

---

### Post by avtolle on 2009-02-17
The closest I've come to achieving this (on Apple ppc hardware, FYI) is to do the network upgrade; otherwise, a fresh install, with the xorg.conf file backed up to a flash drive, and then copying it over has been the only way I've "sorta, kinda" made it work. One small advantage that I did have was that even though the monitor was not recognized by the "Live CD", I could at least get to a command line after an alternate CD installation.

---

### Post by ghostmunch on 2009-02-17
Thanks avtolle

I was considering a network upgrade. How can I make sure the xorg.conf file doesn't change doing it that way.

---

