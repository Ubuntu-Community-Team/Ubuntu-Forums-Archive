---
title: "Shuttle mainboard sound driver information"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by st1100pilot on 2006-02-15
Hello all,

I have a shuttle mainboard, I am pretty sure that this is the one: [http://http://www.ajump.ca/ajump/product.asp?dept_id=5160&pf_id=3040122]("http://http://www.ajump.ca/ajump/product.asp?dept_id=5160&pf_id=3040122")

The sound works, but has a really strange issue. There is a buzzing in the sound that comes and goes. The majority of the time it is there, I leave the sound pretty much turned down very low so I don't have to deal with the sound. However, every once-in-a-while, the sound clears up for one, or two tracks, and sounds great, then the buzz comes back when the next track starts. Go figure.

Anyway, I am going to install a different sound driver, and need to know which one to  install. On the mainboard drivers CD, it has Linux drivers, I just don't know which one to use. Linux distros listed on the CD are:

240
2216
Caldera
happy
Mandrake
RedFlag
RedHat

Which one is closest to Ubuntu? I'm not looking forward to re-installing the driver, and want to make sure I install the closest one.

Thanks

---

### Post by Haegin on 2006-02-16
OK, dont bother with drivers on the CD. You will need "snd-cmipci".

First try entering this in a terminal:
```

sudo modprobe snd-cmipci

```

If that works you just add it to the modules file so it is loaded on startup.
1. Open the modules file in gedit (if you only have console then replace gedit with nano).
```

sudo gedit /etc/modules

```
2. add "snd-cmipci" to the end (with no quotes)
3. Save it (Ctrl + O in nano) and close it (Ctrl + X in nano)
4. Reboot and hope it fixes the problem.

I haven't had much experience with installing drivers (apart from compiling alsa to support my audigy value) but this should work (I think - please say if it doesn't). If the modprobe step fails then you will need to compile alsa with the new driver. It can be a bit daunting but it is easy enough when you have instructions. The following is adapted from [here]("http://ubuntuforums.org/showthread.php?t=21211").

Install the linux-headers package that suits your kernel. I am running kernel 2.6.10-5-386 ("uname -r" can help here)

sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10

cd /usr/src
sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9.tar.bz2)
tar xvjf alsa-driver-1.0.8.tar.bz2
cd alsa-driver-1.0.8
sudo ./configure --with-cards=cmipci --with-sequencer=yes
sudo make
sudo make install

sudo nano /etc/modules
add in

snd-cmipci

-----------------------------------------------------
Edit: Added sudo to the modprobe command.

---

### Post by st1100pilot on 2006-02-16
What does this do? Does it tell Ubuntu to try harder to find the right driver? 

I searched the forums with a couple of different queries, and didn't find anybody else describing a similar problem.

Thanks for the reply, I'll try it when I get home this evening.

---

### Post by Haegin on 2006-02-17
This tells ubuntu to load the correct driver when you turn the pc on. I guess there maybe other steps needed to tell it which driver to use but hopefully it will pick up the new driver and work. I found the driver by looking at that website you mentioned, looking at the onboard sound chip and looking it up on the alsa website to find the driver.

Tell me if it works or complain if you have problems

---

### Post by st1100pilot on 2006-02-19
Ok, sorry about the delay. Here is the output from the modprobe command and another command that I ran:

st1100pilot@UbuntuLinux:~$ lspci -v|grep audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 30)
st1100pilot@UbuntuLinux:~$ modprobe snd-cmipci
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.12-10-386/kernel/sound/core/snd-hwdep.ko): Operation not permitted
WARNING: Error inserting snd_opl3_lib (/lib/modules/2.6.12-10-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko): Operation not permitted
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.12-10-386/kernel/sound/core/snd-hwdep.ko): Operation not permitted
WARNING: Error inserting snd_opl3_lib (/lib/modules/2.6.12-10-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko): Operation not permitted
FATAL: Error inserting snd_cmipci (/lib/modules/2.6.12-10-386/kernel/sound/pci/snd-cmipci.ko): Operation not permitted
FATAL: Error running install command for snd_cmipci
st1100pilot@UbuntuLinux:~$


My BIOS says I have VIA-3058 AC97 audio, but in sound prefs it lists VIA 8233 sound and MPU 401 UART as my options. 

I bought a SB Live 24 sound card, and it didn't work so I removed it(found out it was the cheapie $30 version). So I will be continuing to try to get this onboard one working great. Like I stated above, it works, I can hear sound and sometimes it works flawlessly, but on the next track playing (or system sound) it goes right back to being buzzy.

Thanks!

---

### Post by Haegin on 2006-02-19
Sorry - you need to use "sudo modprobe snd-cmipci" instead. (If you ever get a permissions error and you know the command is safe then just add sudo to the beginning to try it as root).

It looks like it will work, if it does then continue with adding it to the /etc/modules file.
1. Open the modules file in gedit (if you only have console then replace gedit with nano).
```
sudo gedit /etc/modules
```
2. Add "snd-cmipci" to the end (with no quotes)
3. Save it (Ctrl + O in nano) and close it (Ctrl + X in nano)
4. Reboot and hope it fixes the problem.

---

### Post by st1100pilot on 2006-02-19
Thanks so much for your help. I tried all of those tips, and a bunch of other things I found, but no luck - still buzzy.

Sooooooo.... I cheated. I remembered an old soundcard in another computer I own (running DSL Linux) that I can't get the sound working on. I suspected that it worked, but that DSL couldn't configure it right. So I yanked it, and put it in this machine, and voila! Nice, clean sound. It is an older card, an Ensoniq, so I figure that the drivers have long since been worked out.

THanks again for your help. It is people like yourself that will make Ubuntu the distro that finally goes mainstream.

See you on the forums

---

