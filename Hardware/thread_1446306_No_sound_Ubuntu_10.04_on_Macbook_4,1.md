---
title: "No sound Ubuntu 10.04 on Macbook 4,1"
date: 2010-04-03
forum: Hardware
---

### Post by Tylerjd on 2010-04-03
In the article, [https://help.ubuntu.com/community/MacBook4-1/Lucid](https://help.ubuntu.com/community/MacBook4-1/Lucid) , it says that sound works out-of-the-box, but when I booted up from a upgrade from 9.10, I can't hear any sound. I've already looked at the alsa config file, but nothing seems wrong. Any suggestions?

---

### Post by Tylerjd on 2010-04-03
I sorda fixed it, I have to plug headphones in, and then pull them out and it works.

---

### Post by brad_c6 on 2010-05-01
idk, still have the sound problem, I tried plug, then unplug and it doesn't seem to do much :confused:

---

### Post by struppi on 2010-05-22
I solved this on my MacBookPro4,1 by adding the following line to my /etc/modprobe.d/alsa-base.conf file:

```
options snd-hda-intel model=mb5
```

It's weird that the mbp4 needs the mb5 model setting, especially since I think I had to set model=mbp3 in a prior version of Ubuntu (I think it was 9.04).


fwiw, I had also performed these steps:

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

as was recommended here:

[http://ubuntuforums.org/showthread.php?t=1489283](http://ubuntuforums.org/showthread.php?t=1489283)

but I'd try the model=mb5 step first without doing the ppa repo update, since it seems it might have only bought me more noise in my logs :/

fyi, here is the output from the alsa information script (from before I added model=mb5):

[http://www.alsa-project.org/db/?f=bc1638ad904adde8b07d633a01c049b8622de626](http://www.alsa-project.org/db/?f=bc1638ad904adde8b07d633a01c049b8622de626)

hth.

---

### Post by s1rUK on 2010-06-03
Hi there, 

I've the same (bothersome) problem with my Macbook. Firstly, I fixed it typing in /etc/modprobe.d/alsa-base.conf the following line

   ```
options snd-hda-intel model=mb5

```

Secondly, I followed the instructions above upgrading my system. My actual version of Alsa is as follows:
```
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 21 2010 for kernel 2.6.32-22-generic (SMP).
``` 

IDK why? I solved it listening the sounds from the speakers but I didn't solve the problem with the headphones. 


Can I fix the problem once and for all?

---

### Post by stib on 2010-09-27
this is what sorted the problem on my mbp (mid 2010 I'm not sure what generation that is):

[INDENT]sudo echo "options snd-hda-intel power_save=10 power_save_controller=N model=mbp5">>/etc/modprobe.d/alsa-base.conf
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)[/INDENT]

---

### Post by jrothim on 2011-03-15
Thanks for everyone's posts!  I had the same issue with my Jan-2011 MacBook Pro; thankfully it now works.

The above post by *stib* on 27 Sept. 2010 (four commands above) also worked for me.  (I did get some kind of GPG error with the "sudo apt-get update" command.)

I am running Ubuntu 10.04 on a MacBookPro6,1 (according to "% sudo dmidecode -s system-product-name").  I am also running kernel 2.6.32-29-generic.

Additionally, I  had to turn everything on in the "alsamixer" controller.  Note the tab key brings up three different pages.  Also "." and "," seem to enable the left and right channels.

Thanks!  Jeff

---

### Post by jrothim on 2011-03-28
I updated to kernel 2.6.32-30, and now the audio no longer works.  It appears that there might not be a linux-alsa-driver-modules-2.6.32-30 package available yet.

Has anyone encountered this problem by chance also?

---

### Post by Dmwebb on 2011-04-01
Im running a Macbook7 (mid2010) with Ubuntu 10.10 I was also having the issue with no sound and the red light from my earbud jack. Ive tried all the steps above to solve my problem but it wasnt until the lest step suggested by jrothim that i fixed the issue. By using the alsamixer controller it allowed me to turn up the volume for both speakers and to turn off my S/PDIF which took care of my red light issue which was just the laptop thinking i plugged in an optical cable. Thanks for the great suggestions from everyone :popcorn:

---

