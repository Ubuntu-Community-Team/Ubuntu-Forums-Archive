---
title: "Installed ubuntu on Chromebook no audio at all"
date: 2023-04-08
forum: Hardware
---

### Post by tackskull on 2023-04-08
Hi there, I just installed ubuntu on my chromebook, deleting chrome os. Everything works grate but the only issue is that my chromebook have no sound at all. Even connecting wired headphones the result is the same. The only way to have audio is to connect a bluetooth speaker on any kind. Since I would like the full potential of my chromebook, I would like to resolve this issue. 

I tried to use this guide here [https://gist.github.com/jeremy-breidenbach/92fc648ed2590ff9cd3a0ae57ed98e4a](https://gist.github.com/jeremy-breidenbach/92fc648ed2590ff9cd3a0ae57ed98e4a)

I downloaded the asound state file and unzipped on the download folder; then I runned this 2 codes on terminal:

sudo alsa force-unload

sudo cp ~/Downloads/asound.state /var/lib/alsa

I rebooted the chromebook. There is no audio again, but i can notice that before, on the audio icon in the bottom right part of the screen, use to have a red line (like audio is no avaible), now that red line in not there anymore. 

Can somebody help me solve this issue?

Thanks everybody

---

### Post by tackskull on 2023-04-09
Nobody?

---

### Post by him610 on 2023-04-11
I don't have an answer for you, but I have a few questions.

What are the specs of your chromebook?
Where did you find the guide to install Ubuntu on your Chromebook?
Did you try USB headphones?
Other than no audio through the 3.5mm connection, did you experience any other issues?

In a few months, I will be attempting to install Xubuntu on a Chromebook that is nearing its AUE date.

---

### Post by tackskull on 2023-04-12
My Chromebook specs are theese:
4x intel Celeron N4120 CPU 1.10GHz
memory 3.7 GiB of RAM
Graphics Processor: Mesa Intel UHD Graphics 600

this is the guide I used [https://dbtechreviews.com/2018/09/how-to-install-ubuntu-on-chromebook-and-remove-chromeos/](https://dbtechreviews.com/2018/09/how-to-install-ubuntu-on-chromebook-and-remove-chromeos/)

No, I didn't try usb headphone, I don't have it.
No, I didn't find any other issue. Kubuntu run fast and smooth on this Chromebook, all the apps I installed works fine too. 

Hope somebody can tell me a solution. Is ok just to use bluetooth headphones, but missing the base feature of the built in speakers is a bit a pain in hte hearth.


Processors: 4 × Intel® Celeron® N4120 CPU @ 1.10GHz
Memory: 3,7 GiB of RAM
Graphics Processor: Mesa Intel® UHD Graphics 600

---

### Post by him610 on 2023-04-12
@tackskull - thanks
Whether I have any issues or not with audio when I convert my Chromebook, I will post an entry in this thread.

---

### Post by kinddolphin8827 on 2023-04-13
I may not have the right to pass on my advice, however I have infarct run into this on the machine(s) that I was using in my early early  stint.

The best I can remember I that I had a weird sound blaster or some wacky onboard sound which drove me completely mad utterly ridiculous. Throughout my  years of being an active Linux user.

There are two main questions that I've got for you.

1. What are the specifications of the machine that you are using as you're running Ubuntu?

2. Do you have and hardware that requires proprietary drivers?

3. Could you please provide us with boot logs and screenshots?

---

### Post by him610 on 2023-04-16
> The only way to have audio is to connect a bluetooth speaker on any kind.
If you have audio using bluetooth, I would think you have some misconfiguration with your audio. 
This video explains alsamixer (terminal) and Volume Control (GUI)...[https://www.youtube.com/watch?v=gs9I1gPGn9A]("https://www.youtube.com/watch?v=gs9I1gPGn9A")

By the way, *asound.state* is part of the alsa package. No need bring your own; there is a possibility of corrupting the original file.

---

### Post by tackskull on 2023-04-18
When opening rhe alsamixer on the terminal, it shows 4 audio output, and can't upper the volume of none of them, in fact all the audio remain to a value of 0.

---

### Post by tackskull on 2023-07-17
Guys, I found a solution for pure luck.

I just followed the instrunction on this git-hub page [https://github.com/eupnea-linux/audio-scripts](https://github.com/eupnea-linux/audio-scripts)

 I ran the 3 coomand on the terminal, rebooted my chromebook (I am running Ubuntu on it) and now magically I have sound from the built in speaker. 

Thanks for your support, hope this can help somebody else.

---

### Post by bakedapplin31 on 2023-10-10
The github page is gone, do you have any way to help me get this working?

---

### Post by VMC on 2023-10-12
> **bakedapplin31 said:**
> The github page is gone, do you have any way to help me get this working?

Maybe this is the one:
[https://github.com/eupnea-linux-backup/audio-scripts](https://github.com/eupnea-linux-backup/audio-scripts)

---

