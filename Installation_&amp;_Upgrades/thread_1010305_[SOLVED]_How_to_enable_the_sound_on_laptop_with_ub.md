---
title: "[SOLVED] How to enable the sound on laptop with ubuntu?"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by talofo on 2008-12-13
Hi all.


This is my first post, on UBUNTU OS!! :D 

I'm glad, however, I can get no sound working on my laptop.

Here:
[http://www.linlap.com/wiki/HP+EliteBook+8530P](http://www.linlap.com/wiki/HP+EliteBook+8530P)

It says:
Sound	Works	Need options snd-hda-intel model=laptop 


I have been on the terminal and I have type:
sudo vi /etc/modprobe.d/alsa-base

and at the end of the file I've added:
snd-hda-intel model=laptop


But, after that, I don't know how to save the file! :s


Any help? :s

---

### Post by talofo on 2008-12-13
And when I try to go to the same file, I'm getting this:


E325: ATTENTION
Found a swap file by the name "/etc/modprobe.d/.alsa-base.swp"
          owned by: root   dated: Sat Dec 13 21:09:40 2008
         file name: /etc/modprobe.d/alsa-base
          modified: YES
         user name: root   host name: oikram-elitebook
        process ID: 6256
While opening file "/etc/modprobe.d/alsa-base"
             dated: Mon Sep 15 05:16:36 2008

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/modprobe.d/alsa-base"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/modprobe.d/.alsa-base.sw
p"
    to avoid this message.
"/etc/modprobe.d/alsa-base" 42 lines, 2344 characters




Sorry for this newbie questions, but I'm absolutly clueless about what to do.


Hope you can help me out.
Regards,
MEM

---

### Post by impact on 2008-12-13
Use

sudo gedit /etc/modprobe.d/alsa-base

or

sudo nano /etc/modprobe.d/alsa-base

Those two editors are a lot more user friendly than vi.

---

### Post by talofo on 2008-12-13
> **impact said:**
> Use

sudo gedit /etc/modprobe.d/alsa-base

or

sudo nano /etc/modprobe.d/alsa-base

Those two editors are a lot more user friendly than vi.


Thanks. Later on maybe I will learn that other editor, but gedit seams quite well. :) thanks.

Do you know if I need to restart the ubuntu or something, after I edit that file and save it?



Thanks,
MEM

---

### Post by talofo on 2008-12-13
Anyone. Please. I have no sound. I see all other persons ho report good news on this. Maybe I'm just making something stupid that I'm not aware of.

What could it be?


Thanks,
MEM

---

### Post by talofo on 2008-12-14
I'm really stuck here. I've reconfirm the options. I have put the volume to max... my sound icon appear, all seams ok, just, NO SOUND. :( I have no mute enable on the quickbuttons. When I touch the volume buttons on my laptop they work. I just can't listen nothing.

I have running windows before, and the sound as worked, so, the hardware is capable of working.

Why can't I have no sound?? I need to test other thinks like music and skype... but with no sound, it's useless.

Please please almighty gurus, give me a clue... :S

:(
MEM

---

### Post by talofo on 2008-12-14
solution:

well, i'm newbie:


i've typed:

snd-hda-intel model=laptop 


i forgot the "options" part!!!

options snd-hda-intel model=laptop


regards,
mem

---

