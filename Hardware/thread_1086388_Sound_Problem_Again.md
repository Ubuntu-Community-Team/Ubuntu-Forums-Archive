---
title: "Sound Problem Again"
date: 2009-03-04
forum: Hardware
---

### Post by MacroLand on 2009-03-04
Hi All,

Although this has been posted several times, I still could not make the sound work on my HP dv4 1220us laptop. I am running 64 Bit Ubuntu 8.10. 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"


My aplay -l command gives the output:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

After running gksudo gedit /etc/modprobe.d/alsa-base 

I added options snd-hda-intel probe_mask=1
also tried  options snd-hda-intel enable_msi=1 

also I run gksudo gedit /etc/rc.local command to add modprobe hda... command.

I am dual booting with Windows Vista and the sound works in Vista. 

Also I have downloaded all updates from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and installed them.

It seems nothing has changed and I dont know what is going on..

Any help will greatly be appreciated,

Thanks

---

### Post by NaplesBill on 2009-03-04
I have an HP DV4-1155SE.  I was able to get the sound working with the following alsa-base config:

> alias snd-card-0 snd-hda-intel 
alias sound-slot-0 snd-hda-intel 
options snd-hda-intel model=dell-m4-1

I also had to set the default mixer track device by selecting PCM.  I had to do the same thing for the sound icon on the taskbar.

---

### Post by MacroLand on 2009-03-04
Hi NaplesBill,

Thanks a lot. It worked and now I am listening music :)

I run gksudo gedit /etc/modprobe.d/alsa-base and changed the last line to
options snd-hda-intel model=dell-m4-1

and then reboot the machine. It simply worked :)

---

### Post by jaminux on 2009-03-04
HP is definitely the wrong choice to work with Ubuntu without a hassle. I have had problems with sound as well.

Maybe we are better off all buying Dell in future. ^^

---

### Post by NaplesBill on 2009-03-04
I would rather deal with the couple minor tweaks on my HP than to even touch a Dell.  

The sound issue has happened to me on so many machines and distros of Linux.  It's no big deal to me.  It is working flawlessly otherwise.  All my media buttons work and the built-in bluetooth and wireless worked without any additional effort.

I did install the official ATI driver and it's working at my native resolution with 32-bit color.  Honestly, I couldn't be happier.

---

### Post by MacroLand on 2009-03-10
I have not used Dell so far; however, my first laptop was an HP and after then I continued with HP. The sound problem could become an issue but it has been resolved with the keyword NaplesBill had posted. The media buttons are working and also I installed the ATI drivers to be able to activate the Compiz futures and so far I am happy with my Ubuntu and HP.

---

