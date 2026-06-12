---
title: "Asus N53jq, sound not working"
date: 2010-12-15
forum: Hardware
---

### Post by tivnanwebb on 2010-12-15
Recently purchased the Asus N53jq. The specs are really nice, but the internal speakers won't work in Ubuntu (even though they work in Windows). I'm a new user, and just want to get out of the shadow of windows, so I would appreciate any help I can get on this matter. The output still works, and the chipset is Intel Hm55 express. Thanks.

---

### Post by tomas fri zu on 2010-12-15
Hi, I've just solved the same problem on mine new N53JQ:

1. open file /etc/modprobe.d/alsa-base.conf as root

2. write to the end of the file

      options snd-hda-intel model=auto position_fix=0

3. save the file

4. reboot

---

### Post by jreece on 2010-12-17
Tried that and still no sound through the speakers or HDMI.

---

### Post by jreece on 2010-12-17
> **jreece said:**
> Tried that and still no sound through the speakers or HDMI.
...when editing with sudo. Literally logging into the terminal as root did the trick. Thanks!

---

### Post by jreece on 2010-12-17
Still no HDMI audio.

---

### Post by tomas fri zu on 2010-12-20
You can try this (however I can't because I don't have anything that would play sound from HDMI).

Go to sound preferences (in ubuntu menu -> System -> Preferences -> Sound Preferences) and in card "Output" choose HDA NVidia Digital Stereo (HDMI).

---

### Post by jreece on 2010-12-20
I'm not that lazy. I already tried that. I have done a lot of searching and there seems to have been a problem with the drivers for the Realtek ALC259 chipset with the 10.04 and the 10.10 releases of ubuntu (and other distributions.) From what I can see this issue is "officially" fixed as far as the linux community is concerned, but there are still some bugs obviously. 

As for the HDMI is that controlled through the same sound chip or does the nvidia chip handle that? I'm currently using the proprietary nvidia graphics drivers and they work well for multiple monitors etc.

---

### Post by jreece on 2010-12-24
There are two sound controllers in this PC. The internal speakers and input/output are controlled by the Realtek chip that tomas fri zu found a fix for and HDMI is controlled by the nVidia 425m chip set. 

In addition to the line provided by tom you need to add 

 options snd-hda-intel probe_mask=0xffff,0xfff2

to the end of the same file and reboot.

I found the fix here: [https://bbs.archlinux.org/viewtopic.php?pid=767623](https://bbs.archlinux.org/viewtopic.php?pid=767623)

I hope this helps someone else. Happy Huluing!

---

### Post by jreece on 2010-12-24
What?

---

### Post by tomas fri zu on 2010-12-26
It's a bit off-topic, but I solved some problems with touchpad and suspending to ram and put useful links to this post
[http://art.ubuntuforums.org/showpost.php?p=10281274&postcount=348](http://art.ubuntuforums.org/showpost.php?p=10281274&postcount=348)

---

### Post by jreece on 2011-01-04
Thanks. I was just getting around to looking for a fix for suspend.

---

### Post by lidex on 2011-01-04
So this is solved then? OP, can you mark it using thread tools up top?

---

### Post by Pieterd218 on 2011-01-11
I am sorry, but it is still not working for me after the suggestions done before. In a French topic I found I should enable a sound option in the bios, but I can't find this option either. Anyone have a clue how to continue from here?

Edit: This problem was solved by checking Analog output to  Analog speakers in Sound preferences/output tab...

---

### Post by lukfugl on 2011-01-13
> **Pieterd218 said:**
> I am sorry, but it is still not working for me after the suggestions done before. In a French topic I found I should enable a sound option in the bios, but I can't find this option either. Anyone have a clue how to continue from here?

Edit: This problem was solved by checking Analog output to  Analog speakers in Sound preferences/output tab...

I am still having problems getting this to work as well. I've added the snd-hda-intel line to my alsa-base.conf, but (1) sound still not working, and (2) I don't have an analog option in the Sound preferences Output tab. The only radio button there is "Internal Audio Digital Stereo (IEC958)".

Is there something special I need to do to make the analog option show up in the Output tab?

---

### Post by lidex on 2011-01-13
> **lukfugl said:**
> I am still having problems getting this to work as well. I've added the snd-hda-intel line to my alsa-base.conf, but (1) sound still not working, and (2) I don't have an analog option in the Sound preferences Output tab. The only radio button there is "Internal Audio Digital Stereo (IEC958)".

Is there something special I need to do to make the analog option show up in the Output tab?

It would help to see your system status. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by jozwa on 2011-01-14
i made one
[http://www.alsa-project.org/db/?f=882d69e84f9094d86ac0003e74d3797c4e0881d5](http://www.alsa-project.org/db/?f=882d69e84f9094d86ac0003e74d3797c4e0881d5)
can you help please

---

### Post by lidex on 2011-01-15
> **jozwa said:**
> i made one
[http://www.alsa-project.org/db/?f=882d69e84f9094d86ac0003e74d3797c4e0881d5](http://www.alsa-project.org/db/?f=882d69e84f9094d86ac0003e74d3797c4e0881d5)
can you help please

Were you trying to get hdmi audio working? Those edits you made to alsa-base.conf should be removed. Next update your alsa modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by jozwa on 2011-01-15
Thax for quick replay.
but the hdmi audio isn't my first task.
i'm trying to get sound out of my internal speakers.
if i now conf my sound and i choice for duplex and output on analoog speakers, i can hear it on my earphone when i plug them in. if if config not to analog speaker but to analog out of analog headphone. there is no sound any where.
but i didn't try your solution for now because i understand it's for hdmi to get working. i take that for step 2.
thanks in advantage.

joachim

> **lidex said:**
> Were you trying to get hdmi audio working? Those edits you made to alsa-base.conf should be removed. Next update your alsa modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by lidex on 2011-01-16
No. Updating the alsa modules provides better support for your codec/s regardless of output. So not just for hdmi. I'm sorry if my wording implied that.

---

### Post by jozwa on 2011-01-16
oke. now i have great news. after al had done by google its working already and without your advice.
here is what i did. i hope i remember it right.
1 i tried all options given on page one
2 even some simulair i dont realy know where i found( see the extra lines in my alsa-base.conf)
3 next i did: [https://wiki.archlinux.org/index.php/Asus_N82JV#Audio](https://wiki.archlinux.org/index.php/Asus_N82JV#Audio) except the last part about ´alias´.
that mean i did this part.( i downloaden link nr 8 and 9 (see below) )
```
1. Install ALSA drivers available at Realtek [[8]]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false") 
 tar xvf LinuxPkg_x.x
tar xvf alsa-driver-1.0.xx
cd alsa-driver-1.0.xx
./configure --with-cards=hda-intel
make
make install ** Note: **Realtek's  ALSA drivers, currently 1.0.23-5.15rc5, aren't compiling properly in  kernel 2.6.35. As an alternative, download the latest alsa-driver  snapshot from here[[9]]("http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-snapshot.tar.gz") (tested with 01/09/2010 snapshot)
 2. Add [COLOR=#000055][FONT=monospace]options snd-hda-intel index=0 model=auto[/FONT][/COLOR] to [COLOR=#005500][FONT=monospace]/etc/modprobe.d/modprobe.conf[/FONT][/COLOR]. 
Open [COLOR=#005500][FONT=monospace]/etc/modprobe.d/sound.conf[/FONT][/COLOR]

```4 the last part i did was
```
 sudo apt-get install --reinstall linux-image-2.6.35-24-generic
```(i cant find where i found that could be a solution.)

now i have a have 4 opties for ubuntu (2 safe mode of course) but the same kernel version.
only the new one is 
```
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 6b6e5b33-f679-4332-8d70-bfe9959384b3
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=6b6e5b33-f679-4332-8d70-bfe9959384b3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
```the old one start only tty1 en the new one start tty8(gui)

i hope i can help anyone whit this and properly lidex, you can understand what is happening so ubuntu can be growing. Thank you for helping and i hope this will keep working even after kernel updates.
my next step is updating nvidia driver. because i can't change the visual effects setting whit the recommended nvidia driver provided by "additional drivers".

even i'm not great whit linux i like to learn and if you like you can explain what could happen by what i have done to let my sound working.(extra, i check if i get sound out of my mini jack plug and even that is working as it should be.)

maby this olso can be help full: my actualy alsa-base.conf:
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
#zelf toegevoeg van (http://ubuntuforums.org/showthread.php?t=1646249)
#options snd-hda-intel model=auto position_fix=0
#options snd-hda-intel probe_mask=0xffff,0xfff1
#options snd-hda-intel probe_mask=0xffff,0xfff2
#options snd-hda-intel index=0 model=auto
#alias snd-card-0 snd-hda-intel
#alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=auto
```

---

### Post by blowfish880 on 2011-01-18
hey guys,
when i bought the above mentioned notebook, i had the same problem and solved it with the fix on the first page (the line at the end of alsa-base.conf). this worked, but recently i noticed that the speakers are not working anymore for no apparent reason. in the meantime i only made some updates via synaptic (that included a kernel update, but booting into the old kernel doesn't work either) and disabled the sound for the login screen. i also did some stuff in windows (dual boot, installed skype) - not sure if that's relevant. 
to fix the issue i tried to update the alsa modules as described above. i checked everything in alsamixer and must have tried about every combination in the sound options menu of ubuntu. the peculiar thing is, that the sound works, if i connect headphones, even if i select "analog speakers" in the output tab of the sound preferences. does anyone have a clue, why my speakers are not working anymore?

---

### Post by blowfish880 on 2011-01-18
hey guys,
when i bought the above mentioned notebook, i had the same problem and solved it with the fix on the first page (the line at the end of alsa-base.conf). this worked, but recently i noticed that the speakers are not working anymore for no apparent reason. in the meantime i only made some updates via synaptic (that included a kernel update, but booting into the old kernel doesn't work either) and disabled the sound for the login screen. i also did some stuff in windows (dual boot, installed skype) - not sure if that's relevant. 
to fix the issue i tried to update the alsa modules as described above. i checked everything in alsamixer and must have tried about every combination in the sound options menu of ubuntu. the peculiar thing is, that the sound works, if i connect headphones, even if i select "analog speakers" in the output tab of the sound preferences. does anyone have a clue, why my speakers are not working anymore?

---

### Post by blowfish880 on 2011-01-18
hey guys,
when i bought the above mentioned notebook, i had the same problem and solved it with the fix on the first page (the line at the end of alsa-base.conf). this worked, but recently i noticed that the speakers are not working anymore for no apparent reason. in the meantime i only made some updates via synaptic (that included a kernel update, but booting into the old kernel doesn't work either) and disabled the sound for the login screen. i also did some stuff in windows (dual boot, installed skype) - not sure if that's relevant. 
to fix the issue i tried to update the alsa modules as described above. i checked everything in alsamixer and must have tried about every combination in the sound options menu of ubuntu. the peculiar thing is, that the sound works, if i connect headphones, even if i select "analog speakers" in the output tab of the sound preferences. does anyone have a clue, why my speakers are not working anymore?

---

### Post by blowfish880 on 2011-01-18
hey guys,
when i bought the above mentioned notebook, i had the same problem and solved it with the fix on the first page (the line at the end of alsa-base.conf). this worked, but recently i noticed that the speakers are not working anymore for no apparent reason. in the meantime i only made some updates via synaptic (that included a kernel update, but booting into the old kernel doesn't work either) and disabled the sound for the login screen. i also did some stuff in windows (dual boot, installed skype) - not sure if that's relevant. 
to fix the issue i tried to update the alsa modules as described above. i checked everything in alsamixer and must have tried about every combination in the sound options menu of ubuntu. the peculiar thing is, that the sound works, if i connect headphones, even if i select "analog speakers" in the output tab of the sound preferences. does anyone have a clue, why my speakers are not working anymore?

---

### Post by blowfish880 on 2011-01-18
hey guys,
when i bought the above mentioned notebook, i had the same problem and solved it with the fix on the first page (the line at the end of alsa-base.conf). this worked, but recently i noticed that the speakers are not working anymore for no apparent reason. in the meantime i only made some updates via synaptic (that included a kernel update, but booting into the old kernel doesn't work either) and disabled the sound for the login screen. i also did some stuff in windows (dual boot, installed skype) - not sure if that's relevant. 
to fix the issue i tried to update the alsa modules as described above. i checked everything in alsamixer and must have tried about every combination in the sound options menu of ubuntu. the peculiar thing is, that the sound works, if i connect headphones, even if i select "analog speakers" in the output tab of the sound preferences. does anyone have a clue, why my speakers are not working anymore?

//EDIT: sory, for the multiple posts. obviously i had some problems with the connection. can an admin please delete the duplicate posts?

---

### Post by lidex on 2011-01-18
> **blowfish880 said:**
> hey guys,
when i bought the above mentioned notebook, i had the same problem and solved it with the fix on the first page (the line at the end of alsa-base.conf). this worked, but recently i noticed that the speakers are not working anymore for no apparent reason. in the meantime i only made some updates via synaptic (that included a kernel update, but booting into the old kernel doesn't work either) and disabled the sound for the login screen. i also did some stuff in windows (dual boot, installed skype) - not sure if that's relevant. 
to fix the issue i tried to update the alsa modules as described above. i checked everything in alsamixer and must have tried about every combination in the sound options menu of ubuntu. the peculiar thing is, that the sound works, if i connect headphones, even if i select "analog speakers" in the output tab of the sound preferences. does anyone have a clue, why my speakers are not working anymore?

//EDIT: sory, for the multiple posts. obviously i had some problems with the connection. can an admin please delete the duplicate posts?
Try removing that edit from alsa-base.conf

---

### Post by blowfish880 on 2011-01-19
nope, doesn't work either.

---

### Post by Yuri_MB on 2011-01-19
@blowfish: I had the exact same issue as you had. All of a sudden the sound did not work anymore. So, actually I reinstalled alsa, using
```

sudo aptitude reinstall alsa-base
```

Rebooted, and still no sound. I got agitated, turned the laptop off and went to sleep. This morning I started the laptop again and the sound was back.
So to be honest, it looks more or less random whether or not we have sound :-). You could try reinstalling the alsa base.
Oh, also verify if in your BIOS (somewhere around something called security, you can set pci locks) that the soundcard is set to unlock. That's all I did, and now I have sound again :-).

Good luck!

---

### Post by blowfish880 on 2011-01-19
> **Yuri_MB said:**
> 
```

sudo aptitude reinstall alsa-base
```


that did the trick. thanks heaps.

---

### Post by blowfish880 on 2011-01-19
but you're right, it seems quite random when the speakers work and when they won't. it was working today, then i rebooted to windows and used a headset. after rebooting to ubuntu the speakers don't work again and even reinstalling alsa-base doesn't do it. this is really frustrating. if anyone has an idea why this is - i'm happy about any clues.

---

### Post by lidex on 2011-01-20
@blowfish880
Can you provide more system info please? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by blowfish880 on 2011-01-21
hey lidex,
recently i added the maverick partner repository (for a different reason) and that caused a few updates including some alsa stuff. right now the sound is working. i do have a feeling that it will break again. if it does i will run the command you told me to but for now i'm gonna leave it as it is (never change a working system). thanks anyway.

---

### Post by blowfish880 on 2011-01-24
there we go: briefly fired up windows (didn't even do much, just wanted to test something), rebooted to ubuntu and sound is broken again. reinstalling alsa-base and linux-alsa-driver-module-... didn't help either. i ran the command and the result is here:
[http://www.alsa-project.org/db/?f=ee8a147b3b7fec8dcf2e4a7daeac0de7871caf74](http://www.alsa-project.org/db/?f=ee8a147b3b7fec8dcf2e4a7daeac0de7871caf74)

i'd really appreciate your help!

---

### Post by jozwa on 2011-01-24
> **blowfish880 said:**
> there we go: briefly fired up windows (didn't even do much, just wanted to test something), rebooted to ubuntu and sound is broken again. reinstalling alsa-base and linux-alsa-driver-module-... didn't help either. i ran the command and the result is here:
[http://www.alsa-project.org/db/?f=ee8a147b3b7fec8dcf2e4a7daeac0de7871caf74](http://www.alsa-project.org/db/?f=ee8a147b3b7fec8dcf2e4a7daeac0de7871caf74)

i'd really appreciate your help!

i reïnstalled recendly my ubuntu from 32 to 64 bit and i follow my discription i did and it work again.
so lets try it my way. see page 2 almost the end.

---

### Post by lidex on 2011-01-25
> **blowfish880 said:**
> there we go: briefly fired up windows (didn't even do much, just wanted to test something), rebooted to ubuntu and sound is broken again. reinstalling alsa-base and linux-alsa-driver-module-... didn't help either. i ran the command and the result is here:
[http://www.alsa-project.org/db/?f=ee8a147b3b7fec8dcf2e4a7daeac0de7871caf74](http://www.alsa-project.org/db/?f=ee8a147b3b7fec8dcf2e4a7daeac0de7871caf74)

i'd really appreciate your help!
Try changing the position fix parameter you added to alsa-base.conf to:
```
probe_mask=1
```
The value of 0 you have for position fix is actually default behavior anyway.

---

### Post by blowfish880 on 2011-01-25
good news, the sound is working again. at the moment it seems like i just have to turn off the laptop after using windows (rebooting doesn't do it). after turning it off and on the sound works. it's really strange behaviour. thanks to both of you for the help.

---

### Post by mad_prince on 2011-01-25
Hi, I've some problem with sound in my asus n52da. Everything was fine 'till yesterday, but today I've got sound only from output (headphones), but internal speakers don't work. my system info 
 [http://www.alsa-project.org/db/?f=8e836c9b8041169a58e806548aeb9c17b58bff69](http://www.alsa-project.org/db/?f=8e836c9b8041169a58e806548aeb9c17b58bff69)

Speakers ALTEC

Edit

Strange, it works again. Yesterday evening, before I went to bed speakers doesn't work, but today it is ok. No updates, no soft installation, just turning on the computer.

My current alsa sys info
[http://www.alsa-project.org/db/?f=663d5f1555d0c0be402b08bad25fcad1ee431cdd](http://www.alsa-project.org/db/?f=663d5f1555d0c0be402b08bad25fcad1ee431cdd)

---

### Post by mad_prince on 2011-01-28
doesn't work today :/

---

### Post by lidex on 2011-01-29
> **mad_prince said:**
> doesn't work today :/

For you I suggest removing edits from alsa-base.conf
```
snd-hda-intel: model=auto position_fix=0
snd-hda-intel: model=eeepc-p901

```
and re-installing alsa. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by tivnanwebb on 2011-01-30
So after trying all of the pertinent solutions from the first page, without any results, I scrolled through the subsequent posts and noticed that one user reccomended that I try shutting down my computer in windows and then starting it again in ubuntu, and voila--the sound suddenly worked. Because the methadology was anything but scientific, I'm not sure which of the solutions was responsible--but I do know that it has to be one of the first posts, and that it will only work once you have manually rebooted FROM windows. The sound has worked continuously since then, even though I've been using both Windows and Ubuntu on this computer, and have not needed to shut down windows (as opposed to hitting "restart") since the first time. It's really strange, but it did the trick. Thanks to all.

---

### Post by mad_prince on 2011-01-30
when u said that... I lost my sound after rebooting to ubuntu from windows 7. Maybe it's connected somehow?

---

### Post by fermilesi on 2011-02-01
Fixed my notebook speakers!!! (Asus X5MJF = N53JF)
 
Thank you so much.
[I'm just starting to pour some of the water for my first cup of Ubuntu!]

---

### Post by KubuBeans on 2012-07-03
Hey I'm getting the same error everyone else has gotten and I added the two lines suggested on Page 1 and 2 to the bottom of my alsa-base.conf 
What should I do? My headphones work when my computer originally boots, but oddly enough the sound starts to accelerate more and more as time goes by. 
I unchecked "hardware acceleration" for my flash player as well.

---

