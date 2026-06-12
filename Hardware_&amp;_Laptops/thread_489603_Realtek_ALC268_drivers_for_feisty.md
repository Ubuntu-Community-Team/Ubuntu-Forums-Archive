---
title: "Realtek ALC268 drivers for feisty?"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by talava on 2007-07-01
Hi all,

I'm struggling to find drivers for my realtek 268 sound card. Realtek has driver for the 262 for example but not the 268. Those are available only for vista.

Do I have a chance to get the sound working working in feisty?

My laptop is the Acer 6292.

---

### Post by HumanAnarchist on 2007-07-01
I got the same card and it's not working in Gutsy either :( 

I think it's included in the latest and greatest version of alsa. I read it on the mailinglist for alsa-development, so I'm waiting for it to be included in the next update of alsa for Gutsy. 

-ha-

---

### Post by talava on 2007-07-02
So you don't mean the 1.0.14? Is there a newer one for gutsy?

My laptop is starting to seem pretty damn useless with feisty... Still waiting support for my wlan card and a way to get the 3d-effects working.

Maybe i'll just give up and wait for astable version of gutsy to arrive and hopefully better times will follow :)

---

### Post by HumanAnarchist on 2007-07-02
I don't mean 1.0.14, but the development source for alsa. I guess it will be 1.0.15 when it's released. 

I got a AGN4965 wlan card and it works in Gutsy with the native driver, no ndiswrapper. I had to install it manualy from source and compile the module. 

My nVidia 8400m GS card also works in Gutys. I installed with the help of 'envy' and the manual option. I had to hack the file /usr/share/envy/instun/classes.py. I just did a search and replace feisty with gutsy and it worked :) 

I guess when Gutsy finaly comes out, your laptop should work fine 

-ha-

---

### Post by blobbe on 2007-07-02
I tried compiling the latest alsa sources on my TravelMate 6292. Now I get sound from the headphone jack but at a very low level. No audible sound from the integrated  speakers though.

---

### Post by HumanAnarchist on 2007-07-02
I haven't tried that yet, but it's a start. 

Have you checked 'alsamixer'? Or 'alsactl store' and look at the settings of that file. Maybe you can edit that file and restore it. I saw that as a tips on the alsa-dev mailinglist. 

-ha-

---

### Post by blobbe on 2007-07-02
Yep, I've played around with alsamixer, unmuted everything and set all channels to max. Editing the config file that 'alsactl store' saves didn't help either. It offers exactly the same controls as alsamixer and you can't go above the max volume. :)

---

### Post by HumanAnarchist on 2007-07-02
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165)

Looks like the developers of alsa is working on our card right now :) Maybe in some days it will work.

---

### Post by JAmerican on 2007-07-02
Try this...

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

It worked for my ALC882 Realtek HD Audio. But if you have sound, just increase the volume in ALSAMIXER.

My card had sound so I just increased it without the guide after I reinstalled Ubuntu. 

JAmerican

---

### Post by HumanAnarchist on 2007-07-02
This problem is for Realtek 268 only, but it seams like it has been fixed now. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326)

-ha-

---

### Post by blobbe on 2007-07-02
Sound working! Both the integrated speakers and the headphone jack now work with adequate volume.

I recompiled the latest alsa development sources using the patches (realtek10.tar.gz and realtek11.tar.gz) found on
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104)

Then added the following line to /etc/modprobe.d/alsa-base:
options snd-hda-intel model=toshiba

According to [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165) you probably only need the patch from realtek10.tar.gz.

---

### Post by talava on 2007-07-03
Wow, can't wait for that miraculous patch!

Once I have sound i pretty much have every *vital * feature working on my laptop. Then I can get back to getting the 3d effect working.

---

### Post by AlteredAgain on 2007-07-05
i don't understand much of linux, i'm really new and just installed Ubuntu for the first time last night.

i have the same sound card as you do and i am struggling to get the sound to work. :(

can anyone guide me through this?

---

### Post by talava on 2007-07-10
I failed getting the sound working too. I tried installing the 1.0.14 version manually with no succes. According to the [mini-HOWTO]("http://www.alsa-project.org/~valentyn/Alsa-sound-mini-HOWTO-4.html") it seems I don't have a proper kernel source tree since certain directories are claimed to be missing.

A more understandable guide on getting the ALC268 working would be nice... Or i'll just wait for the new Alsa to be in the repositories.

---

### Post by blobbe on 2007-07-10
talava: I think it's the linux-headers-generic package you're missing. It will probably take a while before this fix gets to the Ubuntu repositories. I don't even think it's in the latest development sources of alsa yet.

You should be able to get things working by following these steps:

1. Install packages you need to do the compilation, you probably only need build-essential and linux-headers-generic, but I'm not really sure:
```

sudo apt-get install build-essential linux-headers-generic

```

2. Download the alsa driver sources:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)

3. Extract and untar the driver sources:
```

tar -jxvf alsa-driver-1.0.14.tar.bz2

```

4. Download realtek12.tar.gz found here:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104)

Login as guest (if you don't have an account).

5. Extract the files:
tar -zxvf realtek12.tar.gz

6. Put the extracted files (patch_realtek.c and hda_codec.c) in the pci/hda subdirectory of the alsa driver sources.

7. Configure, compile and install the driver, by going to the driver source directory and doing the following:
```

./configure
make
sudo make install

```

8. Add this line to e.g. the end of /etc/modprobe.d/alsa-base so the correct (fixed) model is used:
```

options snd-hda-intel model=toshiba

```

You can use e.g. pico to edit the file:
```

sudo pico /etc/modprobe.d/alsa-base

```

After adding the line, save with Ctrl-O + Enter and exit with Ctrl-X.

9. Restart the computer.

If you don't feel like restarting this should probably work to:
```

sudo /etc/init.d/alsasound stop
sudo modprobe -r snd-hda-intel
sudo modprobe snd-hda-intel

```

---

### Post by talava on 2007-07-10
Thanks blobbe for that. But i decided to try compiling the Alsa once more and this time there were no complications. So my sound is working fine now.

I made a small post about [ubuntu on my laptop]("http://ubuntuforums.org/showthread.php?t=497686") and i'll add your advice there in case someone has those problems.

---

### Post by dehuszar on 2007-08-11
Hey, quick question.  

I am also toying with this whole process on my Satellite U305-S5097 and I'm wondering if you folks are all uninstalling the ALSA 1.0.13 debs that come in the Feisty repos.  I went ahead and uninstalled all the debs, but the alsa-utils deb won't uninstall without taking out gdm and ubuntu-desktop, which is a bummer.  There's also the asound2 library of the same version which threatens to take out the entirety of usable apps if removed.  Are you all just leaving those debs in place?  All the debs?  

I ask because so far, I can only get OSS to work.  Checking to see if pre-installed ALSA debs might be hindering the ALSA side of the equation.  All attempts at making sound play from the hda-intel ALSA device gives me this precious error:

> audiotestsrc wave=sine freq=512 ! 
audioconvert ! audioresample ! gconfaudiosink: 
Could not open resource for writing

---

### Post by blobbe on 2007-08-12
> **dehuszar said:**
> Hey, quick question.  

I am also toying with this whole process on my Satellite U305-S5097 and I'm wondering if you folks are all uninstalling the ALSA 1.0.13 debs that come in the Feisty repos.  I went ahead and uninstalled all the debs, but the alsa-utils deb won't uninstall without taking out gdm and ubuntu-desktop, which is a bummer.  There's also the asound2 library of the same version which threatens to take out the entirety of usable apps if removed.  Are you all just leaving those debs in place?  All the debs?

Don't remember uninstalling anything, so I guess I just left all installed packages in place.

---

### Post by dehuszar on 2007-08-12
> **blobbe said:**
> Don't remember uninstalling anything, so I guess I just left all installed packages in place.

And do you have full ALSA sound or are you using OSS?

Also, does your microphone work?

---

### Post by blobbe on 2007-08-13
> **dehuszar said:**
> And do you have full ALSA sound or are you using OSS?

I'm using ALSA.

> **dehuszar said:**
> Also, does your microphone work?

I haven't got it working but I haven't tried very hard either, because I don't need it at the moment. But the microphone not working seems to be a common problem. You could try the suggestion in the last post ( Cimmo 07-31-07 18:28 ) here:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165)

---

### Post by Pixman on 2007-08-13
Doesn't seem to be fixed yet.
Has anyone got a solution for this? It's such a shame, that this still doesn't work. I don't know, why no one was able to do this yet. Not that I'm anyone urging to do it, I'd do it myself if I could and I'm atm trying to learn about sound cards, I already know some stuff about driver development.

However, any suggestions are welcome.
I've got a Acer Aspire 5310 with an ALC268 chipset... only works with ACPI=OFF.. 
Sucks so hard, that everything works except the sound, which is essential to my work...


Besides, in the end, it works with acpi=off... could the problem be elsewhere than ALSA?

It acts like it plays audio.. every program plays through it. But I just hear no sound.... and the mixer is not muted... too strange. :/

Compiled the latest HG source of alsa... brought me further at least a bit through setting me up with all controls on my card :)

---

### Post by Sollos on 2007-08-26
I'm just telling that my sound and headjack work after I install the new alsa-driver. But what a pain, the sound still come out from my speaker after I plugged in my earphone. It seems both the headphone and the speaker still activated. Didn't found any solutions for this yet!!!

---

### Post by dehuszar on 2007-08-26
Sadly, there's no way to do it other than manually adjusting the volume slider for each output.  It looks like all this stuff is being worked on in the development branches.  I guess we'll just have to sit tight until the next alsa release/update.  I am anyway.

---

### Post by Josillo on 2007-09-01
Hello all !!!

I've been strugling with this specific chip for a few weeks now, and finally It's working!

Here's where I found the solution.

[http://ubuntuforums.org/showthread.php?p=3294483#post3294483](http://ubuntuforums.org/showthread.php?p=3294483#post3294483)

I hope this is good for you too.


Enjoy!

---

### Post by dehuszar on 2007-09-02
I couldn't get ALSA to work.  OSS only.

---

### Post by enz on 2008-05-29
> **blobbe said:**
> talava: I think it's the linux-headers-generic package you're missing. It will probably take a while before this fix gets to the Ubuntu repositories. I don't even think it's in the latest development sources of alsa yet.

You should be able to get things working by following these steps:

1. Install packages you need to do the compilation, you probably only need build-essential and linux-headers-generic, but I'm not really sure:
```

sudo apt-get install build-essential linux-headers-generic

```

2. Download the alsa driver sources:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)

3. Extract and untar the driver sources:
```

tar -jxvf alsa-driver-1.0.14.tar.bz2

```

4. Download realtek12.tar.gz found here:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104)

Login as guest (if you don't have an account).

5. Extract the files:
tar -zxvf realtek12.tar.gz

6. Put the extracted files (patch_realtek.c and hda_codec.c) in the pci/hda subdirectory of the alsa driver sources.

7. Configure, compile and install the driver, by going to the driver source directory and doing the following:
```

./configure
make
sudo make install

```

8. Add this line to e.g. the end of /etc/modprobe.d/alsa-base so the correct (fixed) model is used:
```

options snd-hda-intel model=toshiba

```

You can use e.g. pico to edit the file:
```

sudo pico /etc/modprobe.d/alsa-base

```

After adding the line, save with Ctrl-O + Enter and exit with Ctrl-X.

9. Restart the computer.

If you don't feel like restarting this should probably work to:
```

sudo /etc/init.d/alsasound stop
sudo modprobe -r snd-hda-intel
sudo modprobe snd-hda-intel

```

big thanks to your instruction, works perfect for me:P

---

