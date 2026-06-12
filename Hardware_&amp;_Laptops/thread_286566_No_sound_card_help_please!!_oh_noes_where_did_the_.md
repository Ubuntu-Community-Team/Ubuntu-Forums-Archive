---
title: "No sound card?? help please!?! oh noes where did the sound go..."
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by honeydew on 2006-10-27
recently I undertook a project to make the systems in my bedroom completly silent, I took to my closet and dug up a ton of old hardware.. I ended up choosing and using a compaq 1830(it is 430mhz and has 62mb of ram)  I know what your thinking.. why the hell would anyone try and plug a paperweight into the wall, it just cant do anygood and will most likely hurt loved ones, I know I know.. but be surprised if you may..(I am running most programs with ssh -X, from my dual amd 1900+ server) I am running xubuntu desktop and while opening top I am only using 50mb of ram (w00t! I win) so the only problem with this now.. is.. it is sooo very silent I want to make some noise come out of it.... but the problem lies in this.. there is no noise, alsa and oss say that they cant find a driver.. what do I do? what rocks can I look under? should I upgrade to edgy(yes,yes I installed a day before it came out, though I dont know if that should matter..) well if know anything about my ailments please send me some love.. help me out.. please.

- love and light

---

### Post by kvonb on 2006-10-28
Open a terminal and type the following:

```
lspci | grep audio
```

This will at least tell you if your sound card is detected, and tell you what type it is.

If there is no response from that command then it is either a driver issue or the onboard sound is disabled in BIOS.

Regards,  Kev :)

---

### Post by honeydew on 2006-10-28
thanks kev for the quick responce, though I am getting lifted spirits allready as I feel we can eliminate both of thoose possiblities..   When I posted the command I recieved:

```

~$ lspci | grep audio
0000:00:11.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)

```

any other thoughts?

---

### Post by tommcd on 2006-10-28
Here is a comprehensive sound problems troubleshooting guide:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

Work your way through that. You should at least be able to diagnose the problem this way.

---

### Post by kvonb on 2006-10-28
Sorry for the slower reply, I've been busy.

Try going through the instructions on the link that tommcd supplied below, it looks like a pretty good guide.

I'm wondering if it just a simple mixer problem, I don't know which mixer app that Xubuntu uses but in Gnome you sometimes have to switch the device that the mixer is looking at from the mixers menu.

Let us all know if you got it working.

Regards,  Kev :)

---

### Post by honeydew on 2006-10-28
aye, no luck.. I went to the alsa site, and alot of ess cards are supported cept no support for mine, I tried using a similar driver like es1968 but didnt seem to have any luck.  I may save up a few bucks and go get a usb adapter over the weekend, alsa says that they support them all.


~thanks yas for the insight.

---

### Post by kvonb on 2006-10-28
Sorry to hear that :(

Oh well, can't win them all I expect.

---

