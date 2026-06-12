---
title: "Crashing :("
date: 2008-08-16
forum: General Help
---

### Post by codeking on 2008-08-16
Ubuntu has been crashing an amazing amount.  Usually a few times per day.

Is this normal for Ubuntu?  If not, how can I find out whats causing it?

---

### Post by lukjad on 2008-08-16
No, it is not normal that this happens. What are you doing when it crashes? Are they high demand activities like gaming or just simple text editing or web surfing?

---

### Post by alzie on 2008-08-16
Crashing is not normal for Ubuntu.

Keep track of what programs you are using when it does crash.  Something is triggering this.

When you've narrowed it down, post again (after looking for a solution ;) ).  It would be helpful when you do to include your computer specs too.

---

### Post by tfosorcim on 2008-08-16
Crashing may be caused by any number of things. Have you run the memory test from the boot menu or tested the hard drive?

---

### Post by codeking on 2008-08-16
My computer is has 2GB of RAM and a Pentium IV processor with no swap partition.  I'm not doing much, most of the time just Aptana, XAMPP, Firefox, Evolution, Skype, and Pidgin.  My system should easily be able to handle it.

It seems it crashes when using Aptana and Firefox, but I use those a lot, so I'm not sure thats the cause.  

And by crashing I mean by the screen freezing up and not being able to do anything.  Whenever I'm playing music, the music stops a few seconds after the screen freezes.  Windows XP is perfectly stable.  Sorry if I wasn't clearer bout that before. 

I looked in /var/log/syslog, (a google search turned that up) found the place of the crash and didn't see anything besides some network problems, but that was a minute or so beforehand.

---

### Post by codeking on 2008-08-16
Just had a crash.   It was only partial, I could still move the mouse around still worked, but everything else was frozen.  Cntrl + ALT + Backspace did nothing.  I was running skype, pidgin, rhythmbox, and the movie player.  I've removed skype from the startup services, see if that fixes the crashing.

---

### Post by Sinkingships7 on 2008-08-16
My main concern is your lack of a swap partition. I believe that's necessary...

---

### Post by codeking on 2008-08-17
> **Sinkingships7 said:**
> My main concern is your lack of a swap partition. I believe that's necessary...

You sure about that?  I always thought it was a place to dump a portion of the RAM when you used too much, and I never do.

---

### Post by ender1598 on 2008-08-17
> **codeking said:**
> My computer is has 2GB of RAM and a Pentium IV processor with no swap partition.  I'm not doing much, most of the time just Aptana, XAMPP, Firefox, Evolution, Skype, and Pidgin.  My system should easily be able to handle it.

It seems it crashes when using Aptana and Firefox, but I use those a lot, so I'm not sure thats the cause.  

And by crashing I mean by the screen freezing up and not being able to do anything.  Whenever I'm playing music, the music stops a few seconds after the screen freezes.  Windows XP is perfectly stable.  Sorry if I wasn't clearer bout that before. 

I looked in /var/log/syslog, (a google search turned that up) found the place of the crash and didn't see anything besides some network problems, but that was a minute or so beforehand.
I've got a very similar problem!!  At first it seemed to only happen when I was playing 3D games so I thought my video card was dying.  I bought a new one and the problem persisted.  I then tried swapping in a new power supply and it still crashed.  It's now happening when I just browse web pages or any other low intensity tasks.  It's very random and I can play a game for hours and not have issues and then later on in the night it'll crash every 15 minutes.  I also ran a CPU stress test for a few hours and nothing crashed so I'm fairly certain it's not the processor.

My specs: P4 3.0 Ghz, 2 gig of ram, 500 GB SATA drive, Geforce 7600GT, Ubuntu 8.04.  I did try installing XP on another drive and doing some 3D stuff but after 4 hours or so nothing happened.  This doesn't mean it's not a hardware issue though... I've gone longer in Ubuntu without trouble too.  Overall this is a pretty frustrating problem to troubleshoot.

---

### Post by Sinkingships7 on 2008-08-17
> **ender1598 said:**
> I've got a very similar problem!!  At first it seemed to only happen when I was playing 3D games so I thought my video card was dying.  I bought a new one and the problem persisted.  I then tried swapping in a new power supply and it still crashed.  It's now happening when I just browse web pages or any other low intensity tasks.  It's very random and I can play a game for hours and not have issues and then later on in the night it'll crash every 15 minutes.  I also ran a CPU stress test for a few hours and nothing crashed so I'm fairly certain it's not the processor.



Odd. I have that exact problem with XP.

---

### Post by ender1598 on 2008-08-17
I just ran the memory test from the boot menu for about 5 hours and there were no errors that popped up.  I was almost hoping something significat would show up so at least this mystery would be solved......

---

### Post by Sinkingships7 on 2008-08-17
> **ender1598 said:**
> I just ran the memory test from the boot menu for about 5 hours and there were no errors that popped up.  I was almost hoping something significat would show up so at least this mystery would be solved......

Do you know what motherboard you have? Did you build the computer yourself?

---

### Post by ender1598 on 2008-08-17
It's the motherboard from a Shuttle barebones kit I put together around 4 years ago.  The model is SB75G2...  it's one of their own boards and here's the link to their info page.  [http://eu.shuttle.com/archive/en/fb75.htm#mainboardfb7](http://eu.shuttle.com/archive/en/fb75.htm#mainboardfb7)

---

