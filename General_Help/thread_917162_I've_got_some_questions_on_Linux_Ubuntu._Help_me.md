---
title: "I've got some questions on Linux Ubuntu. Help me?"
date: 2008-09-11
forum: General Help
---

### Post by ieBrazil on 2008-09-11
I'm pretty new on this OS.

You see, I just received the Ubuntu free (live) CD 7.10. I'm using it right now as Live. It's pretty cool!

But there're some doubts

- why there's no sound?
- is it false impression, or my graphic resolutions are lower, even though my laptop supported the Extra option on Desktop visual effects? (I always used XP Professional and the characters looked better than now.)
- are Ubuntu and XP Pro equals with regards to internet.. viruses?

Please, try not to use techy terms. I'm lay, you know.

Tnx in advance to you all! And UBUNTU: humanity to others.




ieBrazil

---

### Post by jblackthorne on 2008-09-11
Welcome to the wonderful world of Ubuntu!  It is a fantastic operating system that is stable, reliable, and easy to use once it is up and running.  Most hardware works flawlessly right after installation.  However, with all the different hardware manufacturers and standards, sometimes off-brand hardware is a little trickier to get setup.  The good news is that nearly all sound cards work fine on Ubuntu once installed.

What brand and model of machine are you running?

Please execute the following commands and post the results to this thread.  This will tell us more details about your hardware and hopefully why you don't have sound.
(to execute these commands, start a terminal by, "Applications menu/Accessories/Terminal)

* uname -a
* sudo aplay -l
* cat /proc/asound/cards
* sudo lshw

Once you provide the requestd info, that will hopefully give us enough info to help fix the sound. :)

Edited to add: I forgot to mention that graphic drivers show up is lower resolution by default as well.  Once installed ,you have a number of options, including installing manufacturer binary drivers if you wish.  (Be default, Ubuntu cannot include manufacturer binary drivers, such as Nvidia drivers, due to licensing.  However, they can be easily activated after installation).

---

### Post by kokkus on 2008-09-11
Do not type the commands in 1 paste.
And when it comes to the graphic. You'll have to enable the graphic driver manually when you have installed ubuntu (security reasons).
(System > administrator > hardware drivers)

---

### Post by unca.paka on 2008-09-11
Also, he's running from the Live CD, hasnt installed Ubuntu yet(from my understanding). In my case, sound didnt work from the Live CD, nor did it load my graphics drivers, just used the old vesa, which I think is the case for all newer(2004+) graphics cards.

Also, to answer the internet question, there are no viruses for linux. Whats the point when it has what, < 2% of the market share...Occasional rootkits, but as a normal user(no servers running, etc) you shouldnt be concerned.

---

### Post by kokkus on 2008-09-11
> **unca.paka said:**
> Also, he's running from the Live CD, hasnt installed Ubuntu yet(from my understanding).
I know, but I told him this so he won't be alarmed, and believing that it doesn't work.

---

### Post by unca.paka on 2008-09-11
Right right, I was reffering to the 2nd post there.

---

### Post by ieBrazil on 2008-09-12
> **jblackthorne said:**
> Welcome to the wonderful world of Ubuntu!  It is a fantastic operating system that is stable, reliable, and easy to use once it is up and running.  Most hardware works flawlessly right after installation.  However, with all the different hardware manufacturers and standards, sometimes off-brand hardware is a little trickier to get setup.  The good news is that nearly all sound cards work fine on Ubuntu once installed.

What brand and model of machine are you running?

Please execute the following commands and post the results to this thread.  This will tell us more details about your hardware and hopefully why you don't have sound.
(to execute these commands, start a terminal by, "Applications menu/Accessories/Terminal)

* uname -a
* sudo aplay -l
* cat /proc/asound/cards
* sudo lshw

Once you provide the requestd info, that will hopefully give us enough info to help fix the sound. :)

Edited to add: I forgot to mention that graphic drivers show up is lower resolution by default as well.  Once installed ,you have a number of options, including installing manufacturer binary drivers if you wish.  (Be default, Ubuntu cannot include manufacturer binary drivers, such as Nvidia drivers, due to licensing.  However, they can be easily activated after installation).



Hi.

You see, Im not using live CD now, but I can get it, if needed later.

My machine is:

Acer (I'm ashamed! I'd like to have a Macbook!) TravelMate 2480, Intel Celeron M Processor 420, 1.6 MHz, 533 MHz, 1MB L2 cache, 512 MB DDR2, 802 11b/g wireless...

I think this is it.

Tnx in advance. 




ieBrazil

---

