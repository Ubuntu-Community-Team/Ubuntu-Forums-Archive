---
title: "Problem with sound/alsa"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by kd35a on 2006-12-27
Hello

I have a problem with my sound, i can't hear anything :/

I get this error when running a program that needs sound, for example alsamixer:
> fredrik@fredrik-linux:/dev$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
My soundcards is built in on the motherboard, which is a Intel FW82815 based one, from intel. (The computer is a HP Vectra VL400)

When i look in /dev/snd (where the sound-devices should be, right?) i can only find "timer". I have enabled the sound-device in BIOS.

ALSA should need the driver intel8x0, and its loaded:
> fredrik@fredrik-linux:/dev$ lsmod | grep snd
snd_intel8x0           34844  0 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

Can anyone see what is wrong??

I'm using Ubuntu 6.10

//Fredrik

---

### Post by dannyboy79 on 2006-12-27
i can point you here, [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
and that's about it! good luck.

---

### Post by kd35a on 2006-12-27
Ok, thanks for the site, it was great! i have read the entire page, but it didn't work :/ 

When typing "cat /proc/asound/modules" i get nothing.

When i looked in "/etc/modprobe.d/alsa-base" i found snd_intel8x0m index=-2, i tested to put it into 0, and also to to put a new option there with intel8x0, with index=0, non worked.

and when i restart alsa, i get this:
> fredrik@fredrik-linux:~$ sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                                                                                                      * warning: 'alsactl store' failed with error message 'alsactl: save_state:1163: No soundcards found...'...                                           [fail]
 * Setting up ALSA...  

some new tips??

---

### Post by dannyboy79 on 2006-12-27
your sound card isn't being found!!! you could have gone through the website I gave you because based on this latest error you're telling me (which is saying you don't have a sound card) you wouldn't of continued with the troubleshooting until you solved the error of finding your sound card! what does lspci -v output? i can't believe that NO ONE ELSE HAS A INTEL motherboard that has onboard sound on it. I know your onboard sound card works. what did you do after you did a install. did you do anything out of the ordinary? are you sure it's enabled in your bios? are you sure you have any motherboard jumpers set correctly? sometime, a jumper can cause the sound to only go to the front headphone jack? if you're using that how to, then you can't continue on with it until you get a true answer or the test that finds the card works.

heres another guide. [http://alsa2.opensrc.org/Quick_Install](http://alsa2.opensrc.org/Quick_Install)

---

### Post by kd35a on 2006-12-27
> fredrik@fredrik-linux:~$ lspci -v
...blablabla...

00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1249
        Flags: medium devsel, IRQ 9
        I/O ports at 1200 [size=256]
        I/O ports at 1300 [size=64]

...blablabla....

It is enabeld in BIOS, yes, i have double-checked. There is nothing wrong with the jumpers, It worked earlier in Ubuntu 5.10, and i haven't been working inside the computer since then, so there is no hardware that has been changed. Thats why I get so confused, the hardware is there, but it can't be found by Ubuntu, I think there is some kind of "high-level" problem somewere.

About the link, I dont think the problem is in ALSA, I think it's somewere in Ubuntu.

---

### Post by dannyboy79 on 2006-12-28
> **kd35a said:**
> It is enabeld in BIOS, yes, i have double-checked. There is nothing wrong with the jumpers, It worked earlier in Ubuntu 5.10, and i haven't been working inside the computer since then, so there is no hardware that has been changed. Thats why I get so confused, the hardware is there, but it can't be found by Ubuntu, I think there is some kind of "high-level" problem somewere.

About the link, I dont think the problem is in ALSA, I think it's somewere in Ubuntu.

well, all I did was search using the info you provided and found this answer. the search feature for this forum is located toward the top right hand side.

[http://www.ubuntuforums.org/showthread.php?t=249627&highlight=Intel+Corporation+82801AA+AC%2797+Audio](http://www.ubuntuforums.org/showthread.php?t=249627&highlight=Intel+Corporation+82801AA+AC%2797+Audio)

---

### Post by kd35a on 2006-12-28
OK, but some problems:
I don't have any "/dev/dsp"
Where is my soundcard, then, if its not in /dev/snd?? i have nothing i can test such things on, if you understand what i mean.

The only time i can see that i have some sound-device is when i write lspci, but no were else, where can i look for my soundcard?? i need to "mount" my soundcard from the "virtual pci-place" to /dev/snd or somewere else.

---

### Post by dannyboy79 on 2006-12-28
i can't help you anymore I am sorry. I have suggested all that I can. search this forum and also search gogle using the info you have about your sound card

---

### Post by kd35a on 2006-12-28
ok :/ but thanks anyway! i have learnd something atleast, now i will go on searching again...

---

