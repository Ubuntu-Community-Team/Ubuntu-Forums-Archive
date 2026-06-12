---
title: "Hda Intel jack sense not working 10.04"
date: 2010-05-03
forum: Hardware
---

### Post by skajoeska on 2010-05-03
I'm having problems getting Ubuntu to recognize when my headphones are plugged into my laptop. When I boot up the sound comes from both the internal speakers and headphone jack. If I unplug my headphones and plug them back in Ubuntu recognizes them and works as desired. I know that intel audio and Ubuntu don't get along well and this is a well discussed subject but I couldn't find anyone with this problem or a solution. Still any links to other posts are very welcome.

In the past all I had to do was add```
options snd-hda-intel model=lenovo
``` into my /etc/modprob.d/alsa-base.conf file. I have tried all of the different models listed for my codec found [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt") but to no avail.

I have also tried to compile the latest realtek drivers with the option ```
./configure --with-cards=hda-intel
``` as per [these]("http://ubuntuforums.org/showpost.php?p=9203173&postcount=7") instructions without success.

this has been an issue for me since 9.04 and still can't find a definite solution. Everything is unmuted and turned to 11 in alsamixer.

useful info:
```
joe@CONDOR:~$ cat /proc/asound/card*/codec#* | grep Codec
Codec: Realtek ALC861-VD
Codec: LSI ID 1040
joe@CONDOR:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 30 2010 for kernel 2.6.32-21-generic (SMP).
joe@CONDOR:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861-VD Analog [ALC861-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

If you need anything else just ask. Thanks.

---

### Post by Johnzw on 2010-05-04
I also have this problem. I also have the problem of audio dropping completely (and being replaced by static) occasionally.

```

john@shada:~/audio$ cat /proc/asound/card*/codec#* | grep Codec
Codec: LSI ID 1040
Codec: Realtek ALC861-VD
john@shada:~/audio$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

```

This is quite vexing and one of *many* things that Lucid broke (in the grand tradition of Linux upgrades hosing everything...). I'd desperately like to get my audio working correctly again. Any help would be greatly appreciated.

---

### Post by skajoeska on 2010-06-19
I forgot I posted this. But I still have the same issues. So Bump.

---

### Post by duruttye on 2010-07-28
Any news on this?

---

### Post by skajoeska on 2010-07-28
Once again I way over thought this problem. I fixed this a bit back so I don't remember all the conditions surrounding my success. But i'm pretty sure all I had to do was open up alsamixer and mute "front" by highlighting it and pressing the "m" key. After a quick reboot everything worked as wanted. I could have sworn I had done this before. So I might of installed some dependencies or something that along with muting front fixed it. Sorry not to be too much help. If that doesn't work just reply back and i'll see what I can remember.

Joe

---

### Post by lvleph on 2010-08-10
A work around is to go to sound preferences and switch the output to headphones.

I also found this 
[http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html](http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html)
but I am in the middle of checking to see if it works.

EDIT: All that needs to be done is
```
sudo apt-get install linux-backport-modules-alsa-lucid-generic
```
After restart everything works.

---

### Post by Gaius on 2010-09-03
Hello

I have this problem as well. 
Alsamixer way isn't working for me, nearly blew my eardrums trying it :)
If i mute the Speakers, no front option in there, I only get sound to the headphones but it's kinda low. If I touch a volume control both speakers and headphones goes back to full volume again.

```
gaius@Voidray:~$ sudo apt-get install linux-backport-modules-alsa-lucid-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backport-modules-alsa-lucid-generic

```

Is what I get from the other option for a fix. Anyone got any ideas?
Hardware is much the same as previous posters. Laptop is Acer Aspire 7736ZG


/G

---

### Post by pierreu1 on 2010-09-04
> **lvleph said:**
> A work around is to go to sound preferences and switch the output to headphones.

I also found this 
[http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html](http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html)
but I am in the middle of checking to see if it works.

EDIT: All that needs to be done is
```
sudo apt-get install linux-backport-modules-alsa-lucid-generic
```After restart everything works.

The fix in the link worked for me. Many thanks.

---

### Post by Gaius on 2010-09-04
I managed to install the backport but that didn't do anything constructive.

I've tried adding this line to my alsa-base.conf. 
options snd-hda-intel model=XXXXX enable=1 index=0

Problem is there isn't a good model for me to put in there for my ACL888 chip.
Looking in [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt)
I have tried 3stack-dig and acer as models, didn't help any (Acer Aspire 7736ZG)

/Gaius

---

### Post by daqron on 2010-10-26
> **Gaius said:**
> Hello
```
gaius@Voidray:~$ sudo apt-get install linux-backport-modules-alsa-lucid-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backport-modules-alsa-lucid-generic

```/G
I get the same error. I enabled backports in my software sources but still not found. I have found tons of results on Google for headphone jack sense issues in 10.04 but no working solutions. The "headphone jack sense" option doesn't even seem to exist anymore.

I have a Dell Studio XPS 9100. Headphones work but they don't disable speakers when plugged in. Also microphone jack doesn't work. 

ARGH. Back to Windows for now because I need these :(

---

### Post by p2ranger on 2010-10-26
I was able to get my jacksense to work. I have a Lenovo G555, which I realize is different. But here is the thread that I followed to get it to work. It may provide of some use.

[http://ubuntuforums.org/showpost.php?p=9906171&postcount=24]("http://ubuntuforums.org/showpost.php?p=9906171&postcount=24")

Realize, that in the third step the driver that it requests you to download from linuxant.com may not be for the same sound card as what you have.

Hope that helps some

Jason

---

### Post by Gaius on 2010-10-28
After the latest kernel update together with the audio team alsa snaphot for that kernel my problems with jack sense was solved. 

Try launchpad, if you haven't already, and search for a similar bug or add a new one for your system.

/Gaius

---

### Post by swarna_cse on 2011-04-14
Yes, I am having the same problem since Lucid. It is very irritating. Had earlier tried many workarounds but none worked.

I am now using Natty.:(

---

