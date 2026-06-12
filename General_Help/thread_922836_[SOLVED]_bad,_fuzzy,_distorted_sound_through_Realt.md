---
title: "[SOLVED] bad, fuzzy, distorted sound through Realtek ALC662"
date: 2008-09-17
forum: General Help
---

### Post by rudy.elgato on 2008-09-17
Hi,

I've just put together a new system running Ubuntu 8.04.1 on an ECS Geforce7050M-M motherboard and AMD Athlon LE-1620 processor (the $59.99 combo from Fry's was impossible to pass up).  The system installs and starts up perfectly.  But, as soon as I install the NVidia proprietary drivers my sound becomes very bad, fuzzy, staticy sounding.  This will happen whether I update the NVidia driver using EnvyNG or going through System->Admininstration->Hardware Drivers. 

So, if I don't enable the NVidia proprietary drivers my sound is great, but my video is stuck in 800x600.  As soon as I update the NVidia drivers, my video goes to the correct resolution to fill my 22" monitor, but my sound sucks.  

I've been poking around all day trying to find the right "fix", but I haven't come across it yet.  Any ideas or help would be tremendously appreciated.

Thanks...

---

### Post by rudy.elgato on 2008-09-18
Anyone, any ideas?  I guess I do not understand why updating to the nvidia video drivers would cause my sound to become distorted.  Are there audio drivers installed as well?

---

### Post by TheLions on 2008-09-18
copy this in your browser t download Realtek drivers from ther page: [ftp://202.65.194.212/pc/audio/LinuxPkg_5.07.tar.bz2](ftp://202.65.194.212/pc/audio/LinuxPkg_5.07.tar.bz2) or go to [http://www.realtek.com.tw/](http://www.realtek.com.tw/) or from here [http://uploaded.to/?id=e64zzn](http://uploaded.to/?id=e64zzn)

the unpack it,
type 
```
cd where/drivers/are
```
```
./install
```

---

### Post by rudy.elgato on 2008-09-18
Thanks...  I tried that yesterday.  I had to install the "curses" library, and then the "gettext" package to get that to build.  It eventually did build cleanly, and I presume the 'install' installed all that was built into their proper locations, but my audio was still distorted after I reboot my box.

Is there some additional step needed after the 'install'?

---

### Post by rudy.elgato on 2008-09-19
TheLions, I really do appreciate your information, but building the driver directly from Realtek has not cleared up my buzzy sound problem.  Here's what I've done:

I've downloaded and extracted [ftp://202.65.194.212/pc/audio/LinuxPkg_5.07.tar.bz2](ftp://202.65.194.212/pc/audio/LinuxPkg_5.07.tar.bz2), installed the required curses and gettext packages, and ran the install (cd'ed into the realtek directory and 'sudo ./install').  That build ran cleanly without any errors, and then the last step in the build process runs the 'alsaconf' binary that the build generates.  

I then ran 'alsaconf', which produces a string of several popup windows that speak of detecting, testing, and configuring for my sound card.  It appears to find my onboard sound and finishes cleanly basically saying all is well.  At this point I go to the saxaphone ogg file in the installed ./Examples directory, hover over the file and it starts playing and still sounds all buzzy with the still noticiable static, exactly as things were before building the LinuxPkg_5.07.tar.bz2.

I then reboot the system, go back to the saxaphone ogg in ./Examples, and still get the buzzy, static sounding playback.  

So, either I'm still missing a step when I build the Realtek drivers, or building and installing the drivers directly does not address my problem.

Anyone, any other ideas?

---

### Post by TheLions on 2008-09-19
it seems that new drivers didn,t solve your problem...

try lowering PCM volume at 75% in sound mixer, that solved my bad sound

if that doesn't help try this guide:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

also try here:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by rudy.elgato on 2008-09-20
I'll have a closer look at those 2 threads.  Thanks...

Something I'm wondering about with the build I ran, I captured the output of the build process and notice that it builds a snd-hda-intel.ko and copies/installs this new *.ko into 

/lib/modules/2.6.24-19-generic/kernel/sound/pci/hda/

but when I run 'modprobe -l |grep snd-hda-intel' it finds the snd-kda-inte.ko from this directory:

/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/

Shouldn't the build I ran have installed what it generated into the location that 'modprobe' returns?

---

### Post by rudy.elgato on 2008-09-22
Anyone?  All you Ubuntu diehards out there and the only friendly offer of help and support comes from TheLions?  

Come on, someone has got to have some ideas, something for me to try.  I've tried updating my ./alsa-base file with various "options snd-hda-intel model=XXXX" settings, I've rebuilt, installed and configured the driver from Realtek.  What else might I be missing?  

Am I the only Ubuntu user who gets buzzing, fuzzy, hissing audio after installing the nvidia proprietary drivers?  I mean, my audio is perfect immediately after a fresh install (which I've run many, many times trying to figure out what's going here...).  Then as soon as I go to the nvidia driver, installed either through envy or System->Admininstration->Hardware Drivers, my sound goes to crap.  It's still audible, just with a very noticible hiss during any audio playback.  I've played with what I can play with through volume control and through alsamixer.

Technically, I'm not a complete idiot and am able and willing to try different things to get this fixed.  I'm just frustrated because I've the whole flippin weekend going through this forum, going though every place google will take me, and I'm still stuck with crappy audio.  Hell, I even sent email directly to Alberto Milone, who's name is all over EnvyNG, and never even heard back.

Guess I'll try installing a cheap sound card and see if that will work, but geez folks, the lack of ideas, or offers to help here, is EXTREMELY disappointing...  

I might just have to reconsider my move to Ubuntu if this is the sort of support a person can expect for a fundamental part of a system, good sound.  I guess if it works for you out of the box, you're golden, but if you run into any kind of problem, too bad, you're on your own to try to figure it out...

---

### Post by TheLions on 2008-09-22
here is some ideas if you wanna give it a try:

1. install newest NVIDIA drivers: [http://ubuntuforums.org/showpost.php?p=4773886&postcount=16](http://ubuntuforums.org/showpost.php?p=4773886&postcount=16)

2. connect you speakers on front speakers if you havent already

3. try sound in livecd

4 try beta Intrepid Ibex (U8.10)

5.read somemore FIXiTy0uSeLF tutorial: [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) ; [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

6. try older/newer kernel

---

### Post by rudy.elgato on 2008-09-29
Well, I tried tons of things, but nothing would clear up the fuzzy, buzzy, hissing sound that would come through the audio everytime I went to the propietary NVIDIA driver.  

So, broke down and bought a $10.00 Dynex DX-SC51 off of eBay, plugged it in, and I've got nice, clean, clear sound now.  

Probably pretty dumb of me to waste so much time trying to get things to work and let myself get so frustrated over it, but I just hate having to go with a workaround to something that should just plain work.  Don't know, guess maybe there's just some fundamental problem with the NVIDIA GeForce 7050 chipset (NVIDIA GeForce 7050 PV + nForce 630a) and their drivers.  Who knows...

Anyhow, to TheLions, I've left a formal "Thanks" for you here on the forums, and I really do appreciate you taking the time to give my problem some thought.  It's people like you that will keep Ubuntu in a positive light and will make it a success...

---

### Post by TheLions on 2008-09-29
You are welcome!!!

by the way could you mark this thread "Solved"?

---

### Post by jondiced on 2008-11-05
hey rudy.elgato, i have the same exact problem with my nForce 720a chipset and onboard ALC662 soundcard. not being the handiest user around and still slightly terrified of ubuntu, this post isn't worth much more than commiseration. if only i could find the turtle beach sound card i use on my laptop, maybe i could get that to work...

thanks for all your help TheLion.

---

### Post by tommynz1975 on 2009-09-30
hi lowering the pcm in the sound mixer fixed the issue....  from 6.06--->> 8.10 distored sound on compaq c500.  .. Many thank

---

