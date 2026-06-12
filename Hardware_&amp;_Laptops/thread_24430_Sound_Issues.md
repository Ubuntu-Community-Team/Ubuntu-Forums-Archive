---
title: "Sound Issues"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by Enkidu on 2005-04-06
I recently installed ubuntu 5.04 on my tecra 8100 laptop.  Everything worked fine except for the sound.  Alsa is even selecting to use the right driver: Yamaha DS-XG (YMF744), but whenever a sound should play the right speaker clicks and then the left speaker clicks.  Any ideas would be much appreciated.

Also, my university is blocking irc which would be a much needed resource because I don't have much experience with linux.  If anyone knows how to access the irc server in another manor that would also be appreciated.

---

### Post by coughcool on 2005-04-07
Just want to add a "me too" to this. I'm running hoary with no sound. :-? 

Tecra 8100

---

### Post by n2024 on 2005-04-08
Are you sure tou unmute your card?
type alsamixer and unmute master and pcm ! To do that :
move withe the arrow and press m to mute / unmute and up and down arrow to increase volume!

If it's not that, type :
lsmod | grep snd and post the result!

No idea about your irc problem

good luck and see tou soon!

Noel

---

### Post by Enkidu on 2005-04-09
They were already unmuted.  The results of lsmod | grep snd is as follows:

snd_ymfpci             58180  3
snd_ac97_codec         59268  1 snd_ymfpci
snd_pcm_oss            48296  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_ymfpci,snd_pcm_oss
snd_opl3_lib            9728  1 snd_ymfpci
snd_timer              23300  3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               9120  1 snd_opl3_lib
snd_page_alloc         11144  2 snd_ymfpci,snd_pcm
gameport                4736  1 snd_ymfpci
snd_mpu401_uart         7296  1 snd_ymfpci
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  2 snd_opl3_lib,snd_rawmidi
snd                    50660  13 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd

---

### Post by dbott67 on 2005-04-09
I'm also having issues with my sound card on a Toshiba Tecra 8000.  I was running Warty and had sound working after following these instructions:

```
Enabling Sound on Toshiba Tecra 8000 in Ubuntu Linux

1) Edit /etc/modutils/alsa-base

# ALSA Configuration.
alias snd-card-0 snd-opl3sa2

# some stuff for the OSS drivers
alias char-major-14 snd-pcm-oss
alias sound-slot-0 snd-card-0

# aliases for sound card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

2) Open terminal and type "sudo update-modules"

3) Edit /etc/modules

snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530 <--- its one long row!

4) Re-boot
```

I upgraded to Hoary last night and the sound card stopped working.   I searched around the forums but I couldn't find any clear-cut solution, so I backed up my existing 'alsa-base' file and renamed the 'alsa-base.dpkg-dist' to 'alsa-base'.

Here's what I get when I lsmod | grep snd:

```
dbott@ubuntu:~ $ sudo alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
dbott@ubuntu:~ $
dbott@ubuntu:~ $ lsmod | grep snd
snd_opl3_lib           10112  0
snd_hwdep               9220  1 snd_opl3_lib
snd_cs4231_lib         24832  0
snd_mpu401_uart         7168  0
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  2 snd_cs4231_lib,snd_pcm_oss
snd_timer              23300  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    50276  10 snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_cs4231_lib,snd_pcm

```

I also get a message during boot for the following device:

Yamaha OPL3-SA sound card not found or device busy [ok]

and during shutdown:

/etc/init.d/alsa: Warning 'alsactl restore' failed with message alsactrl... (message skipped by before I could finish jotting it down).

There are also a series of 'beeps' just as the gdm loads and as it shuts down (17 beeps or so).  There is a very brief error that flashes 'INVALID CARD NUMBER" as it beeps during the shutdown sequence.

Any help would be appreciated.

Thanks,
Dave

---

### Post by coughcool on 2005-04-10
[QUOTE=coughcool]Just want to add a "me too" to this. I'm running hoary with no sound. :-? 

Tecra 8100[/QUOTE]


Just want everyone to know that I just installed the Final Release of Hoary Hedgehog 5.04 and NOT the 5.04 (RC)  my sound works Great!

---

### Post by Enkidu on 2005-04-10
Whats the difference and how do I know which I have?

---

### Post by dbott67 on 2005-04-11
[QUOTE=coughcool]Just want everyone to know that I just installed the Final Release of Hoary Hedgehog 5.04 and NOT the 5.04 (RC)  my sound works Great![/QUOTE]

I'm also running the final release, not the RC.

Enkidu,

If you downloaded Hoary (or upgraded Warty) before April 8, you're probably running the RC version.  RC went "gold" on April 8, 2005.

On Friday night, I changed my sources.list file from the 'warty' repositories to 'hoary' and followed these instructions:  [Upgrade to Hoary from Warty](http://ubuntuforums.org/archive/index.php/t-24233.html) 

If you're not sure which version you have, you could always follow the above link to perform the upgrade.

-Dave

---

### Post by TheRealEdwin on 2005-04-11
I have the problem where I have no sound at all with any of the options available. Any suggestions?

---

### Post by coughcool on 2005-04-11
[QUOTE=coughcool]Just want everyone to know that I just installed the Final Release of Hoary Hedgehog 5.04 and NOT the 5.04 (RC)  my sound works Great![/QUOTE]


Well it was working great. After a reboot I now have the exact problem listed in the first post. Note: As far as I know nothing has changed from the install to the reboot.  Ubuntu had been runing for 2 days with no issues and working sound.

here is lsmod info

lsmod | grep snd
snd_ymfpci             56768  2
snd_ac97_codec         64608  1 snd_ymfpci
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           10112  1 snd_ymfpci
snd_timer              23300  3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               9220  1 snd_opl3_lib
snd_page_alloc          9604  2 snd_ymfpci,snd_pcm
gameport                4608  1 snd_ymfpci
snd_mpu401_uart         7168  1 snd_ymfpci
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd                    50276  11 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd

---

### Post by coughcool on 2005-04-11
[QUOTE=coughcool]Just want everyone to know that I just installed the Final Release of Hoary Hedgehog 5.04 and NOT the 5.04 (RC)  my sound works Great![/QUOTE]

That is until I rebooted and I've not managed to get it working like it was since.  :?

---

### Post by Lauwenmark on 2005-04-12
[QUOTE=dbott67]
I upgraded to Hoary last night and the sound card stopped working.   I searched around the forums but I couldn't find any clear-cut solution, so I backed up my existing 'alsa-base' file and renamed the 'alsa-base.dpkg-dist' to 'alsa-base'.
[/QUOTE]

I also have a Tecra 8000 and encountered the same problem.

It appears that when loading the module for the soundcard (snd-opl3sa2), modprobe doesn't take into account the options passed to the module. After some investigation, I found that the content of /etc/modprobe.d/alsa-base was the offender.

To solve the problem, I edited the following line of /etc/modprobe.d/alsa-base :

```

install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2

```

Into:

```

install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530 && /lib/alsa/modprobe-post-install snd-opl3sa2

```

And things then worked back as they should.
Maybe there is a "cleaner" way to correct this, but I hadn't yet time to investigate further.

Hope this helps !

---

### Post by jordz on 2005-04-13
Hey thx! I have a tecra 8000 too, and installed hoary and no sound. Im gonna try it out, but i think it works, i was searching for the dma/irq settings as well. Thx :)

---

### Post by coughcool on 2005-04-15
Lauwenmark,

I have a Tecra 8100 any way you can help me figure out what options I need to get my sound working consistently?

I've been able to fool it into working by doing some seemingly random things. Unfortunately as soon as I think I discover the root of the problem I find myself back to square one.

can you can point me in the right direction?

Thanks

---

### Post by amias on 2005-04-24
I followed the config instructions given for the tecra 8000 and i now have working sound. The only other thing i did was to add my user account to the audio group.

sudo usermod -G audio your_username

The /dev/dsp and /dev/dspW nodes belong to root:audio when they files are created. you will not be able to access the nodes as a normal user without adding your user account to the audio group. This will take effect at the next login.

Hoary seems a little slower on this laptop than warty did , still its very nice , thanks :)

---

### Post by Enkidu on 2005-04-26
I have tried every single thing in this thread and I still can't get sound to work!??!  Is there anything else it could be?

---

### Post by jliedeka on 2005-04-29
[QUOTE=Lauwenmark]I also have a Tecra 8000 and encountered the same problem.

It appears that when loading the module for the soundcard (snd-opl3sa2), modprobe doesn't take into account the options passed to the module. After some investigation, I found that the content of /etc/modprobe.d/alsa-base was the offender.

To solve the problem, I edited the following line of /etc/modprobe.d/alsa-base :

```

install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2

```

Into:

```

install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530 && /lib/alsa/modprobe-post-install snd-opl3sa2

```

And things then worked back as they should.
Maybe there is a "cleaner" way to correct this, but I hadn't yet time to investigate further.

Hope this helps ![/QUOTE]
 Where did you get those DMA/IRQ numbers?  I don't see anything interesting in dmesg.  This is what I see:

intel8x0_measure_ac97_clock: measured 49451 usecs
intel8x0: clocking to 48000
ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 9 (level, low) -> IRQ 9
PCI: Setting latency timer of device 0000:00:1f.6 to 64
MC'97 1 converters and GPIO not ready (0xff00)

The last line seems to be saying something useful but I don't know what it means.

     Jim

---

### Post by lucus on 2005-05-01
modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530


i have a toshiba tecra, and this is how i got my sound to work.
you might try a similar modprobe....
i was frustrated to all get out until i did this.

---

### Post by dninja on 2005-05-13
Has anyone managed to get a Tecra 8100 soundcard working yet with Ubuntu?

There are a few people saying that they got sound working but there has also been mentions of the Tecra 8000 which is a different sound system.

Everything I have read, even from the authors of the alsa drivers says that a 8100 won't work with alsa.

I've had gentoo running on on the 8100 with OSS but I can't get OSS running with Ubuntu Hoary. As other people have said, the app plays and thinks that it is putting out sound but it isn't.

PS The volume is turned up!

---

### Post by Enkidu on 2005-05-30
I have finally gotten sound to work on a tecra 8100, though the solution just leaves further questions.

The first thing to do is change /etc/modutils/alsa-base to this:

```

alias char-major-116 snd
alias snd-card-0 snd-card-ymfpci
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
options snd snd_major=116 snd_cards_limit=1 snd_device_mode=0660 snd_device_grid=17 snd_device_uid=0
post-install snd alsactl restore

``` 

*note that the last stop is not necessarily needed for different computer types*

Then you need to follow these steps (as taken from [KernelByHandHowto](http://www.ubuntulinux.org/wiki/KernelByHandHowto))

```


$ sudo -s

# apt-get install build-essential bin86 libncurses-dev

# apt-get install linux-tree-2.6.10
# cd /usr/src
# tar jxf linux-source-2.6.10.tar.bz2
# ln -s linux-source-2.6.10 linux

# cd /usr/src/linux
# cp /boot/config-* .config
# make oldconfig

# make

# make modules_install install


```  

*note that not all the steps on the webpage are needed*

I don't know if this will work with another version of the linux-tree.

The weird thing is that you don't have to run the new kernel, it just has to be compiled for the sound to work.  If anyone has further information on this then it would be appreciated.  Also, this should probably be reported someone so that someone looks into it, but i dont know where.

---

### Post by xy77 on 2005-06-15
I have a similar problem here with the intel corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01):
```

ACPI: PCI interrupt 0000:00:1f.6[B] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:1f.6 to 64
MC'97 1 converters and GPIO not ready (0xff00)

```

no sound so far

A few days ago the sound worked great and I cannot imagine having changed anything. This is a IBM Thinkpad T42p btw.

Hope anyone can help me.

- David (xy77)

PS: output of lsmod | grep snd:

```

snd_intel8x0m          18372  0
snd_intel8x0           32352  2
snd_ac97_codec         74144  2 snd_intel8x0m,snd_intel8x0
snd_pcm                94696  3 snd_intel8x0m,snd_intel8x0,snd_ac97_codec
snd_page_alloc          9732  3 snd_intel8x0m,snd_intel8x0,snd_pcm
snd_timer              25060  1 snd_pcm
snd_seq_device          8460  0
snd                    55012  10 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer,snd_seq_device
soundcore              10016  1 snd

```

content of /etc/asound.conf
```

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
# slave.pcm "dmixer"
slave.pcm "pcm.card0"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:1,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

```

---

### Post by mikelh on 2005-08-08
I could repeatedly manage to get distorted and undistored sound out of my Tecra 8100:

cold boot the Tecra --> sound gets distorted
then
suspend to RAM or DISK and resume: sound becomes chrystal clear and remains until
next cold boot.

I suspect something within the ymfpci driver with relation to ACPI resume,
maybe there is one additional setting that has not been done on cold boot / insmod ?

Any kernel hacker here ?

Mike

---

