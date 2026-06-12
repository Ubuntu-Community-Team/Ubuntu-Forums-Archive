---
title: "Speaker issues HP dv7-3085dx laptop"
date: 2009-11-18
forum: Hardware
---

### Post by Veratyr9 on 2009-11-18
I just picked up an hp dv7-3085dx laptop, trashed windows and put on ubuntu studio 9.10

Issue that I'm having is that I'm getting sound oout of the subwoofer (yes this laptop has a built in sub, go figure) but not out of the actual speakers.

Headphone jacks do not work (there are 2 of them)

Don't know where to start.  help?


found these lines in lspci if it helps

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)

---

### Post by pigs_eye_bozo on 2009-11-20
I am new to linux so I don't know if this is right/helpfull, but I did the following with some success.  The problem I had was it only worked when I did it in my home directory.  I did not like the mess it left in the home folder so I  reinstalled Ubuntu and tried to follow the same instructions in the /ect/modprobe.d directory (i.e. where my audio drivers live) but it did not work.  Not sure why.
 

 These instructions are from: [http://ubuntuforums.org/showthread.php?p=7531391](http://ubuntuforums.org/showthread.php?p=7531391)
 

 gnostic@GnoStiC-dv7:~$ cat /proc/asound/card0/codec#* | grep -i codec
Codec: IDT 92HD75B3X5


what i did to get sound was;

wget -c [ftp://ftp.alsa-project.org/pub/drive...1.0.21.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2")
wget -c [ftp://ftp.alsa-project.org/pub/utils...1.0.21.tar.bz2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.21.tar.bz2")
wget -c [ftp://ftp.alsa-project.org/pub/lib/a...1.0.21.tar.bz2]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21.tar.bz2")
tar xvf alsa-driver-1.0.21.tar.bz2 
tar xvf alsa-lib-1.0.21.tar.bz2
tar xvf alsa-utils-1.0.21.tar.bz2 
cd alsa-driver-1.0.21/
./configure --with-cards=hda-intel
make
sudo make install
cd ..

cd alsa-lib-1.0.21/
./configure 
make
sudo make install
cd ..
cd alsa-utils-1.0.21/
./configure 
make
sudo make install


up to here, as you can see there is nothing special.. now we have to add our sound card model to alsa-base.conf based on codec info we have BUT there is no model listed for our card in alsa configuration guide; [http://paste.ubuntu.com/238572/](http://paste.ubuntu.com/238572/) 

so i picked the nearest number which is STAC92HD71B* :smile:

STAC92HD71B*
ref Reference board
dell-m4-1 Dell desktops
dell-m4-2 Dell desktops

STAC92HD73*
ref Reference board
dell-m6 Dell desktops


adding the following line to /etc/modprobe.d/alsa-base.conf solved my no sound problem, i may work for you too.. dell-m6 would probably work but i had sound with dell-m4-2 so i didn't bother to test..

options snd-hda-intel model=dell-m4-2
 

 I also found instructions at the ALSA sight for installing updated drivers but have not yet gotten them installed.  The following link is found at: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
 >>Documentation >>Unofficial ALSA wiki so I guess follow at your own risk.
 

 [http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install)

---

### Post by Qaranthir on 2009-11-24
I have a similar laptop (HP DV7-3080ed) with the same soundchip.
To be honest: I tried several things and I don't know which one works....

I added the following lines at /etc/modprobe.d/alsabase.conf:

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4
options snd-hda-intel enable_msi=1

And I installed linux-backport-modules-karmic and linux-backport-modules-alsa-karmic-generic.
At least, the sound improved considerably... (Not a bass-toned sound anymore)

Still, the headphone jacks don't function.

Besides the audioproblems, the BIOS gives warnings at every startup and reboot about overheat. It probably has to do with the core i7 720QM processor, which still isn't support by lm_sensors.

---

### Post by Veratyr9 on 2009-12-01
> **Qaranthir said:**
> I have a similar laptop (HP DV7-3080ed) with the same soundchip.
To be honest: I tried several things and I don't know which one works....

I added the following lines at /etc/modprobe.d/alsabase.conf:

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4
options snd-hda-intel enable_msi=1

And I installed linux-backport-modules-karmic and linux-backport-modules-alsa-karmic-generic.
At least, the sound improved considerably... (Not a bass-toned sound anymore)

Still, the headphone jacks don't function.

Besides the audioproblems, the BIOS gives warnings at every startup and reboot about overheat. It probably has to do with the core i7 720QM processor, which still isn't support by lm_sensors.


This worked! thanks!  though the backport didnt do much i dont think.   yea i haev the same problem with "overheating" i figured it was something with the OS not reporting temps or something.  its not overheating

---

### Post by mars_ninja on 2009-12-05
> **Qaranthir said:**
> I have a similar laptop (HP DV7-3080ed) with the same soundchip.
To be honest: I tried several things and I don't know which one works....

I added the following lines at /etc/modprobe.d/alsabase.conf:

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4
options snd-hda-intel enable_msi=1

And I installed linux-backport-modules-karmic and linux-backport-modules-alsa-karmic-generic.
At least, the sound improved considerably... (Not a bass-toned sound anymore)

Still, the headphone jacks don't function.

Besides the audioproblems, the BIOS gives warnings at every startup and reboot about overheat. It probably has to do with the core i7 720QM processor, which still isn't support by lm_sensors.

Actually if you just use:

options snd-hda-intel model=hp-m4

That works for me. (Same laptop specs)

Jason

---

### Post by mars_ninja on 2009-12-05
Anyone figure out the headphone jack problem?

---

### Post by wolfgangpauli on 2009-12-12
Hi,

I had the same problem on a pavilion dv8, only the rear speakers (e.g. sub-woofer) were working. 

All I had to do (in karmic) was as mentioned before was append the following to /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=hp-m4

(note: there is another entry that I don't think I added/touched: 

# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

)

Anyway, I am glad that the headphone jack is working also, just as the microphone (skype). I do have to manually mute the "speaker" in kmix to only get sound on the headphones, and had to check "Capture" on the capture device to get microphone to work.

Thanks!!!

---

### Post by Arctother on 2010-01-06
Wolfgang,

I have the same laptop as you, and had the same issue - except changing my alsa.conf file fixed the speakers but not the microphone.

What do you mean by selecting capture under capture device ?

I tried removing pulseaudio, that did not solve the problem, it just made several other things not work ! 

Thanks
-Arc

---

