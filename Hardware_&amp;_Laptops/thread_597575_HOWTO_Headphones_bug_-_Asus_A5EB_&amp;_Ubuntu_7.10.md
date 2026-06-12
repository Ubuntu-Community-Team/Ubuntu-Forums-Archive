---
title: "HOWTO: Headphones bug - Asus A5EB &amp; Ubuntu 7.10 - Intel HDA ICH6 (ALC880) sound card"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by PauloSTP on 2007-10-30
Hi,

I've been a ubuntu and kubuntu user for over an year and have given nothing but praise.

But recently I've bought a new laptop, an Asus A5EB, and have stumbled upon a few hardware problems - the webcam, the tv tuner and, until today, the sound card.

This tutorial is intended to help people using Ubuntu 7.10 Gutsy Gibbon on this Asus laptop or any other with the same on-board sound card - 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (ALC880).

For some reason the Alsa Driver won't give you a way to control the headphone output in the Alsa Mixer, so here's the workaround built from bits of information gathered from these forums.

**_Step 1:_** Open up the Terminal (Applications > Accessories > Terminal)

_**Step 2:**_ Paste the following line:
> sudo gedit /etc/modprobe.d/alsa-base
and input your password

**_Step 3:_** When the text editor opens, paste this new line at the bottom of the file:
> options snd-hda-intel model=z71v position_fix=1

_**Step 4:**_ Save the file and close the editor. You can also close the terminal now and restart your computer.

_**Step 5:**_ After restarting you can check on the Alsa Mixer (double click on the loudspeaker on the menubar) that now there's a Headphone fader. Just click the small loudspeaker beneath it and raise the fader.

You can now listen to sound with your headphones, but some small problems come up. The *Fn* shortcut keys for mute, volume up and down on your keyboard don't work and also the loudspeaker icon on the menubar won't control the volume. So:

_**Step 6:**_ Right click on that loudspeaker icon and go to the preferences. Select PCM and close.

_**Step 7:**_ Go to System > Preferences > Sound and at the bottom of the window select PCM and close.

That's it! Your problem is solved. :)

I tried to make this tutorial as user friendly as possible, so any newbie can follow it. I still consider myself a newbie and sometimes the users on these forums forget they once were there.

This tutorial will also work for other ubuntu based systems like kubuntu, with just some small changes. If you need some extra help, just ask. My knowledge is very limited but i'll gladly help.

---

### Post by plesset on 2007-11-28
Thanks for your post. I had been struggling for a few days now ([http://ubuntuforums.org/showthread.php?p=3856997](http://ubuntuforums.org/showthread.php?p=3856997)), I followed your steps and whola - got the headphones to work.

---

### Post by PauloSTP on 2008-01-06
Great! I'm glad this post is useful.  :cool:

---

### Post by napsy on 2008-01-06
Glad to see it works. Sorry for off-topic but I have the same issue with my fujitsu-siemens pi-2515. Maybe there's a fix there I could use? Tnx.

---

### Post by PauloSTP on 2008-01-06
Well, if the sound card is the same it will work. So give it a try!

If your laptop uses another sound card I don't know a solution for the problem, sorry.

---

### Post by Lincolin on 2008-03-01
Thx .. nice one .. but can you pls help me with another issue ,, a have also an Asus A5eb laptop .. and i ama new user to Linux .. swithed from MS

The problem is i cant get this os to install my video drivers ..  i would be very greatfull if you can givem me a guide of some sort or send it to me by e-mail .. pls i need it .. i'm cind off disapointed in linux .. but dont lose hope .. heard alot of good things about this OS .. and id like to test it my self .. like beryl .. but with no video drivers there is no beryl :( ,, hope to get help .. 

e-mail: [email]Lincolin@mail.ru[/email]
Im using Ubuntu 7.10

---

### Post by PauloSTP on 2008-03-10
Hi!

I don't recall having any problem with the graphics card in Ubuntu... :confused: At the moment I don't have Ubuntu installed, I'm trying another distribution, but I could swear I had no problem with that. Try installing Beryl with Synaptic Package Manager, it should work.

Good luck on that, and have a little patience with Linux, it can get on your nerves at the beginning.

---

