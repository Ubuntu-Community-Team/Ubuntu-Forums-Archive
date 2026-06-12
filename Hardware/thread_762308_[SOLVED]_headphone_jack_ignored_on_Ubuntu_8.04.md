---
title: "[SOLVED] headphone jack ignored on Ubuntu 8.04"
date: 2008-04-22
forum: Hardware
---

### Post by tcheard on 2008-04-22
I'm a semi-new user of Ubuntu. Yesterday I did the upgrade from Ubuntu 7.10 to Ubuntu 8.04 on my Sony VAIO VGN-FZ17G. Anyway, when I was on Ubuntu 7.10 my headphone jack was ignored and audio was just played out of the laptop speakers, even when there was speakers plugged into the headphone jack. I did some research and fixed it with this: [http://ubuntuforums.org/showthread.php?t=637799](http://ubuntuforums.org/showthread.php?t=637799) with Fabiotc's post

Then I did the upgrade yesterday and they didn't work anymore. So I tried the same fix, but it didn't work.

Can anybody help? It would be much appreciated.

Thanks,
Tom

---

### Post by goodywitch on 2008-04-26
I have the same problem (why didn't I find your post before?).

---

### Post by oooh on 2008-04-26
same problem here:

Solved it in 7.10 with the link detailed by tcheard above.

Now with Hardy Heron it does not work anymore.

I will try the same fix anyway and let u all know. 

On the meanwhile, we can all try this, it worked for these people: [http://ubuntuforums.org/showthread.php?t=637799&page=2](http://ubuntuforums.org/showthread.php?t=637799&page=2)

---

### Post by oooh on 2008-04-26
Solved ! 

See: [http://ubuntuforums.org/showthread.php?t=637799&page=2](http://ubuntuforums.org/showthread.php?t=637799&page=2)

---

### Post by goodywitch on 2008-04-26
how do you alter the alsa-base file?  When I try to save changes, it says I'm not allowed to do so?  (um, ultra-newb?)

---

### Post by +Synyster on 2008-04-26
> **goodywitch said:**
> how do you alter the alsa-base file?  When I try to save changes, it says I'm not allowed to do so?  (um, ultra-newb?)

type the following command in the terminal
```
gksudo gedit etc/modprobe.d/alsa-base
```

you should be able to edit it then

---

### Post by goodywitch on 2008-04-26
I'm going to come out of this thing feeling like a dunce.  Does the order (opening the alsa-base file vs using the terminal first) matter?  Because I still get:

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

After I edit the file, which I did after typing what you said into the terminal.  

I'm confused by the permissions.  I'm username@username in the terminal, and I"m the only user on this computer.  It won't let me log on as root (I can see why).  When I change to root in terminal, it goes away if I close it, and it doesn't seem to raise what I can do outside the terminal.  The fix is so simple too, if I can manage to save it.

Thanks in advance for the patience to explain this to me :-)
(I should post in the beginner's section, but it started out as relevant to this conversation, and got sidetracked. :-/ )

---

### Post by krantix on 2008-04-26
same problem here with toshiba p100 and hda-intel conexant venice... 

adding the line to alsa-base does not work :-(

---

### Post by oooh on 2008-05-01
Have you tried to do EXACTLY this in your terminal?:

sudo gedit etc/modprobe.d/alsa-base

It should ask you for a password, and once the password is accepted then open the gedit in SU mode.  Then you will be able to exit the gedit saving the file WITHOUT nay trouble.

---

### Post by tcheard on 2008-06-18
Thank you very much. The edit of the alsa base worked for me. That has made my day! Its been bugging me for ages! Thanks

---

