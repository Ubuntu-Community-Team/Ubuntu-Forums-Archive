---
title: "kernel-source for the nvidia 6629 driver"
date: 2005-01-27
forum: Hardware &amp; Laptops
---

### Post by Sham on 2005-01-27
Hi all,

I 've tried to instll my nvidia drivers twice now, using apt and the installer from nvidia (its an fx5600). The desktop is really sluggish, so I suppose using the appropriate drivers will speed things along. What I would really like to know is exactly what I need installed on my system for it to work. I have the kernel headers installed for the kernel I am running. 

uname -r returns: 2.6.8.1-4-686-smp (I have a dual cpu)

in /usr/src I have:
linux-headers-2.6.8.1-4     linux-headers-2.6.8.1-4-686-smp    rpm

The thing is, do I need the source too? If so, how do I get the one for the kernel I have?

sudo apt-cache search linux-source-`uname -r` doesn't show me anything.

Any more input would be great. Maybe if someone has a flawless howto they could post it up? I've tried a couple, but I never get into X thereafter. The nvidia installer also complained about a module being installed which could cause problems. I forget the name, but if this rings any bells again, some advice would be good.

btw, its a warty install running Xfree86. At which point do I change the contents of XF86Config-4?

Sorry about all these dumb questions. I'm tinkering with the machine I use for work, so its pretty important that things go as smoothly as possible.

---

### Post by pseudonym on 2005-01-27
Hey I've just been going through the same labyrinth as you! Got things to work eventually, with a little help from some more knowledgeable users. Just to answer some of your questions directly-

1. Linux-source doesn't have any architecture-specific appendages because it's the source for *all* the different kernels compiled from it. In Warty the full package name is linux-source-2.6.8.1 . But you only need it if you are going to install nvidia 6629 and recompile your kernel at the same time (more on that later).

2. The module which the nvidia installer complains about is Riva Frame-Buffer (riva-fb). If you compile your own kernel you can choose not to include it but I used the shorter method (with just headers) and haven't had any problems. rivafb doesn't show up in lsmod so I suppose that's what counts.

3. You edit XF86Config-4 after you have installed the new driver. The nvidia readme includes several different options you can run the new nvidia module with, but the basic ones are included here -

[http://www.uberdose.com/kbase/ubunt...a-geforce-6600/](http://www.uberdose.com/kbase/ubunt...a-geforce-6600/)

As you will notice, this is also a howto for installing nvidia just using kernel headers. One modification I would make to it is to use vi instead of lynx for editing files in console mode, but that's just my preference.

If you feel up to it you can take the more thorough route and recompile your kernel with the new nvidia module. Though I didn't try it myself, Tichondrius' detailed instructions on how to do this look pretty good -

[http://www.ubuntuforums.org/showthread.php?t=7635&page=3&pp=10](http://www.ubuntuforums.org/showthread.php?t=7635&page=3&pp=10)

Good luck with it whichever way you choose :)

---

### Post by pseudonym on 2005-01-27
I just noticed Tichondrius put his method up as an official howto in the faqs/howtos section of this forum -

[http://www.ubuntuforums.org/showthread.php?t=12823](http://www.ubuntuforums.org/showthread.php?t=12823)

---

### Post by Sham on 2005-01-27
[QUOTE=pseudonym]Hey I've just been going through the same labyrinth as you! Got things to work eventually, with a little help from some more knowledgeable users. Just to answer some of your questions directly-

1. Linux-source doesn't have any architecture-specific appendages because it's the source for *all* the different kernels compiled from it. In Warty the full package name is linux-source-2.6.8.1 . But you only need it if you are going to install nvidia 6629 and recompile your kernel at the same time (more on that later).

2. The module which the nvidia installer complains about is Riva Frame-Buffer (riva-fb). If you compile your own kernel you can choose not to include it but I used the shorter method (with just headers) and haven't had any problems. rivafb doesn't show up in lsmod so I suppose that's what counts.

3. You edit XF86Config-4 after you have installed the new driver. The nvidia readme includes several different options you can run the new nvidia module with, but the basic ones are included here -

[http://www.uberdose.com/kbase/ubunt...a-geforce-6600/](http://www.uberdose.com/kbase/ubunt...a-geforce-6600/)

As you will notice, this is also a howto for installing nvidia just using kernel headers. One modification I would make to it is to use vi instead of lynx for editing files in console mode, but that's just my preference.

If you feel up to it you can take the more thorough route and recompile your kernel with the new nvidia module. Though I didn't try it myself, Tichondrius' detailed instructions on how to do this look pretty good -

[http://www.ubuntuforums.org/showthread.php?t=7635&page=3&pp=10](http://www.ubuntuforums.org/showthread.php?t=7635&page=3&pp=10)

Good luck with it whichever way you choose :)[/QUOTE]


Thanks for the reply.  Just to reiterate, can I list the order I would do thiings and you tell me if it looks correct?

1) Make sure the headers are installed
2) Drop out of x, and and run sudo ./NVIDIA-Linux-x86_64-1.0-6629-pkg2.run
3) Edit XF86config-4 to remove dri and glcore, and add glx. Also change nv to nvidia.
4) Add nvidia to the last line of /etc/modules
5) Get down on knee and pray while rebooting.

Lemme know if this is cool

5)

---

### Post by pseudonym on 2005-01-27
That order looks good, only I would add the following -

At 1) make sure you have the GNU C Compiler installed ( gcc) because the nividia binary package checks for it.

At 2) Make sure Gnome is completely shut down - sudo /etc/init.d/gdm stop.

At 3) Edit XF86Config-4 with a few performance options. See [www.ubuntuguide.org](www.ubuntuguide.org) for the simplest things to add to increase performance. Also comment out the three lines in 'Section DRI' at the very end of the file (since you won't be loading this anyway).

At 5) You shouldn't need to reboot (but, obviously, if you prefer, do so). Just do sudo modprobe nvidia when you're done editing and restart Gnome.

Either way, though, you'll still want to pray :-D

---

### Post by Sham on 2005-01-27
[QUOTE=pseudonym]That order looks good, only I would add the following -

At 1) make sure you have the GNU C Compiler installed ( gcc) because the nividia binary package checks for it.

At 2) Make sure Gnome is completely shut down - sudo /etc/init.d/gdm stop.

At 3) Edit XF86Config-4 with a few performance options. See [www.ubuntuguide.org](www.ubuntuguide.org) for the simplest things to add to increase performance. Also comment out the three lines in 'Section DRI' at the very end of the file (since you won't be loading this anyway).

At 5) You shouldn't need to reboot (but, obviously, if you prefer, do so). Just do sudo modprobe nvidia when you're done editing and restart Gnome.

Either way, though, you'll still want to pray :-D[/QUOTE]

Cheers buddy. I'll let you know if I get to the other side.

---

### Post by Sham on 2005-01-27
[QUOTE=pseudonym]That order looks good, only I would add the following -

At 1) make sure you have the GNU C Compiler installed ( gcc) because the nividia binary package checks for it.

At 2) Make sure Gnome is completely shut down - sudo /etc/init.d/gdm stop.

At 3) Edit XF86Config-4 with a few performance options. See [www.ubuntuguide.org](www.ubuntuguide.org) for the simplest things to add to increase performance. Also comment out the three lines in 'Section DRI' at the very end of the file (since you won't be loading this anyway).

At 5) You shouldn't need to reboot (but, obviously, if you prefer, do so). Just do sudo modprobe nvidia when you're done editing and restart Gnome.

Either way, though, you'll still want to pray :-D[/QUOTE]

Ok, I followed the scheme, and all I got was a black screen. no nvidia splash, or gnome. Any ideas?


the end of the xfree log:

```

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

When reporting a problem related to a server crash, please send
the full server output, not just the last messages.
This can be found in the log file "/var/log/XFree86.0.log".
Please report problems to debian-x@lists.debian.org.

```

lsmod report the module as loaded

---

### Post by pseudonym on 2005-01-27
I'm assuming you didn't get anything during the installation which looked odd?

Check your XF86Config-4 again for any anomalies. I know the slightest thing wrong in that can cause graphical grief (eg. when I went to edit it once to add my monitor's name and frequency ranges, I forgot to add the model name into *both* sections which ask for it, and I wasn't able to start X).

Other than that I'm not sure (I'm not an expert in this). Maybe uninstall and re-install? The driver comes with /usr/bin/nvidia-installer. If you run that with '-uninstall' you should be able to get back to where you started.

---

### Post by Sham on 2005-01-28
[QUOTE=pseudonym]I'm assuming you didn't get anything during the installation which looked odd?

Check your XF86Config-4 again for any anomalies. I know the slightest thing wrong in that can cause graphical grief (eg. when I went to edit it once to add my monitor's name and frequency ranges, I forgot to add the model name into *both* sections which ask for it, and I wasn't able to start X).

Other than that I'm not sure (I'm not an expert in this). Maybe uninstall and re-install? The driver comes with /usr/bin/nvidia-installer. If you run that with '-uninstall' you should be able to get back to where you started.[/QUOTE]

Nothing went obvioulsy wrong during the installation. Do you think it is worth uing th version before?

---

### Post by pseudonym on 2005-01-28
You mean the 6611 driver? At least installation of that will be easier, seeing as you can do it through apt. But I guess it depends on whether you really *need* the latest driver, I suppose. You will if you have a high end vid card, I know that much.

I've got a Ti4400 and it still does a great job. It runs Half-Life 2 really well in windows (haven't tried any non-native games under Linux yet). When I had the 6111 driver I was getting great fps in games like Return to Castle Wolfenstein and Quake3, in high detail at 1024x768 (although these are hardly cutting edge games, of course). I upgraded because I want to run Half-Life 2 and a few others in Linux using Cedega.

Of course, if you're game you can try and install the 6629 driver doing the kernel recompile method. That way you can still track the changes in package management. I haven't done it, though, because if something went wrong I'd be in a bit of a pickle. I don't really understand enough about Linux  to know how to fix it. I know that before I upgrade to Hoary I'll just have to uninstall my nvidia driver and then reinstall it after the upgrade using apt, which by then you will be able to.

---

### Post by sharkzf6 on 2005-01-28
I don't know too much about this but I can tell you from first hand experience that if the screen goes blank, X is running, just not with the correct refresh rates for you monitor. To check, after all the hard disk thrashing is over and you're just looking at a blank screen, hit Ctrl-Alt-F1, this will take you to a new login screen from the command prompt without shutting down X. To get back hit Ctrl-Alt-F7, this will take you back to X, although in your case that means a blank screen. See, usually, if X fails to load after several attempts due to some error, it will not start and you will be dropped into the command prompt run level. Look at the hsync and vsnyc numbers in XF86Config-4 and make sure your montior supports what's listed.
Good Luck  :wink:

---

### Post by Sham on 2005-01-28
[QUOTE=sharkzf6]I don't know too much about this but I can tell you from first hand experience that if the screen goes blank, X is running, just not with the correct refresh rates for you monitor. To check, after all the hard disk thrashing is over and you're just looking at a blank screen, hit Ctrl-Alt-F1, this will take you to a new login screen from the command prompt without shutting down X. To get back hit Ctrl-Alt-F7, this will take you back to X, although in your case that means a blank screen. See, usually, if X fails to load after several attempts due to some error, it will not start and you will be dropped into the command prompt run level. Look at the hsync and vsnyc numbers in XF86Config-4 and make sure your montior supports what's listed.
Good Luck  :wink:[/QUOTE]

I set the values myself using the spec sheet in the manual. In the end I used the previous driver (6111) which seemed to work. Hurrah!

Thanks for the tip, I might try 6299 again (If I can be bothered ;) )

---

