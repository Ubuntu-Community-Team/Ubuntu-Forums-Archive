---
title: "nvidia drivers cause x to go blank"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by ionophore on 2005-10-30
Hey everyone.  I just installed kubuntu a few hours ago and i can't seem to get the nvidia drivers to work.  I install nvidia-glx from the package manager (my card is an FX5800), then run sudo nvidia-glx-config-enable (following the directions...).  When i reboot all i get is a blank screen (once x is invoked).  Booting to a command prompt and running nvidia-glx-config-disable and then rebooting saves me.  

The desktop is pretty sluggish so i'd really like to get these drivers loaded.  any help would be much appreciated.  

Thanks a bunch,

-ben

---

### Post by Xian on 2005-10-30
Since you didn't mention it, I'll ask. Have you read & followed the forum How-To on [installing nVidia](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia) drivers in Ubuntu/Kubuntu?

---

### Post by ionophore on 2005-10-30
Yeah, i've been through all of that.  I notice that i have a file in my home directory called .xsession-errors, but after clearing it out and trying again, no errors are written.  Is there some place where x will write any errors it encounters.  I mean, clearly it's having some sort of error...

The screen just goes blank and i get a "no signal" on my monitor.  I can't even ctrl+alt+delete to reboot or switch to another terminal.

-ben

---

### Post by tseliot on 2005-10-30
Try method 2 in my guide (the manual installation)

---

### Post by ionophore on 2005-10-30
Hey tseliot - i just went through your procedure and i get a similar situation, although this time it dosen't lock up so much.  Instead of the completely blank screen that i was previously getting, i get a completely blank screen with a little blinking cursor in the upper right hand corner, and the computer isn't locked up - i can switch to another terminal, go back to driver "nv" and then restart x and be ok.  

Any other ideas?

-ben

---

### Post by ionophore on 2005-10-31
Ok, i've been messing around with it a little more and i see some errors in the kdm.log file that may be indicating the cause of the problem. Here is a portion of that file: >  Error: API mismatch: the NVIDIA kernel module is version 1.0.7667, but this X module is version 1.0.7676. Please be sure that your kernel module and all NVIDIA driver files have the same driver version. (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure (EE) NVIDIA(0): that there is a supported NVIDIA GPU in this system, and (EE) NVIDIA(0): that the NVIDIA device files have been created properly. (EE) NVIDIA(0): Please consult the NVIDIA README for details. (EE) NVIDIA(0): *** Aborting *** (EE) Screen(s) found, but none have a usable configuration. Fatal server error: no screens found 

So it looks as if i need an updated kernel module?  where might i find that?

---

### Post by ionophore on 2005-11-01
Ok so here's a bit of an update after screwing with it a bit.  I loaded a previous version of the drivers (7667) from the nvidia website (manually, as in the forum guide) and got it all to work.  Then, foolishly, i did a system update and... it broke! (in the same manner as before: hard lockup with a blank screen on starting X).  So i tried loading the more modern version of the drivers (7676) and i got the same error message in the logs as i described in my previous post.  

So i reloaded the old drivers (7667) and it still didn't work, this time with no error messages.  I shut it off for the night, came home today, and reloaded 7667 - just to see - and ta da - it works.  

So what the heck is going on?  It seems to me that this whole escapade was unnecessary.  I should be able to get the drivers all nice and working by using the distro system update tools.  Maybe i should file a bug report or something?

(PS:  i realize that i am to some extent talking to myself in these posts, as judging by the amount of replies i'm getting, but i figure if i may be able to help someone else in the future my efforts are worth it).  

-ben

---

### Post by kennywest on 2005-11-02
Aha, you have the same problem I was having (read my blog october 8, 2005 on [http://kennywest.blogspot.com/)](http://kennywest.blogspot.com/)). You have to uninstall/purge all ubuntu NVidia stuff (yes, all of it). Then rerun the NVidia script which will compile your drivers and install them. Do this after booting into rescue mode (which is runlevel 1).

---

### Post by reid on 2005-11-02
[QUOTE=ionophore]Ok, i've been messing around with it a little more and i see some errors in the kdm.log file that may be indicating the cause of the problem. Here is a portion of that file:
```
Error: API mismatch: the NVIDIA kernel module is version 1.0.7667, but this X module is version 1.0.7676. Please be sure that your kernel module and all NVIDIA driver files have the same driver version. (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure (EE) NVIDIA(0): that there is a supported NVIDIA GPU in this system, and (EE) NVIDIA(0): that the NVIDIA device files have been created properly. (EE) NVIDIA(0): Please consult the NVIDIA README for details. (EE) NVIDIA(0): *** Aborting *** (EE) Screen(s) found, but none have a usable configuration. Fatal server error: no screens found
```

So it looks as if i need an updated kernel module?  where might i find that?[/QUOTE]


Same problem here, does anyone have a solution?  I went through in aptitude and removed every package that had 'nvidia' in the name, and also all of the restricted modules as well, cleared my apt cache, then marked 'nvidia-glx' and installed it and all of it's dependencies, edited /etc/X/xorg.conf to use the nvidia module.  That results in my machine freezing when I boot into gdm.

I am using breezy and the 2.6.12-9-k7 kernel, if that helps.

TIA

---

### Post by tseliot on 2005-11-02
Sorry if I didn't answer before. Please DON'T use driver 7676, try 7667 (follow EVERY STEP of method 2 in my guide).

P.S. if you have any questions about the drivers, please post them in the thread of my guide.

---

### Post by kennywest on 2005-11-03
[QUOTE=reid]Same problem here, does anyone have a solution?  I went through in aptitude and removed every package that had 'nvidia' in the name, and also all of the restricted modules as well, cleared my apt cache, then marked 'nvidia-glx' and installed it and all of it's dependencies, edited /etc/X/xorg.conf to use the nvidia module.  That results in my machine freezing when I boot into gdm.

I am using breezy and the 2.6.12-9-k7 kernel, if that helps.

TIA[/QUOTE]

Did you do a purge as well? The problem is that when you remove the package, the nvidia startup script remains in init.d, which is causing all the problems. So you need to either purge the package or remove the script from the init.d directory. After that, reinstall the nvidia driver from the nvidia site. 7676 is working fine for me.

---

### Post by tseliot on 2005-11-03
[QUOTE=kennywest]Did you do a purge as well? The problem is that when you remove the package, the nvidia startup script remains in init.d, which is causing all the problems. So you need to either purge the package or remove the script from the init.d directory. After that, reinstall the nvidia driver from the nvidia site. 7676 is working fine for me.[/QUOTE]
This means you have to type:

sudo rm /etc/init.d/nvidia-*

P.S. For any questions about the drivers you can post in the thread of my guide (look at my signature)

---

### Post by kennywest on 2005-11-03
Right, sorry for that. I read some other stuff about this nvidia script thing before reading your guide.

---

### Post by ionophore on 2005-11-03
reid - 

If you follow the forum guide (linked in oe of the posts above) you will be able to get it working.  I guess the solution is twofold:

1)  Do not use the ubuntu-supplied drivers (ie, from apt), because it won't work
2)  Use an older version of the nvidia drivers (7667) that you can download from the nvidia site

Why is it that way?  I couldn't tell you.  But, hey, works for me.  

-ben

---

### Post by ezphilosophy on 2005-11-22
I have the same problem.  I had the same problem in Hoary, and have the same problem now in Breezy.  It SEEMS that my video card is working fine (Gforce2Go 16 MB).  However, anytime I want to restart, shutdown, alt+ctrl+back, etc., I get a blank screen.  Don't know what to do.
Now, I read what kennywest is saying about "merge", but as a relative newbie, I'm not really sure what that all means.  It's pretty annoying having to manually shutdown my computer by pressing the button and it would be great to have a fix.
Hope someone can help.
Oh, and I did tseliot's method 2 and that seemed to install fine (it recognizes the video card and works) but still gets the blank screen after try to reboot.

---

### Post by Kannisto on 2005-11-22
[QUOTE=ionophore]reid - 

1)  Do not use the ubuntu-supplied drivers (ie, from apt), because it won't work
2)  Use an older version of the nvidia drivers (7667) that you can download from the nvidia site

-ben[/QUOTE]
Actually you can use the ubuntu repos if you change in /etc/apt/sources.list
"breezy universe main restricted multiverse" to "hoary universe main restricted
multiverse" uninstall your current driver and install the older from the hoary repositories. Then lock the package and change hoary back to breezy in sources.list. Worked fine for me.

---

### Post by reid on 2005-12-04
Hi,

Just a post for closure on my part.  I thought I had posted my solution, but I guess not.  I was using the driver from the repos (7667) and it was not working.  What ended up fixing it for me was to have this line in my xorg.conf:
 Option "NvAGP" "1"
That is in the Device section for the card.  It was set to 2.

Thanks for the help everyone.

---

