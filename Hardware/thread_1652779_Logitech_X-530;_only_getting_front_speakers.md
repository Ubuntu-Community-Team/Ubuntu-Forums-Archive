---
title: "Logitech X-530; only getting front speakers"
date: 2010-12-25
forum: Hardware
---

### Post by Justym on 2010-12-25
Alright, I've had Ubuntu for a while now (most recently had to reinstall due to a problem I couldn't fix, 10.04) yet I know nothing about how to fix things on it...I've been looking on Google on how to get the rear and center speakers to work for me, but they just won't.

Now, if there's a solid solution for this, I'll need step by step for answers. This includes all the 'troubleshooting' information. I know that if you know more about my hardware would help, but getting that on here is difficult for me. So anyways...

Let's get this started. ><"

---

### Post by Justym on 2010-12-30
Hm, 4 days....I'll bump this... If I'm not allowed to, sorry. =/

---

### Post by Justym on 2011-01-05
Hm...6 days this time....anyone? Again, sorry if I'm not allowed to bump this or whatever...

---

### Post by Justym on 2011-01-12
6 days again... 
Does anyone know at all how to get my 5.1 system working?
=/

---

### Post by Justym on 2011-01-23
Another bump since no one's replied...

---

### Post by rowland on 2011-03-14
Right click on the little speaker icon next to the clock, Sound preferences.
Hardware> Choose a device to configure. I think there has to be 1 that is the video card, and there may be another one. For me its: Internal Audio. 1 output. If not, then its your video card that is the sound card as well...
When you have chosen wich one, (Internal Audio 1 output for me), then down, before the close button choose profile: I have selected Analog Surround 5.0 Output> Close
By this i think you should hear all sounds on all 5 speakers, and the subwoofer works alone. If you have a microphone, then i think you have to select: Analog surround 5.0 Output + Analog stereo Input.
My experience with that is that it gives me some sort of a beeping or background noise.... But i'm not sure whats with all that.
I hope this was useful for you.
If i can help you in anything else, e-mail me @ [email]sosroli@gmail.com[/email]
(notice that im newbie)
good luck

---

### Post by Justym on 2011-03-17
I should mention that my sound thing is no longer configured for the default Sound in the Preferences. Somehow or another I've gotten Gnome ALSA Mixer to be used for my Sound preferences.

Either I need a fix that would allow me to get all 5 of them working with the ALSA Mixer, or I need to know how to get rid of the ALSA Mixer and then configure my 5 speakers to the regular Sound preferences...

---

### Post by Justym on 2011-04-05
Bumpaaage

---

### Post by Justym on 2011-04-16
Yet another bump. I wonder how long this will take o.o

---

### Post by Justym on 2011-04-30
They say Patience is a Virtue...

---

### Post by sanbalestrini on 2011-05-07
I have the same problem. Any assistance would be greatly appreciated.

---

### Post by Justym on 2011-05-19
Another bump...

---

### Post by lidex on 2011-05-20
> **Justym said:**
> Another bump...

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Justym on 2011-05-21
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

[http://www.alsa-project.org/db/?f=740dc0c549c99fbc905eaa709fa8423a83abaa9f](http://www.alsa-project.org/db/?f=740dc0c549c99fbc905eaa709fa8423a83abaa9f)

---

### Post by lidex on 2011-05-22
Try resetting your pulse configuration.
Using a Terminal="Applications-> Accessories-> Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by Justym on 2011-05-23
That didn't really do anything...

---

### Post by lidex on 2011-05-24
Then try the alsa upgrade via the link in my sig.

---

### Post by Justym on 2011-05-26
> **lidex said:**
> Then try the alsa upgrade via the link in my sig.

I got all the way until the part where I test it. The regular test worked fine, but the multichannel did not.

"{USER}@{COMPUTERNAME}:~/Desktop$ speaker-test -D surround51 -c6

speaker-test 1.0.24.2

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument"

---

### Post by lidex on 2011-05-27
Edit your /etc/pulse/daemon.conf file thusly:
```
gksu gedit /etc/pulse/daemon.conf
```
More info here:
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)
[http://forums.debian.net/viewtopic.php?f=7&t=47953](http://forums.debian.net/viewtopic.php?f=7&t=47953)

---

### Post by Justym on 2011-05-27
I edited it, restarted and still it doesn't work.
The Sound Preferences thing doesn't work either, it doesn't list 5.1 as an option. For whatever reason, now whenever I try to open System>Preferences>Sound it continually loads saying "Waiting for sound system to respond" without actually doing anything. I assume this is because of the addition of ALSA/PulseAudio. 

Anyway, I made the edit, still only the front two speakers and subwoofer.

---

### Post by lidex on 2011-05-27
This item may not be fully compatible. I don't want to beat a dead horse. Have you tried the logitech site/boards?

---

### Post by Justym on 2011-05-28
> **lidex said:**
> This item may not be fully compatible. I don't want to beat a dead horse. Have you tried the logitech site/boards?

No, I have not.

---

