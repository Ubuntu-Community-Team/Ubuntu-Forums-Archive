---
title: "MSI GE600 Speakers not working"
date: 2010-11-16
forum: Hardware
---

### Post by mr.twister on 2010-11-16
Hello,

I installed Ubuntu 10.04 on MSI GE600 (with ALC888). The problem is that laptop speakers don't play sound, but headphones do. I have unmuted all types of outputs in alsamixer, and tried adding following line to **/etc/modprobe.d/alsa-base.conf**, with several variations of model parameter:

```
options snd-hda-intel model=targa
```

But it didn't help.

I would appreciate if anybody could help me with this problem.

---

### Post by amirf on 2010-12-04
same here ! nothing helps.

---

### Post by kormoran on 2011-01-14
Hi,

first sorry for my english ;-)

This solution is proposed by the Polish forum Wojtek1984 nhl.pl user. 

You must download a modified Alsa drivers from [http://rapidshare.com/files/442250931/alsa-driver-1.0.23_fixed.tar.bz2]("http://rapidshare.com/files/442250931/alsa-driver-1.0.23_fixed.tar.bz2"). Next, you must extract this (write tar -jxvf alsa-driver-1.0.23_fixed.tar.bz2), go to extracted folder (cd alsa-driver-1.0.23_fixed) then compile and install (Wojtek originally use this command: *./configure --with-cards=hda-intel --with-card-options=hda-codec-intelhdmi,hda-codec-realtek --with-oss=no && make && make install * but in my Ubuntu this doesn't work. My solution is: first compile *./configure --with-cards=hda-intel --with-card-options=hda-codec-intelhdmi,hda-codec-realtek --with-oss=no*; when compilation is done write *make* and then type *sudo make install*).

At the end you have to do one more thing - in **alsa-base.conf** located in /etc/modprobe.d at end of file add line *options snd-hda-intel model=targa-8ch-dig enable_msi=1*. 
Save and restart computer, the speakers should work now.

After restart if speakers not work write in terminal alsamixer and check is the speakers on (and master, PCM and front must be set correctly).

Full article of support Linux GE600/GE700 (in polish) -> go [http://www.nhl.pl/index.php?showtopic=31093&st=0]("http://www.nhl.pl/index.php?showtopic=31093&st=0")

---

### Post by tiosus on 2011-02-01
> **mr.twister said:**
> Hello,

I installed Ubuntu 10.04 on MSI GE600 (with ALC888). The problem is that laptop speakers don't play sound, but headphones do. I have unmuted all types of outputs in alsamixer, and tried adding following line to **/etc/modprobe.d/alsa-base.conf**, with several variations of model parameter:

```
options snd-hda-intel model=targa
```But it didn't help.

I would appreciate if anybody could help me with this problem.



i used this and worked grate

```
 options snd-hda-intel model=targa-dig
```

---

### Post by jasonrey on 2011-04-19
hi,

i have a similar problem myself, with my GE700. i also have ALC888.

when i plug in a headphone into the audio jack, there is sound, no problem with that. but when i remove it, there's no sound from the speaker :confused:

i tried different settings in the alsa-base.conf file. still no success. everything's updated through update manager.

it works perfectly in win7, though. i have it on dual boot.

in the above post by @kormoran, the posted file is not available anymore.

any help is appreciated :)

---

### Post by kormoran on 2011-04-29
Hi,

I uploaded this driver again, now is located at: [http://www.megaupload.com/?d=9UNE0HN4](http://www.megaupload.com/?d=9UNE0HN4)

---

### Post by jasonrey on 2011-05-01
thanks! this works perfectly on my GE700. you're the best! :)

speakers and everything works great! woohoo! btw, i'm on 11.04 now :)

---

### Post by rastar101 on 2011-05-31
excuse me for my so bad english
i sucsesful for active sound car on msi ge600 & ge 700 on ubuntu 11.04 & 10.10 
step by step
1- download This Package from :
[http://rapidshare.com/files/442250931/alsa-driver-1.0.23_fixed.tar.bz2](http://rapidshare.com/files/442250931/alsa-driver-1.0.23_fixed.tar.bz2)
[http://www.megaupload.com/?d=9UNE0HN4](http://www.megaupload.com/?d=9UNE0HN4)
2-run on Terminal
Code
> 
rm -rf ~/alsa* ~/.pulse*
sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo nautilus
3-with opened window copy that package from downloaded place to /usr/scr/alsa/
4-run on terminal
> 
sudo tar xjf alsa-driver*
cd alsa-driver*
sudo ./configure
sudo make
sudo make install
sudo gedit
5-on opened gedit click in file/open 
open this file:
/etc/modprobe.d/**alsa-base.conf**
at the end of page add this line :
> 
 *options snd-hda-intel model=targa-8ch-dig enable_msi=1*
6- restart 
7-After restart if speakers not work write in terminal alsamixer and check  is the speakers on (and master, PCM and front must be set correctly)
excuse me for bad english again

---

### Post by harane on 2011-08-08
Hi, everyone.
I also have a GE600.
I installed 11.04 and upgrade latest alsa driver 1.0.24 using auto update script.

I tried many options with numerous rebooting as follows:

*options snd-hda-intel model=targa-8ch-dig enable_msi=1* .... no sound
[I]options snd-hda-intel model=targa-2ch-dig ..... no sound
[/I]*options snd-hda-intel model=targa-2ch .... no sound*
*options snd-hda-intel model=targa .... no sound*
*options snd-hda-intel model=auto .... no sound**options snd-hda-intel model=*3stack-6ch .... no sound
[I]---------- no option --------------   ..... only headphone works and speaker is not.
I removed pulse at all   ...........  soundcard option disappeared
full reinstall ubuntu  ...............  repeat same situation
 
What can I do more?
I check alsamixer after everyt rebooting.
And I tried to reinstall my ubuntu, too.
Win7 has no problem in sound via speaker.

It had no problem when using ubuntu 10.04


[/I]

---

### Post by harane on 2011-08-21
> **harane said:**
> Hi, everyone.
I also have a GE600.
I installed 11.04 and upgrade latest alsa driver 1.0.24 using auto update script.

I tried many options with numerous rebooting as follows:

*options snd-hda-intel model=targa-8ch-dig enable_msi=1* .... no sound
[I]options snd-hda-intel model=targa-2ch-dig ..... no sound
[/I]*options snd-hda-intel model=targa-2ch .... no sound*
*options snd-hda-intel model=targa .... no sound*
*options snd-hda-intel model=auto .... no sound**options snd-hda-intel model=*3stack-6ch .... no sound
[I]---------- no option --------------   ..... only headphone works and speaker is not.
I removed pulse at all   ...........  soundcard option disappeared
full reinstall ubuntu  ...............  repeat same situation
 
What can I do more?
I check alsamixer after everyt rebooting.
And I tried to reinstall my ubuntu, too.
Win7 has no problem in sound via speaker.

It had no problem when using ubuntu 10.04

[/I]

This is my alsa information:
[http://www.alsa-project.org/db/?f=026293a84cd5db3a28a2174dbbe23af4b6d7634e](http://www.alsa-project.org/db/?f=026293a84cd5db3a28a2174dbbe23af4b6d7634e)

I upgraded kernel any still no sound.  
I think I have to boot with Win7 for music and movie sadly.

---

### Post by stu87282 on 2011-08-23
Hello everybody
I got a MSI GE600 too
Have u guys have ever counter this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651104")?
everything goes well when installing ubuntu and first boot
but about second or third reboot this bug appears for unknown reason
and it started tracing ,then stuck...
and I can't enter ubuntu any more...
It seems u guys can run ubuntu on GE600
have any idea what happened with my GE600? How to slove it?
can u teach me step by step? Plz

PS. I am new to ubuntu and sorry for my poor English...:(

---

### Post by harane on 2011-08-23
MSI600GE supports graphic card switching.
You can select AMD instead of Intel in BOIS.

---

### Post by stu87282 on 2011-08-23
> **harane said:**
> MSI600GE supports graphic card switching.
You can select AMD instead of Intel in BOIS.
Everything works perfectly but speakers now!!!
Thank you :)

PS. I follow rastar101's steps but my speakers still not working :(

---

### Post by artwoofer on 2011-10-13
> **stu87282 said:**
> Everything works perfectly but speakers now!!!
Thank you :)

PS. I follow rastar101's steps but my speakers still not working :(
Rastar is My best friend This stepm is true
1- download This Package from :
[http://rapidshare.com/files/44225093..._fixed.tar.bz2]("http://rapidshare.com/files/442250931/alsa-driver-1.0.23_fixed.tar.bz2")
[http://www.megaupload.com/?d=9UNE0HN4](http://www.megaupload.com/?d=9UNE0HN4)
2-Extract the folder on your Desktop
3. open terminal go to desktop directory from this cammand:
```
cd Desktop
```4. go to extracted folder from this command:
```
cd alsa-driver-1.0.23_fixed
```5.than for compile type this command :
```
*./configure --with-cards=hda-intel --with-card-options=hda-codec-intelhdmi,hda-codec-realtek --with-oss=no*;
```6.now make by this command:
```
make
```if dont work use this:
```
sudo make
```7.now install driver by this command:
```
*sudo make install*
```8. now run gedit by this command:
```
sudo gedit                      
```on opened gedit click in file/open 
open this file:
/etc/modprobe.d/**alsa-base.conf**
at the end of page add this line :
     ```
*options snd-hda-intel model=targa-8ch-dig enable_msi=1*
```please save file & restart yoy system
9.-After restart if speakers not work write in terminal alsamixer and  check  is the speakers on (and master, PCM and front must be set  correctly)
10.please tel me this steps working for you or not .
excuse me for bad english again

---

### Post by fredz_ on 2011-12-30
hello everyone.

the actual patch works just fine, but unfortunately, no longer with new kernel (3.0 branch).

I am actually unable to build it under the new ubuntu (11.10).  

has anyone encountered the same issue?

---

### Post by domtom66 on 2012-01-01
Hello,

I have the same problem with my MSI GE700 running Ubuntu 10.04. I've tried the described procedure given by Kormoran and I can run the ./configure. Unfortunately the next step (make) stops with the following failure:

p ../../alsa-kernel/include/core.h .
patch -p0 -i core.patch core.h
make[4]: patch: Command not found
make[4]: *** [core.h] Error 127
make[4]: Leaving directory `/home/dom/Downloads/alsa-driver-1.0.23_fixed/include/sound'

Any idea what's going wrong?

Dominique

---

### Post by artwoofer on 2012-02-02
> **domtom66 said:**
> Hello,

I have the same problem with my MSI GE700 running Ubuntu 10.04. I've tried the described procedure given by Kormoran and I can run the ./configure. Unfortunately the next step (make) stops with the following failure:

p ../../alsa-kernel/include/core.h .
patch -p0 -i core.patch core.h
make[4]: patch: Command not found
make[4]: *** [core.h] Error 127
make[4]: Leaving directory `/home/dom/Downloads/alsa-driver-1.0.23_fixed/include/sound'

Any idea what's going wrong?

Dominique
hi 
i have too this problem please go step by step my Method.

---

### Post by jasonrey on 2012-02-16
does anyone else have another copy of the driver? megaupload is down now ;)

---

### Post by artwoofer on 2012-02-29
> **jasonrey said:**
> does anyone else have another copy of the driver? megaupload is down now ;)
hi
Download from This link :
[http://www.4shared.com/zip/KtusPY6y/alsa-driver-1023_fixed.html](http://www.4shared.com/zip/KtusPY6y/alsa-driver-1023_fixed.html)

---

