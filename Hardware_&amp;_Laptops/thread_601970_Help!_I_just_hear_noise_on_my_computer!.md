---
title: "Help! I just hear noise on my computer!"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by Unnicknamed on 2007-11-03
Suddenly I just hear noise whenever I play music, or listen to any sound from the computer.

My sound card is integrated with my motherboard, this motherboard is a ASUS M2N SLI.

I change spearkers and I still hear noise.

Help me please :(

---

### Post by Rhubarb on 2007-11-03
What sort of noise do you hear?

Is it a deep 50 or 60Hz hum you hear (like a poorly grounded mains hum).
Or is it a white noise hiss?
Or maybe you hear some high pitched noises whenever your pc is processing info (like watching a movie, moving your mouse cursor around)?

Different noises mean different things.
For a 50 or 60Hz hum you might need to make sure your PC is grounded properly, try a different power cord / plug some head phones in to see if the sound has gone away.
For white noise, you've probably got a cheap sound card, get a cheap sound card (internal or external) should help a lot.
If you hear weird high pitched noises when you PC is processing something, you might have some IRQ conflicts that can be fixed in the BIOS.

Hope this helps, if it doesn't, reply back with some info about what the sound sounds like (or maybe attach a recording of it).

Cheers,

---

### Post by Unnicknamed on 2007-11-03
Hi there thank you for your help!

For example when I listen to a MP3 it sounded distorted with a white noise instead of the music.

But now it is working again, I opened the computer and check if were not cables making contact with the motherboard. I also did this, and I hope you can explain me what did I do.

Here's some background:

There's a particular bug with my integrated sound card, the first time I install Ubuntu it detects my sound card like an USB sound card. And I can't hear anything. So I have to do this in order to hear something from the sound card:

> 
1. edit the /etc/modprobe.d/alsa-base file (as root),
2. find the line which contains snd-usb-audio.
3. comment it out, or simply delete it.
4. restart your computer


So I did the opposite, I comment the line again and restart, and then I comment it out again and restart.

And everything was to normal.

So what did happen?

What is this "fix" doing?
My motherboard is only a month used, does integrated sound cards have a short life? 
Is this a bad sign that my sound card is gonna die soon? :(
Does this kind of white noise could be for interference or cables making contact with the motherboard?

---

### Post by Rhubarb on 2007-11-04
Ok, by the sounds of it you've probably just got a software problem.

What may help is if you where to download the latest ALSA source code, compile it, and install it.
(I could be wrong, it could be a hardware fault - a BIOS upgrade might help you out here (go to the asus website and grab the BIOS image and flash tools, you may have to use freedos to install it, or maybe you've got a faulty motherboard)



Dependencies required: libncurses5-dev (libncursesw5-dev ?)

1. download and unpack latest alsa-driver, alsa-lib, alsa-util
[http://www.alsa-project.org/alsa/ftp/driver/](http://www.alsa-project.org/alsa/ftp/driver/)
[http://www.alsa-project.org/alsa/ftp/lib/](http://www.alsa-project.org/alsa/ftp/lib/)
[http://www.alsa-project.org/alsa/ftp/utils/](http://www.alsa-project.org/alsa/ftp/utils/)

2. build and install alsa-driver:
```
./configure
make
sudo make install
```

3. build and install alsa-lib:
```
./configure
make
sudo make install
```

4. build and install alsa-utils:
```
./configure
make
sudo make install
```

5. reboot Linux

---

### Post by Unnicknamed on 2007-12-29
Thank you very much, I really appreciate the help you just give me.

---

