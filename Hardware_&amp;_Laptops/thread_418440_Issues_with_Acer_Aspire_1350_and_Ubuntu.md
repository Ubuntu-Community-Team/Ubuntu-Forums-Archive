---
title: "Issues with Acer Aspire 1350 and Ubuntu?"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by bmalone on 2007-04-22
Thought I would open my posting account with this small bit of strange information.

I am new to Ubuntu but not linux.  I had installed and successfully used Ubuntu on my old desktop.   It was a good experience all around, I was impressed.   I needed a portable Ubuntu environment for work and decided to use my Acer 1350.  I had installed many linux distros on it.  Mostly with no problems.

I made a cup of tea and sat down to install U6.10 from a cd.  All appeared to be going ok.  Until it stopped, Copying Files - 53%, and it sat there staring back at me.  I tried a few more times and got the same result.  For no particularly good reason I unplugged the battery from the Acer and tried again.  It worked.  Installed and working ok.

Today I decided to upgrade to 7.04 on the Acer as the desktop had been updated several days previously with no probs.  The Acer didn't enjoy the experience.   Can't access tty, job control turned off, from BusyBox.  Can't be bothered messing around with the machine as there is nothing on it anyway.  I have just tried re-installing from the cd, Copying Files - 59%, and another freeze.  Then I remembered I had the network cable plugged in. So unplug and go again. 

Does anyone know of any major install issues with the Acer 1350?  It seems a little erratic to me, perhaps my Acer is having a mid-life crisis?

---

### Post by britrb on 2007-10-09
Mid life? They arent that young!!

I have an Acer Aspire 1353 and I'm interested in any and all replies to this thread, as I would like to do the same. I am currently DLing an image of Feisty Fawn (strange name!), I'll give it a go and see if there are any issues. The one thing that I know is an issue is the NetGear MA111 v1 wireless adaptor. I'll blow up that bridge when (and if) I come to it!!

Good Luck bmalone,
Brian.

---

### Post by britrb on 2007-10-10
I am currently trying the instal now. Its going really slow though.

---

### Post by britrb on 2007-10-10
I am loading Ubuntu onto the lappy now, but it has sat there for over an hour with a black screen for over an hour. I'd upgrade your RAM atleast mate.

---

### Post by britrb on 2007-10-10
Ok i am haveing error messages about missing error messgaes... I dont think ubuntu will go on. It does load (somewhat) in safe mode, but due to multiple errors and the touchpad not working you cannot install the OS.

---

### Post by britrb on 2007-10-11
If anyone is watching this...

Error message:
__________________________________________________________________________

"There was an error starting the GNOME Settings Deamon.
Some things, such as themes, sounds, or backround settings may not work correctly.

The last error message was:

Did not recieve a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME wil try to restart the Settings Deamon next time you log in."
__________________________________________________________________________

Is this just the system specs of my laptop?

RAM 256mb
CPU AMD Athlon XP-M 2400+
HDD 20gb 5200rpm

Or is there another cause?

---

### Post by little_wam on 2007-12-13
I installed Ubuntu on my Acer Aspire 1350 and I didn't encoutered any difficulty or problem.
The only thing was that. in 7.0.4, my wifi card was not launched automatically but it looks like it is OK for 7.0.10.

By the way, does someone know how to increase the resolution of my screen (actually 1024x768)? 

Windows are really big, and surfing with this laaaaarge view is annoying. (graphic card ATI mobility Radeon 9200, I use the default (though free?) driver.)

---

### Post by britrb on 2007-12-13
I think thats the max resolution for the aspire 1350 series' monitors.

---

### Post by little_wam on 2007-12-14
Just the same day as I post, I experiment some annoying freezings on my Ubuntu 7.0.10.

It may be caused by a program (Azureus, Gmail notifyer, Pidgin.... Firefox??) but it makes the computer totally freeze.
Is there a way to kill some processes? no way, apparently.
So, it happened 4 times yesterday in about... 1 hour! If it really happens again or if I don't find the buggy program, I'll have to start thinking of a new distrib'... OpenSuSE? Fedora? Or simply windows...

---

### Post by little_wam on 2007-12-15
Now I'm stuck with 640x480 resolution... do you know which driver is best to use (and in fact, used by default) with a mobility radeon 9200 ?

thx

---

### Post by little_wam on 2007-12-20
Well well, i tried to set up openSuSE since I faced some inconveniences with Ubuntu. This distrib is a lot worse, at least for my laptop (screen/package setup/no wifi card detected). I will then return to ubuntu 7.0.10 and, overall, to my good old windows XP home edition.

---

### Post by rjmoerland on 2008-03-06
I couldn't get Ubuntu 7.10 to boot on an Apire 1352XC either, during boot the splash screen showed all kinds of zig-zags. After a while, the screen became sometimes fully black and sometimes fully white. 

Then, as I realized that it was already a bit older hardware, i tried Xubuntu 7.10, but had the same issues. Fail safe mode did work, but I found the VESA mode too slow. I started experimenting with the boot parameters (adding vga=xxx etc), and I found that when I just removed the 'splash' option, Xubuntu happily booted without a problem and I got it to install. After the install, the kernel got updated and now everything runs smoothly (but I don't know if that's related :)). Perhaps this bit of info can help anyone.

---

### Post by banoncom on 2008-04-11
I just installed 7.10 on my Aspire 1350

First i tried with a CD but would only get as far as booting and starting the install. Turns out the liteon DVD-RW is having problems reading CD's

I then downloaded the DVD and no probs - installed ok.

Just wondering if any of you with the 1350 have got the Fn+F5 hot key working to toggle displays?

I have posted a new post with the problem titled: Display Function Key on Acer Aspire 1350 

Cheers.

---

### Post by rjmoerland on 2008-04-13
BTW, I needed to add the following to the xorg.conf file (in /etc/X11/) to get DVD playback without artifacts.

 Section "Module"
    Disable "glx"
    Disable "xtrap"
    Disable "record"
    Disable "GLcore"
    Disable "dri"
EndSection

---

