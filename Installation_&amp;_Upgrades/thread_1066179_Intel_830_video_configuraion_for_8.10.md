---
title: "Intel 830 video configuraion for 8.10"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by Threnners on 2009-02-10
I am not having a very good Ubuntu week.

I have an old but reliable Dell Inspiron 1150 with onboard Intel 830 video.   It's been chirping away with 8.04 about since it was initially released.   I had to do some major reconfiguration with the video to get it to work, but after that things were fine.  Of course, I have NO CLUE now what I did to get it to run.

So the last 8.04 update that's pushed down apparently fried my kernel. I could get logged in but all I got was a locked screen that only half loaded.  None of the previous kernels worked.  

Then, like an idiot, I ran xconf from recovery mode and apparently wiped out my video configuration.

I went ahead and wiped the machine out and installed 8.10 using the alternate install cd.   Everything boots normally until the splash screen, then I get a black screen and the drums.

Removing Splash does not work.
Removing Compiz & Compiz Core does not work.
dpkg-reconfigure xserver-xorg only lets me configure the keyboard.

I do not know how to get my xconf configuration up here, but it is VERY minimal and all the settings look generic.  

I am at my wits end.  If I could just get this [profanity deleted] video driver configured, my life would be fabulous.  Please help!

---

### Post by avtolle on 2009-02-10
Your problem with the video card is addressed at [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards)
basically, you need to install in safe graphics mode, as I read it.

---

### Post by Threnners on 2009-02-11
I can't install in safe graphics mode - I can only install using the alternate CD, and when it boots up, black screen, knocking sound.  That's it.

Like I said, removing compiz doesn't work.  I still get the black screen.

---

### Post by Threnners on 2009-02-11
Well.  Isn't that something.  Dell says I have an Intel 830 chipset on this machine.

I finally break down and go back to Feisty, and it seems the driver that works for this machine is the i810.

I guess that screws me out of being able to use 8.10 then, unless someone got it to work for them.

Geek sad.

---

### Post by Kismet on 2009-03-01
Is there a bug reported for this issue, and or any further news? It is frustrating having to run an *old* ubuntu to get *accelerated* graphics. Any one else see the irony?

---

