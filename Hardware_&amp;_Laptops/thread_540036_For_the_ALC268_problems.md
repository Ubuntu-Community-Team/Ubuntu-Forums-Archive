---
title: "For the ALC268 problems"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by redwinedrummer on 2007-09-01
Hello everyone,

This is for those who are experiencing problems with the Realtek ALC268 codec on their laptops.

I've had the same problems with an Acer 4520G notebook, but thankfully, **the new ALSA 1.0.15 RC1 natively supports the ALC268. ** Installed it without problems.

I have to confirm, though if my previous attempts at fixing the audio might've affected it. I tried OSS (4.0.1066) and ALSA 1.0.14. OSS did not help, and ALSA worked partially. System sounds did not work with ALSA and with the help of other forum goers, had to add "options snd-hda-intel model=acer" to /etc/modprobe.d/alsa-base. So I'm not sure if the remnants of the old OSS and/or ALSA might've affected the audio one way or another. But I compiled and installed the ALSA RC from scratch and audio is working without problems.

The headphones are working, but I haven't tested the microphone and line-in.

Hope this solves most (if not all) ALC268 problems. Props to the ALSA team!

ALSA RC changelog: [http://www.alsa-project.org/main/index.php/Changes_v1.0.14_v1.0.15rc1]("http://www.alsa-project.org/main/index.php/Changes_v1.0.14_v1.0.15rc1")

Update: Apparently, system sounds are still not working. Audio on Mozilla browser as well.

---

### Post by Corentin38 on 2007-09-01
I'm glade the new version of the ALSA's drivers support the ALC268 realtek sound card : It is the one in my zepto 6224W notebook too !

But could somebody explain the way to install these drivers ? I'm using the tribe 5 of gusty for some hybrid hard drive problems ... I'm not really a compilation's champion ... well ... in facts, I dont know anything about it ! The ./configure, make and make install send me back an error since the make command ...

I'm sorry i I don't post in the good topic, but I'm from the ubuntu-fr forum and my english is not as well as i would like !

Thanks

---

### Post by Josillo on 2007-09-01
Thanks for the good news!!!

Finally the sound is working in my notebook.  I have a Toshiba Satellite U305-S5107
I'm leaving here some links that I found helpfull to make this work.

First, downloaded the drivers version 1.0.15rc1 from here:

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

(I downloaded alsa-drivers, alsa-lib and alsa-utils)



Then I installed them following these instructions:
[https://help.ubuntu.com/community/SoundTroubleshooting#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8](https://help.ubuntu.com/community/SoundTroubleshooting#head-083f68c150e8cc9de635a7ab89b8ccfc6100ecf8)

(follow the same procedure for drivers, libs and utils)


Last step:  I added the line
```

options snd-hda-intel model=toshiba
```

to the /etc/modprobe.d/alsa-base


Let me point out that my sound didn't work until I added this last line to the alsa-base file.  Probably  you'll have to use another option if your notebook is not a toshiba.


I hope this is clear enough for you, you can ask me anything if it is not.


Cheers!!!

---

### Post by redwinedrummer on 2007-09-01
Josillo,

I'm glad you got your audio working!

> 
Let me point out that my sound didn't work until I added this last line to the alsa-base file. Probably you'll have to use another option if your notebook is not a toshiba.


Yes, I experienced this, too. I had to add
```
options snd-hda-intel model=acer
```

However, there are still no system sounds (log in, log out etc) and audio in flash. Are you experiencing this too? I saw two fixes in the web, but didn't work. One was modifying the /etc/firefox/firefoxrc and adding

```
firefox_DSP="aoss"
```

But the source for that fix was outdated. It was written for Dapper Drake. Also found a fix that involves linking libesd. Doesn't work, either.

Corentin38,

I'm sorry, but I don't have much experience in debugging make errors. Maybe someone who has more experience can help. But for starters, are you using "make" and "make install" as root? Can you also post the output of your make, since it's generating errors?

---

### Post by Josillo on 2007-09-02
After doing what I explained before the sound worked just fine, includin system sound and flas (I tested it in youtube.com)

I'm sorry I can help you with that!!!


I executed  ¨make¨ and ¨make install¨ both as root, using sudo

```
./configure
sudo make
sudo make install
```

The only error I got where....

from executing ¨configure¨

```
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
```

and from executing ¨sudo make¨

```
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
```

Fortunately no error message at all from ¨sudo make install¨


I'm sending the standard output of the three commands attached.  I hope you find this helpful!
(I had to attach them as a tar archive because separate txt files would exceed upload limit)
Cheers.


Josillo

---

### Post by Corentin38 on 2007-09-02
I don't have compilation error anymore, but it's still not working ...
What is the name of the sound card, for the ./configure command's option --with-card ?

---

### Post by Josillo on 2007-09-02
As I read from here:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

it should be:

```
sudo ./configure --with-cards=hda-intel
```

But I haven't used that option, and it worked perfectly fine for me.  As I said  before I just executed:

```
sudo ./configure
```

With no aditionial options.


Cheers

---

### Post by Josillo on 2007-09-03
By the way... I've just discovered something I'd like to chance and I wanted to ask you guys if you have any idea how to do it, because I've been searching the forum, but can't find a clue about it.

The issue is that now I have my sound card working perfectly, but the volume control wheel in my laptop affects the Headphone Volumes.

Any idea on how can I change it to affect the Master Volume or the PCM volume instead?

Thanks!


Josillo

---

### Post by Corentin38 on 2007-09-03
no idea !

---

### Post by HumanAnarchist on 2007-09-16
thanks for this thread!

Made the sound work, but still got a problem that the sound comes out both in the internal speaker and in the headphone, when the headphone is plugged in...

-ha-

---

### Post by skinnie on 2007-10-27
I have that same problem..and the thing is..if u mute the volume,and have some headphones connected,they still get sound..
other thing..my skype has no sound..I tried all devices there and no way..

---

### Post by fedevit on 2007-11-11
I'm receiving the following error message when I execute 

sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes

for the alsa-utils

The message is:
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

all the procedure for drivers and lib went right to the end without any error message.

what can I do?

Please help me, I would appreciate any suggestion

---

### Post by mayfly on 2007-12-14
Hi,

I have been following the various instructions linked to in this thread (i have no sound at all, not even system sounds) and have run into a problem. I have an hda-intel card with a realtek id 268 chip. downloaded the newest version of the alsa driver (1.0.15), followed the directions for installation to a tee... alsa-driver-1.0.15 installed fine, alsa-lib.-.015 installed fine, but when i tried to install alsa-utils-1.015 i got the following error:

checking for libasound headers version >= 1.0.12... not present.
configure: error: Sufficiently new version of libasound not found.

So I checked for my version of libasound...it is 1.0.14. I may not be a math wizard but that seems >= 1.0.12 to me. wtf. Soooooo...I restarted my computer, and now my soundcard doesn't show up at all! alsamixer tells me "no such device", there is absolutely nothing in proc/asound/cards...what did I do???? is the disappearance of my soundcard related at all to this libasound thing?

I am a brand new user of linux, so my apologies if I didn't express anything correctly in this message...all i want for xmas is sound!

---

