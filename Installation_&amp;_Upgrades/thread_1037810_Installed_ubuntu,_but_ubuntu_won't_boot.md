---
title: "Installed ubuntu, but ubuntu won't boot"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by tumi2000 on 2009-01-12
I've installed ubuntu on my new laptop using 8.10 alternate cd (live cd didn't work)
So the installer told me to reboot so I did,
I started up my laptop everything was going good, GRUB came up so I selected the first option "ubuntu 8.10, kernel 2.6.27-7-generic" 
Ubuntu loaded then I got a black screen with a white _ in the top corner that blinked twice-thrice after that a white screen came up.

please help me :(

Update: now the white screen blinks for like a half a second and a black screen comes up :(
Update2: Even though I'm away for now please try to help me,

---

### Post by aeronotix on 2009-01-12
How long have you left it or did you reboot right there? 

If you rebooted try leaving it for a longer amount of time.

---

### Post by tumi2000 on 2009-01-12
I left it for like 5-10 minutes

---

### Post by aeronotix on 2009-01-12
Okay, why didn't the LiveCD work and what sort of graphics adapter are you using, for example if it's a graphics card then I'd suggest taking it out.

I'm pretty new to Linux but I'm wracking my brain to help.

---

### Post by Partyboi2 on 2009-01-12
> **tumi2000 said:**
> I left it for like 5-10 minutes
Try removing the splash screen when you boot. When you are booting and see "grub loading..." press ESC and highlight the Ubuntu kernel and press "e" to edit then highlight the line starting "kernel" and press "e" again then change splash to nosplash then press enter then "b" to boot. Hopefully this will give some more info and also post your graphics card info.

---

### Post by tumi2000 on 2009-01-12
> **Partyboi2 said:**
> Try removing the splash screen when you boot. When you are booting and see "grub loading..." press ESC and highlight the Ubuntu kernel and press "e" to edit then highlight the line starting "kernel" and press "e" again then change splash to nosplash then press enter then "b" to boot. Hopefully this will give some more info and also post your graphics card info.

512MB ATI HD3650
I did what you said some text scrolls down, and eventually it's back to the white screen :(

---

### Post by tumi2000 on 2009-01-12
> **aeronotix said:**
> Okay, why didn't the LiveCD work and what sort of graphics adapter are you using, for example if it's a graphics card then I'd suggest taking it out.

I'm pretty new to Linux but I'm wracking my brain to help.

the graphics card is in my above post
when i inserted the live cd and i selected something like try out ubuntu, then a white screen blinks for 1 sec then I have a empty black screen infront of me, the cd suddenly stops spinning and yeah thats pretty much it :(

---

### Post by Achetar on 2009-01-12
Sounds like X isn't starting properly. Boot the recovery mode one (and make sure it's set to nosplash) and use the 'Fix Graphics' (or 'Fix X Server' or something like that, I can't reboot whilst typing this). That may fix it. If *that* (ie the recovery mode kernel) won't boot. Try the linux mint LiveCD (use version 6 Felicia). That is almost the same as ubuntu but from what I've heard has more compatibility.

---

### Post by tumi2000 on 2009-01-12
> **Achetar said:**
> Sounds like X isn't starting properly. Boot the recovery mode one (and make sure it's set to nosplash) and use the 'Fix Graphics' (or 'Fix X Server' or something like that, I can't reboot whilst typing this). That may fix it. If *that* (ie the recovery mode kernel) won't boot. Try the linux mint LiveCD (use version 6 Felicia). That is almost the same as ubuntu but from what I've heard has more compatibility.

theres nothing the recovery mode commands with nosplash or splash in them, but I'm trying to boot recovery as I speak. I selected try to fix X server, then I get a bunch of options I have no time to read it cause after a few secs i get some message "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf .20090112133839" and i get the recovery menu again.

---

### Post by aeronotix on 2009-01-12
Have you tried my suggestion of removing that Graphics Card?

---

### Post by tumi2000 on 2009-01-12
No I have not well it's a new laptop and not that familiar to a laptop environment and i don't wanna screw something up

---

### Post by aeronotix on 2009-01-12
Oh, nevermind I thought you were on a desktop with a removeable GPU. 

Forget removing it then!

---

### Post by tumi2000 on 2009-01-12
Thought so :)

---

### Post by ugm6hr on 2009-01-12
When you arrive at the white / black screen, have you tried Ctrl-Alt-F1 (or Ctrl-Alt-F2)?

It should drop you at a command prompt.

---

### Post by aeronotix on 2009-01-12
Sorry but I have ran out of ideas, try another distro and post what happens then. Like the guy before me said try LinuxMINT, a few people I know have used that and prefer it to Ubuntu. From what I hear it more or less "Works out the box" as far as codecs and plugins are concerned. 

Sorry about giving you such a bad answer but I'm at a loss at what to do, wait for a guru to appear!

> **ugm6hr said:**
> When you arrive at the white / black screen, have you tried Ctrl-Alt-F1 (or Ctrl-Alt-F2)?

It should drop you at a command prompt.

YEAH, you just reminded me, try dpkg-reconfigure xserver-xorg if you get to that.

---

### Post by tumi2000 on 2009-01-12
I can't try that now, I will give you a update tomorrow and pm you if you've forgot :)

---

### Post by aeronotix on 2009-01-12
Yeah alright buddy, see you tomorrow. Yeah PM me because I don't check here everyday.

---

### Post by tumi2000 on 2009-01-12
> **aeronotix said:**
> Sorry but I have ran out of ideas, try another distro and post what happens then. Like the guy before me said try LinuxMINT, a few people I know have used that and prefer it to Ubuntu. From what I hear it more or less "Works out the box" as far as codecs and plugins are concerned.
Well im out of blank cds so ill run out to a store later and try :) linuxmint looks sofar sogood
UPDATE: but apparantly wine won't work :S

---

### Post by tumi2000 on 2009-01-14
Hey I can get to command line by using the recovery mode and click root, and also ctrl+alt+2 doesn't work, well it works for like 1 second and I get the white screen up.
also what will "dpkg-reconfigure xserver-xorg" I can do that command from root but I diddnt configure all the screens that come up

---

### Post by ugm6hr on 2009-01-14
> **tumi2000 said:**
> also what will "dpkg-reconfigure xserver-xorg" I can do that command from root but I diddnt configure all the screens that come up
It reconfigures your driver settings for keyboard / mouse / graphics card etc.

With the new X in Intrepid 8.10, I'm not sure how much effect it will have.  Perhaps someone else knows better.

There is certainly no harm in trying it out - it can't get any worse than a white screen!  Although perhaps backup the baseline xorg, just in case:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
```

---

### Post by tumi2000 on 2009-01-14
I did 
dpkg-reconfigure xserver-xorg
but at one point I get some message xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf .20090114120531
and then I can run a command (root@ubuntu:~#)

---

### Post by ugm6hr on 2009-01-14
If that did anything useful, you should be able to reboot, and it should work.  However, I am doubtful...

I am particularly intrigued by the fact that Ctrl-Alt-F1 causes the same problem.  I am not certain what to make of this, but X should not be running on the current if you do that, so it should not cause the white screen to reappear.

I wonder if this is actually a GDM issue?  Anyone else have any ideas?

---

### Post by tumi2000 on 2009-01-14
That didn't help me with anything cause it happened before i came up to configuring my graphic card, it came up when i was on the 1st steps configuring my keyboard.

---

### Post by saltywalsh on 2009-01-15
I am having the same issue and though I haven't found a solution for it the following should get you to the GUI but once you reboot, you will be stuck with the black screen again:

Do the following:

1. From the Grub boot menu slect the “recovery mode” option.

2. Select “root       Drop to root shell prompt”

Type the following at the prompt:

3. sudo apt-get remove compiz

4. sudo apt-get remove compiz-core

5. exit

6. Select “resume      Resume normal boot”

I may just have to install an older version of the software and see if it works.  I think it all has to do with compiz and maybe if I revert back to 7 of ubuntu I can get it to work.

---

