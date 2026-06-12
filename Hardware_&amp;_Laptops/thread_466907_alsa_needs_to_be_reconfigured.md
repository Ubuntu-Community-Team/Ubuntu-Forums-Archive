---
title: "alsa needs to be reconfigured"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by ronbrooks on 2007-06-07
Some how my alsa file got messed up and I need to reconfigure it for my system. 

Could someone help in how to do this from the command line. 

I don't know how but it is now configured for a sound card I don't have.  The card I have is an VIA8237

Could someone help please.

---

### Post by tturrisi on 2007-06-07
open a terminal & type:
alsaconf
press return key

---

### Post by ronbrooks on 2007-06-07
I tried that command and it didn't work.

---

### Post by reckless2k2 on 2007-06-07
when you typed it, did it produce output? did anything happen after you typed it? just looking for any output.

---

### Post by ronbrooks on 2007-06-07
This is what I got after I typed it in.

bash: alsaconf: command not found

---

### Post by reckless2k2 on 2007-06-07
go into synaptic and search "alsa". sounds like you might not have the package installed. i think the package you are looking for is "alsa" and or "alsa-utils"

---

### Post by ronbrooks on 2007-06-07
I just checked synaptic and it show that they are both loaded in the system

---

### Post by tturrisi on 2007-06-07
sudo alsaconf

---

### Post by ronbrooks on 2007-06-07
This is what I get when I try to test the sounds for sound caputer and when I try.  When I got to sounds and try and play the login sound I get nothing at all.

---

### Post by Ub1476 on 2007-06-07
I have the same error too, kinda.. Need to reinstall alsa at least too.

---

### Post by ronbrooks on 2007-06-07
ronbrooks@ronbrooks-desktop:~$ sudo alsaconf
Password:
sudo: alsaconf: command not found

is not working either the above message is what I get when I use that comand.

---

### Post by ronbrooks on 2007-06-08
Has anyone got any idea on this.  My next thing I guess will be to reinstall the OS and see if that will fix it.  I don't realy want to because I am on dial up and it takes forever to down load all the programs and get the updates.

If anyone can help that would be great.

---

### Post by reckless2k2 on 2007-06-08
did you reinstall alsa as suggested before a fresh install?

---

### Post by ronbrooks on 2007-06-08
No I have not but I will do it now and see what happens.  I will get back to you after I try it and let you know what happened.

---

### Post by ronbrooks on 2007-06-08
I just went to synaptic and reinstalled the Alsa and Alsa utility, and Alsa Libsound2.  I then rebooted the system and nothing has changed.

---

