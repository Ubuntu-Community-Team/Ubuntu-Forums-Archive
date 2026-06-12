---
title: "[SOLVED] Need help with Audio driver"
date: 2008-10-03
forum: Hardware
---

### Post by amiller2571 on 2008-10-03
Hello, I am trying to get my audio drivers working.

I have to audio devices 

1. Creative Sound Blaster F-Xi Platinum
2. Asus Motherboard PW5 HD Deluxe with built in audio.

I really would like to get the Sound Blaster working but, I can settle with the Motherboard Audio.

Could anyone help me get one of them working?


I am using 8.04 Hardy, Kernel 2.6.24-19-generic, GNOME 2.22.3

---

### Post by mindoms on 2008-10-03
please run these commands in a terminal and post the output.
This will give us some information to help you
```

lsb_release -d
uname -r
cat /proc/asound/cards
aplay -l
aplay /usr/share/sounds/startup.wav
lspci | grep -i audio
ps -C esd
ps -C arts
grep "^audio" /etc/group | grep "$USER" | wc -l
lsmod | grep "snd"
head -n 3 /proc/asound/card0/codec#0
head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs
asoundconf list
cat ~/.asoundrc
cat ~/.asoundrc.asoundconf 

```
(from [http://wiki.ubuntuusers.de/Soundprobleme/Audio-Fehler-Beschreibung?highlight=soundproblem](http://wiki.ubuntuusers.de/Soundprobleme/Audio-Fehler-Beschreibung?highlight=soundproblem))

---

### Post by amiller2571 on 2008-10-03
amiller@amiller-asus:~$ lsb_release -d
Description:	Ubuntu 8.04.1

amiller@amiller-asus:~$ uname -r
2.6.24-19-generic

amiller@amiller-asus:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory

amiller@amiller-asus:~$ aplay -l
aplay: device_list:205: no soundcards found...

amiller@amiller-asus:~$ aplay /usr/share/sounds/startup.wav
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such file or directory

amiller@amiller-asus:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
01:01.0 Multimedia audio controller: Creative Labs SB X-Fi

amiller@amiller-asus:~$ ps -C esd
  PID TTY          TIME CMD
 7413 ?        00:00:00 esd

amiller@amiller-asus:~$ ps -C arts
  PID TTY          TIME CMD

amiller@amiller-asus:~$ grep "^audio" /etc/group | grep "$USER" | wc -l
1

amiller@amiller-asus:~$ lsmod | grep "snd"
snd_page_alloc         11400  0 

amiller@amiller-asus:~$ head -n 3 /proc/asound/card0/codec#0
head: cannot open `/proc/asound/card0/codec#0' for reading: No such file or directory

amiller@amiller-asus:~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
head: cannot open `/proc/asound/card0/codec97#0/ac97#0-0' for reading: No such file or directory

amiller@amiller-asus:~$ head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs
head: cannot open `/proc/asound/card0/codec97#0/ac97#0-0+regs' for reading: No such file or directory

amiller@amiller-asus:~$ asoundconf list

amiller@amiller-asus:~$ asoundconf list

amiller@amiller-asus:~$ cat ~/.asoundrc
cat: /home/amiller/.asoundrc: No such file or directory

amiller@amiller-asus:~$ cat ~/.asoundrc.asoundconf
cat: /home/amiller/.asoundrc.asoundconf: No such file or directory

amiller@amiller-asus:~$

---

### Post by mindoms on 2008-10-03
well. It looks bad for Your soundblaster, as this site says, this card is not supported yet in linux: (search for: Sound Blaster X-Fi)
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

but maybe we get your onboard intel chip up and running.
try, in a terminal:
```

sudo modprobe snd-hda-intel

```
please post output, if any.

test if sound works.

if this works, then run:
```

sudo gedit

```
add 
hda-intel
to the end of the document.

Found all that information on:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

hth, stefan

---

### Post by amiller2571 on 2008-10-03
amiller@amiller-asus:~$ sudo modprobe snd-hda-intel
FATAL: Error inserting snd (/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
amiller@amiller-asus:~$


That is what I got for the first code

---

### Post by amiller2571 on 2008-10-03
A nother then I can do till Creative comes out with a working Driver is get a cheap sound card that is knowen to work with Ubuntu. If you know of any that is really cheap and that would be a good temporary setup let me know.

I mean cheap as in under 30$

I found this one- [http://www.newegg.com/Product/Product.aspx?Item=N82E16829130001](http://www.newegg.com/Product/Product.aspx?Item=N82E16829130001)
the reviews say it works right out of the box on Ubuntu.
you think this would be a good temporary sound card?

---

### Post by mindoms on 2008-10-03
I really can not say when those SB drivers will be available. I just have no idea. tomorrow or in 3 years. You courd try to find some info on the internet

You can find supported Hardware at
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

I guess most cheap PCI cards should work.
I have a soundblaster live 5.1, and an onboard CMI8738. both work fine.

but i haven't given up so far :)

if you havent rebooted since the last command (modprobe)
then please post the output to.
otherwise run that modprobe thing from my last post again and then do the following.
```

dmesg | tail -n25

```
 and then try 
```

sudo modprobe intel8x0

```
post any output again, and try the sound output.

make sure the speaker are connected to the onboard-soundcard ;)

---

### Post by amiller2571 on 2008-10-03
Sorry I have not replied I had to run out I will be back to my house later tonight and I will try what you said.

---

### Post by markbuntu on 2008-10-03
If you are having problems getting your Creative X-FI card to work you need to use OSS4 or recompile your kernel with a patched X-Fi driver: 

To get OSS4:

[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

To recompile your kernel and apply the patch (take extreme care doing this, recompiling a kernel is serious business and can seriously break your system,  do not do this unless you are absolutely sure you know what you are doing):

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

I am not sure if these work with the X-FI Platinum, you should ask in the threads before trying them.

---

### Post by amiller2571 on 2008-10-04
amiller@amiller-asus:~$ dmesg | tail -n25
[ 9858.517001] snd_hda_intel: Unknown symbol snd_card_register
[ 9858.517031] snd_hda_intel: Unknown symbol snd_card_free
[ 9858.517061] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 9858.517090] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 9858.517187] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 9858.517226] snd_hda_intel: Unknown symbol snd_verbose_printk
[ 9858.517281] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 9858.517344] snd_hda_intel: Unknown symbol snd_component_add
[ 9858.517382] snd_hda_intel: Unknown symbol snd_card_new
[ 9858.517411] snd_hda_intel: Unknown symbol snd_iprintf
[ 9858.517444] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 9858.517474] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[ 9858.517513] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 9858.517546] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 9858.517576] snd_hda_intel: Unknown symbol snd_hwdep_new
[ 9858.517618] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 9858.517656] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[ 9858.517694] snd_hda_intel: Unknown symbol snd_device_new
[ 9858.517739] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 9858.517780] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 9858.517810] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 9858.517882] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[ 9858.517951] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 9858.517980] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[ 9858.518029] snd_hda_intel: Unknown symbol snd_pcm_format_width
amiller@amiller-asus:~$ sudo modprobe intel8x0
FATAL: Module intel8x0 not found.
amiller@amiller-asus:~$ 



Here are those outputs. sorry for taking so long

Markbuntu, thanks for the links but, I have tried both of those the first one I could not get working. the 2 one I did last time I had linux installed and it work but I had to downgrade my kernel and then other programs that I needed would not install.

---

### Post by mindoms on 2008-10-04
I'm sorry. i wont be able to fix this.
One last chance might be to follow this thread:
[http://ge.ubuntuforums.com/showthread.php?t=762349](http://ge.ubuntuforums.com/showthread.php?t=762349)

good luck :)

---

### Post by markbuntu on 2008-10-04
Those ASUS mobos...you might try a bios update for that one. I think I saw some threads about that board and it seems that's what was needed to get the onboard to work. You might try a search of these forums or a google search for that specific mobo.

---

### Post by amiller2571 on 2008-10-04
Ok. Thanks for all your help. I think I'll just look into getting a nother sound card for now till Creative comes out with a driver (if they ever do).

The last time I had Ubuntu installed I did that kernel downgrade to get soundblaster working. I did a bois update and it killed the sound card driver. I have no idea what happen but it just stop working.

I have always had trouble with the motherboard. I have 3 GB of ram installed in it and all 32 bit systems can only see 2 even thow the bois showed 3. After the bois update the bois drop to 2.3 and the OS showed 2.3. I have know Idea why it does this. I move the RAM chips around and ran test on them. Before the bois update 64 bit system showed all 3 GB but, I not show now I have not installed it seens the update.

---

### Post by markbuntu on 2008-10-04
Get a card with C-Media chips in it, they work OOB and have good specs and are cheap.

---

### Post by amiller2571 on 2008-10-05
Would this one be a good card for Ubuntu?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16829186001](http://www.newegg.com/Product/Product.aspx?Item=N82E16829186001)

---

### Post by markbuntu on 2008-10-05
It has the same C-Media 8768 as my sound card and the specs seem to be all the same. My card is a SIIG though but most likely the same exact one.

---

### Post by amiller2571 on 2008-10-05
Ok. Thanks for all your help!!!

---

### Post by rokimoki on 2008-10-05
did you fixed it? I have the same problem... but still no sound...

---

### Post by amiller2571 on 2008-10-05
No. I have to buy a new sound card for now till Sound Blaster comes out with a working driver.

---

### Post by rokimoki on 2008-10-05
owww I have this audio card, the same as your signature...

---

### Post by amiller2571 on 2008-10-06
There is one way to get it working but you have to do a kernel downgrade whick i don't want to do but just follow this.[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675) I did it once and it work but some other programs that I needed would ot work with the older kernel

---

