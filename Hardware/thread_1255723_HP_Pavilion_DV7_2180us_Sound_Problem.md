---
title: "HP Pavilion DV7 2180us Sound Problem"
date: 2009-09-01
forum: Hardware
---

### Post by alperyilmaz on 2009-09-01
Hi,

I just installed Ubuntu 9.04 to HP Pavilion DV7 2180us model laptop. The graphics card is ATI Radeon HD 4650 and is working fine. However I couldn't make the sound to work. I tried the method mentioned in couple posts, adding "options snd-hda-intel enable_msi=1" in etc/modprobe.d/alsa-base.conf file.

Does anybody fixed sound issues with similar laptop before?

Update: I see the following line appearing in /var/log/jockey.log file:
/var/log/jockey.log:2009-09-01 17:43:07,059 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}


Update2: I installed newest alsa drivers, (1.0.21) and i start hearing sounds. however, the sound is only coming from subwoofer. main speakers and headphones are still silent..

Update3: For the sake of googlers to find this page easily, I'm adding my configuration information:
Audio hardware: 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

Audio codecs:
Codec: IDT 92HD75B3X5
Codec: LSI ID 1040

thanks,

---

### Post by gn0st1c on 2009-09-28
i have a similar notebook (dv7-2133et) and i had no sound too, here is my sound card info;

```
gnostic@GnoStiC-dv7:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

```

```
gnostic@GnoStiC-dv7:~$ cat /proc/asound/card0/codec#* | grep -i codec
Codec: IDT 92HD75B3X5

```

what i did to get sound was;

```
wget -c ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
wget -c ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.21.tar.bz2
wget -c ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21.tar.bz2
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

```

up to here, as you can see there is nothing special.. now we have to add our sound card model to alsa-base.conf based on codec info we have BUT there is no model listed for our card in alsa configuration guide; [http://paste.ubuntu.com/238572/](http://paste.ubuntu.com/238572/) 

so i picked the nearest number which is STAC92HD71B* :)
```

	STAC92HD71B*
	  ref		Reference board
	  dell-m4-1	Dell desktops
	  dell-m4-2	Dell desktops

	STAC92HD73*
	  ref		Reference board
	  dell-m6	Dell desktops

```

adding the following line to /etc/modprobe.d/alsa-base.conf solved my no sound problem, i may work for you too.. ***dell-m6*** would probably work but i had sound with ***dell-m4-2*** so i didn't bother to test..

```
options snd-hda-intel model=dell-m4-2
```

---

### Post by simon_ives on 2009-09-28
Confirmed that the above method fixes sound output on a HP Pavilion dv7 2109TX.

---

### Post by alperyilmaz on 2009-09-29
when you run the following, are you able to hear sound from all the channels or just left-right channels?

speaker-test -D plug:surround51 -c 6 -l 1 -t wav

I wonder the answer since there's subwoofer underneath the laptop and there's no sound coming from it with the above solution. When I was trying to fix it before, all the sound (both left and right) was coming from subwoofer. So, it should be accessible..

---

### Post by gn0st1c on 2009-09-29
i'll try that when i'm home, meanwhile you can try the following;

```

options snd-hda-intel model=hp-dv5
OR
options snd-hda-intel model=hp-hdx

```

```

STAC92HD71B*
============
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  hp-dv4-1222nr	HP dv4-1222nr (with LED support)

STAC92HD73*
===========
  no-jd		BIOS setup but without jack-detection
  intel		Intel DG45* mobos
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  alienware	Alienware M17x

```

---

### Post by mata07 on 2009-09-30
Confirmed that the above method fixes sound output on a HP Pavilion dv7 2160eg
used, 

options snd-hda-intel model=dell-m4-2
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5

thanks.

---

### Post by gmp34 on 2009-10-25
> **mata07 said:**
> Confirmed that the above method fixes sound output on a HP Pavilion dv7 2160eg
used, 

options snd-hda-intel model=dell-m4-2
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5

thanks.

All the above fixed as well my sound problem on HP DV7-2138sf

Many Thanks from Montpellier France

---

### Post by alperyilmaz on 2009-10-25
Hi everybody.. thanks for the replies, can you include in your reply that if the subwoofer/LFE channel works or not with the option you chose? Of course, if you have subwoofer..
run the follwing
speaker-test -D plug:surround51 -c 6 -l 1 -t wav

and report which channels work for you.

In my case, below channels work only:
0 - Front Left
1 - Front Right

---

### Post by hemanngosser on 2009-10-26
only left and right channel works for me and the subwoofer does not...
i've tried:
options snd-hda-intel model=dell-m4-2
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5
but no luck.
i have an HP Pavilion DV7 1190eo and i'm running the ubuntu 9.10 beta

can someone help me? :confused:

---

### Post by modsaid on 2009-10-28
> **gn0st1c said:**
> i have a similar notebook (dv7-2133et) and i had no sound too, here is my sound card info;

```
gnostic@GnoStiC-dv7:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

```

```
gnostic@GnoStiC-dv7:~$ cat /proc/asound/card0/codec#* | grep -i codec
Codec: IDT 92HD75B3X5

```

what i did to get sound was;

```
wget -c ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
wget -c ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.21.tar.bz2
wget -c ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21.tar.bz2
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

```

up to here, as you can see there is nothing special.. now we have to add our sound card model to alsa-base.conf based on codec info we have BUT there is no model listed for our card in alsa configuration guide; [http://paste.ubuntu.com/238572/](http://paste.ubuntu.com/238572/) 

so i picked the nearest number which is STAC92HD71B* :)
```

	STAC92HD71B*
	  ref		Reference board
	  dell-m4-1	Dell desktops
	  dell-m4-2	Dell desktops

	STAC92HD73*
	  ref		Reference board
	  dell-m6	Dell desktops

```

adding the following line to /etc/modprobe.d/alsa-base.conf solved my no sound problem, i may work for you too.. ***dell-m6*** would probably work but i had sound with ***dell-m4-2*** so i didn't bother to test..

```
options snd-hda-intel model=dell-m4-2
```


I confirm that this worked perfectly on my hp dv6 1280us as well.

I added 

```

  options snd-hda-intel enable_msi=1
  options snd-hda-intel model=dell-m4-2

```

to my /etc/modprobe.d/alsa-base.conf

Thanks gn0st1c

---

### Post by alperyilmaz on 2009-11-01
Hmm, that's interesting.. I'm testing Karmic Koala and sound is not behaving same even I do the necessary changes in /etc/modprobe.d/alsa-base.conf.

There's sound but insertingly the headphone in the jack does not mute the laptop's speakers..

Any ideas?

---

### Post by bushwacker on 2009-11-05
I have a Pavilion DV6 with the IDT high def audio codec. I had tons of trouble getting the sound to work in 9.10, but I was able to do it by doing the following steps:

Recompile sound driver module at the latest version, then edited /etc/modprobe.d/alsa-base.conf as shown on this forum. I then had to change the output sound controller to IDT Analog Audio instead of the HDMI digital sound output controller. The sound volume then had to be increased above 100%. Prior to doing this, you couldn't raise the sound volume past 0.00 dB no matter what you tried to do. Redoing the drivers and configs AND selecting the audio controller in that exact order fixed the problem and let me set a positive volume. Out of the box, 9.10 had no driver conflicts, and media players worked, but there was no actual sound through the OS seemed to belive everything was fine and dandy. 

Still no idea *why* the sound only works when fixed in this order, only that it does. Any ideas as to why?

---

### Post by alperyilmaz on 2009-11-09
I just had chance to test the microphone and unfortunately it does not work. So, it would be nice if you can add in your replies that mic works or not.
We need to find the best option for "options snd-hda-intel model=" so that both speakers and mic works.

Best way to test the mic is, go to Applications -> Sound & Video -> Sound Recorder.

---

### Post by Wallynm on 2012-03-21
Hey guys, i'm using ubuntu 11.10 with dv7... Don't know what serie it is but i wanna to thank you because edit the alsa conf file has solved my problem!!!

When i was pluggin my head phone, it wasnt closing the front sound from notebook, and both of them was with sound, now everything is fine!

Thanks!!!

Just 4 refference, i used these lines on my file:

options snd-hda-intel model=dell-m4-2
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-dv5

Cya!

---

### Post by Sxynerd on 2012-04-11
add this line

options snd-hda-intel model=ref

To this file :
 
 
/etc/modprobe.d/alsa-base.conf


sudo gedit /etc/modprobe.d/alsa-base.conf

---

