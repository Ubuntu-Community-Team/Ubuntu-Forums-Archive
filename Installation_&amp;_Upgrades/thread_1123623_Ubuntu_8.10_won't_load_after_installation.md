---
title: "Ubuntu 8.10 won't load after installation"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by tysonxg on 2009-04-12
I am brand new to Ubuntu and Linux and need help.  After I went through the whole installation process everything seemed to be working fine, and when i rebooted after installation was complete it takes me to the login screen as it should.  But, after I enter my user name and password it goes to either a orange/tanish screen  or a black with my cursor on it.  I have full control of the cursor and thats about it.  I have no idea whats wrong, I have tried to install from 2 different disks each burnt at low speeds from the ISO file.  If i check to see if the disk has any errors it tells me there are no errors.  So please help...Thanks

---

### Post by Bucky Ball on 2009-04-12
Does it run from the 'Live' version okay? Boot from the disk and select the option 'Try Ubunut' or whatever that is, rather than install. Also, you could try booting into the recovery kernel, if you are making it to the grub screen that is.

If not running for the live cd you have a hardware problem probably but that will give you somewhere to start looking for a fix at least.

---

### Post by tysonxg on 2009-04-12
The 'Try Ubuntu' option did not work and gave me the same results.  I did boot it into the recovery mode, and am on a screen called 'Recovery Menu' and i dunno what to do from here.

---

### Post by Bucky Ball on 2009-04-12
Okay, well if the 'Try Ubuntu' option didn't work, I suspect there is a conflict between the Gnome environment and your monitor (ie: is setting the wrong resolution or not finding the monitor). 

Boot again normally, when it crashes, hit ctl/alt/f1. That should get you to a console. Type 'dmesg' (no quotes) and that should give some indication of what caused the crash. Post what you can here. I know that is hard because no copy and paste but it should be the very last message.

* incidentally, it sounds like everything is installed okay and happening, so well done there, you just can't for the moment see it!

---

### Post by connorh123 on 2009-04-12
Did you restart your computer?
If not try that.
If not, wait. My Ubuntu loading screen took a while than it usually did. But it's working fine now.

---

### Post by Bucky Ball on 2009-04-12
Also, from recovery menu, you can choose root console and type:

```
startx

```
What error does that generate?

---

### Post by tysonxg on 2009-04-12
Ok so the console came up, but it won't let me type anything...
This is what it says:
[IMG]http://img254.imageshack.us/img254/3616/ubuntu.jpg[/IMG]
kinda blury took it from my phone sorry...

*Edit*

From the root i typed in 'startx' and it gave me a bunch of crazy blue lines...

---

### Post by mrq201 on 2009-04-12
just saying I have the same problem and will be following along also.. hope this is not illegal for doing this.  I do have a question... how do u get to the recovery mode?

---

### Post by tysonxg on 2009-04-12
For me, when I first boot it has the option to press esc and then I just chose recovery mode

---

### Post by mrq201 on 2009-04-12
i typed the startx after i pressed the ctrl/atl/f1 and i got 

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/ .X0-LOCK and      start again

---

### Post by tysonxg on 2009-04-12
I installed the beta and everything is working for me (typing this from inside Ubuntu;) ) so thanks for the help

---

### Post by Bucky Ball on 2009-04-13
Glad to hear it and a pleasure. Welcome to the forums and Linux.

---

### Post by theozzlives on 2009-04-13
Looks like what one of my systems did, I had to install 8.04, then upgrade to 8.10. Still haven't figured how to get 9.04 working on it.

---

### Post by mrq201 on 2009-04-13
So does anyone think I should install 8.04 then upgrade to 8.10? or should i just install the beta version??

---

