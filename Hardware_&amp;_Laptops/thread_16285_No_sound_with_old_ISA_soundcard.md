---
title: "No sound with old ISA soundcard"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by Biffy on 2005-02-20
I just installed Ubuntu on an old AMD K6 computer. I can't get any sound. It's an old ISA Soundblaster 16 (or Soundblaster AWE 16, not quite sure) and it's just dead. I havent had any sound-problems in Linux before so i feel kinda helpless here.

This is what alsamixer gives me:

```
alsamixer: function snd_ctl_open failed for default: No such file or directory
``` 

I am using Hoary btw.

---

### Post by kelean on 2005-02-20
HI,  I am having the same problem.  On other linux distros all i needed to do is run alsaconf.  But when I try it is not there.  I have been reading quite a bit this morning and all im getting is sore eyes.  I really like Ubuntu so far, but this is getting frustrating.  Please help us!!

---

### Post by Biffy on 2005-02-20
Do you also have an old ISA soundcard, or does this problem appear on new soundcards too?

---

### Post by kelean on 2005-02-20
[QUOTE=Biffy]Do you also have an old ISA soundcard, or does this problem appear on new soundcards too?[/QUOTE]
 Yes I do, and I know that it works fine but cant get it to work with Ubuntu.

---

### Post by Baba Tony on 2005-02-20
[QUOTE=kelean]Yes I do, and I know that it works fine but cant get it to work with Ubuntu.[/QUOTE]
 very new to this game myself but sorted out simular problem after trip to [http://www.gentoo.org/doc/en/alsa-guide.xml#alsa-utils](http://www.gentoo.org/doc/en/alsa-guide.xml#alsa-utils) after number of attempts managed to configure an ISA ALS100 card best of luck

---

### Post by m4ng0 on 2005-02-21
I've installed Ubuntu in a K6-2 with an ISA SoundBlaster 16. I did as follows:
1) opened a terminal
2) typed:
sudo modprobe sb io=0x220 irq=7 dma=1 dma16=5
3) logged out from Gnome and logged in again
4) raised sound volume
and it worked!

Then I added
sb io=0x220 irq=7 dma=1 dma16=5
to /etc/modules, so that the module gets loaded on boot.

---

### Post by Biffy on 2005-02-21
[QUOTE=m4ng0]I've installed Ubuntu in a K6-2 with an ISA SoundBlaster 16. I did as follows:
1) opened a terminal
2) typed:
sudo modprobe sb io=0x220 irq=7 dma=1 dma16=5
3) logged out from Gnome and logged in again
4) raised sound volume
and it worked!

Then I added
sb io=0x220 irq=7 dma=1 dma16=5
to /etc/modules, so that the module gets loaded on boot.[/QUOTE]

I tried that, and got this:

```
root@ubuntu:/home/larsson # modprobe sb io=0x220 irq=7 dma=1 dma16=5
modprobe sb io=0x220 irq=7 dma=1 dma16=5
FATAL: Error inserting sb (/lib/modules/2.6.10-3-386/kernel/sound/oss/sb.ko): No such device

```

What now?

---

### Post by m4ng0 on 2005-02-21
...probably you have a SoundBlaster AWE.
Try:
sudo modprobe snd-sbawe io=0x220 irq=5 dma=1 dma16=5

You can also look at this:
[http://www.ubuntuforums.org/showthread.php?t=1805](http://www.ubuntuforums.org/showthread.php?t=1805)

---

### Post by Biffy on 2005-02-21
```
root@ubuntu:/home/larsson # modprobe snd-sbawe io=0x220 irq=5 dma=1 dma16=5
FATAL: Error inserting snd_sbawe (/lib/modules/2.6.10-3-386/kernel/sound/isa/sb/snd-sbawe.ko): No such device
FATAL: Error running install command for snd_sbawe
```

Still no luck. :(

I dont know if that is the correct adress for the card either, and i dont know how to find out the correct adress. BIOS gave me nothing.

---

### Post by Biffy on 2005-02-21
Wait, i just ran that isapnp program and it seems i might have tricked you.

I have taken this from the conf-file:

```
# Card 1: (serial identifier 81 ff ff ff ff 20 00 a8 65)
# Vendor Id YMH0020, No Serial Number (-1), checksum 0x81.
# Version 1.0, Vendor version 0.0
# ANSI string -->OPL3-SA2 Sound Board<--
```

I just remembered that the soundblaster card crashed a while ago, so i changed it to this one. What to do now?

---

### Post by Biffy on 2005-02-21
The next step is to compare the adress for the card with a Windows machine. Well, i dont have a machine running Windows so im not really sure what to uncomment. I'll post the isapnp.conf here. I got this config by typing:

```
pnpdump > /etc/isapnp.conf
``` 

This is the config. Sorry if it's long:

edit: Seems like i cant post the config because it contains too many smileys, and i dont know how to shut them off.

---

### Post by m4ng0 on 2005-02-21
[QUOTE=Biffy]Wait, i just ran that isapnp program and it seems i might have tricked you.

I have taken this from the conf-file:

```
# Card 1: (serial identifier 81 ff ff ff ff 20 00 a8 65)
# Vendor Id YMH0020, No Serial Number (-1), checksum 0x81.
# Version 1.0, Vendor version 0.0
# ANSI string -->OPL3-SA2 Sound Board<--
```

I just remembered that the soundblaster card crashed a while ago, so i changed it to this one. What to do now?[/QUOTE]

Take a look [here](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Yamaha&card=UX256.&chip=YMF701%2C+YMF711%2C+YMF715%2C+YMF718%2C+YMF719%2C+OPL3+SA2%2C+OPL3+SA3&module=opl3-sa2).
It seems you should try:
 modprobe snd-opl3-sa2;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss

---

### Post by Biffy on 2005-02-22
Alright. It gave me this:

root@ubuntu:/home/larsson # modprobe snd-opl3-sa2;modprobe snd-pcm-oss;modprobesnd-mixer-oss;modprobe snd-seq-oss
FATAL: Module snd_opl3_sa2 not found.
root@ubuntu:/home/larsson #

Im gonna reboot now.

---

### Post by Biffy on 2005-02-22
No, still no sound. Why didnt it find that module?

---

### Post by Biffy on 2005-02-22
YAY! I fixed it. It was a typo actually. The correct name for the module is snd-opl3sa2

It works fine. Now let's see if i can edit modules.conf right so the module is loaded at boot.

---

### Post by Biffy on 2005-02-22
I am really not sure what i am suppose to type and where in modules.conf. Help. :)

---

### Post by m4ng0 on 2005-02-22
You can simply add the modules you need to load in /etc/modules, each one in its own line:
[file: /etc/modules]
...
snd-opl3sa2
snd-pcm-oss
....

and so on.

---

### Post by Biffy on 2005-02-23
Oh, so it is so simple. I tought it was /etc/modules.conf , wich actually is a bit confusing.

Well, thanks very much for your help!  \\:D/

---

### Post by landotter on 2005-02-23
[QUOTE=Biffy]Oh, so it is so simple. I tought it was /etc/modules.conf , wich actually is a bit confusing.

Well, thanks very much for your help!  \\:D/[/QUOTE]
 It certainly is simple--I couldn't figure out how to get my  ISA card to work till somebody suggested simply adding the module "sb" to /etc/modules. Fixed. I was also under the assumption that one needed to edit a different file. Too easy... :D

---

### Post by Biffy on 2005-02-23
Haha, yeah, that was too easy! :D

Got one more question. Seems like when i am playing mp3, the system get's a lot slower. Is that because my soundcard is crappy or what? I noticed the same thing under Slackware. This is the computer:

AMD K6 350 mhz
196mb RAM

I am running fluxbox, if that matters.

---

### Post by chronokun on 2006-04-18
I also have a k6 athlon with a yamaha opl3sa2 sound card, i've tried 
sudo modprobe snd-opl3sa2;.... etc
but it doesn't work, my sound used to work until i compiled a new kernal but now when i try and use sudo modprobe snd-opl3sa2 i get:
FATA: Error running install command for snd_opl3sa2
and for modprobe snd-pcm-oss etc i get :
FATAL: Module snd_pcm_oss not found.

---

### Post by chronokun on 2006-04-18
ahh, i've fixed it,
if found the solution here
[http://ubuntuforums.org/showthread.php?t=26990](http://ubuntuforums.org/showthread.php?t=26990)

---

