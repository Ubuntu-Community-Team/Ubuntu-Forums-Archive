---
title: "Toshiba P200-155 no sound"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by blop on 2007-05-17
Hi,

I have installed kubuntu 7.04 and it set everything up without hassle except for my multi memory card reader and more importantly sound.

I have read a few posts and tried a number of things to check its not muted etc...tried this fix:

[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

but it did not work.....can anyone help?

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]lspci
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)

anyhelp appreciated...

---

### Post by blop on 2007-05-20
I have moved across to Ubuntu 7.04 as i found KDE really buggy with beryl on my system....still sound does not work. I have reinstalled ALSA from synaptic and that has not helped any....

really desperate for some help...

i have tried the ALSA recompile here:

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

i did it but, their is now no sound card is detected in System>Admin>Sound. It realises their is a card i think:

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

matt@matt-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
matt@matt-laptop:~$ cat /proc/asound/cards
--- no soundcards ---
matt@matt-laptop:~$ aplay -l
aplay: device_list:222: no soundcards found...
matt@matt-laptop:~$

But im not sure how i get to use it....any help apprecated!!

---

### Post by blop on 2007-05-21
bump

---

### Post by blop on 2007-05-21
bump....save me....save me... im starting to think im death :popcorn:

---

### Post by stchman on 2007-05-21
> **blop said:**
> I have moved across to Ubuntu 7.04 as i found KDE really buggy with beryl on my system....still sound does not work. I have reinstalled ALSA from synaptic and that has not helped any....

really desperate for some help...

i have tried the ALSA recompile here:

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

i did it but, their is now no sound card is detected in System>Admin>Sound. It realises their is a card i think:

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

matt@matt-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
matt@matt-laptop:~$ cat /proc/asound/cards
--- no soundcards ---
matt@matt-laptop:~$ aplay -l
aplay: device_list:222: no soundcards found...
matt@matt-laptop:~$

But im not sure how i get to use it....any help apprecated!!

I have a Toshiba laptop with an SB450 sound card.  The procedure here should work as well for your card:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

Let me know if it works as it worked like a charm for me.

---

### Post by blop on 2007-05-21
sadly it failed...

matt@matt-laptop:~$ sudo rmmod snd-hda-intel
Password:
ERROR: Module snd_hda_intel does not exist in /proc/modules
matt@matt-laptop:~$ sudo rmmod snd-hda-intel
ERROR: Module snd_hda_intel does not exist in /proc/modules
matt@matt-laptop:~$ 

i think its because i dont have a sound card installed....help!!

matt@matt-laptop:~$ aplay -l
aplay: device_list:222: no soundcards found...
matt@matt-laptop:~$

---

### Post by tumnus on 2007-05-27
/proc/modules lists only the loaded modules so it must not have been loaded when you tried 'rmmod snd-hda-intel', which is also why alsa would have not shown any cards. Did you try a 'modprobe snd-hda-intel' first?

There seems to be all sorts of HDA chipset problems, but there are also many different chipsets. It appears the 'model=3stack' fix is for an ATI SB450 chip, which is in some other Toshiba laptops, whereas the Toshiba P200 has an Intel 82801G audio chip.

I am interested in getting the Toshiba P200-155 as well, since it is a near perfect price/feature compromise for my needs as a desktop replacement, so I have been hunting around the web for this problem.

This person using Debian seems to have fixed it with a kernel recompile, though it is hard to tell what patches each distro uses, which could equally affect the results:

[http://www.linux-on-laptops.com/forum/showthread.php?t=1488](http://www.linux-on-laptops.com/forum/showthread.php?t=1488)

It seems to be confirmed, however, with this Ubuntu bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92909](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92909)

Note that one person also mentions that even with the latest kernel you still have to run 'modprobe snd_hda_intel model=6stack-digout' to get it to work, which is a step you were perhaps missing?

Make sure that there is some reference to 'hda' in your dmesg output, or else the correct drivers are obviously not being loaded.

---

### Post by blop on 2007-06-02
appreciate your help...

had a look at those instructions for installing hda sound on my lappy using debian but the commands did not work...


the only reference to hda i have  is this..

[   15.996000] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...

---

### Post by jlwood on 2007-06-02
I have a toshiba a135-s4427 and had no sound or wireless after installing Ubuntu. Here is what worked for me, not sure if you tried this...

Here is what worked for me. I have the ALC861VD.

Edit "/etc/modprobe.d/alsa-base", adding this line, "options snd-hda-intel position_fix=1 model=3stack"

Restart the PC


Then I went to the sound preferences, devices tab, change playback to OSS - Open Sound System.

On the voulume control, File-change device-HDA Intel (Alsa Mixer)

---

### Post by tumnus on 2007-06-03
There are loads of separate bug reports about this, with varying degrees of success fixing it:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93263](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93263)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94373](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94373)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107821](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107821)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111486](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/111486)

Do you have all the Feisty updates downloaded and installed?
Is the snd-hda-intel module actually loaded? (Check with 'lsmod | grep hda')
Out of curiosity, does an Ubuntu Edgy (6.10) Live CD have sound working out of the box?

Are you rebooting when changing any settings? It's the easiest way to make sure everything is restarted properly, although some laptop users have reported having to even completely shutdown and cold boot to get sound working.

---

### Post by blop on 2007-06-03
Hi...really appreciate your continued help....its driving me nuts..


lsmod | grep hda gives me the following:

snd_hda_intel          21912  4 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm                79876  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    54020  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm


No idea what it means, but guess it means i have some modules working. Suspect driver is faulty as i dont have a master volume bar in my audio setup or alsa mixer.

i have all the updates

i will get a 6.10 cd and give it a go...

EDIT: The 6.10 also gives me no sound....but it does give me a master volume bar...so thats something new!! :)


thanks

---

### Post by cptcrunch on 2007-06-03
This happens to be a very common problem and is related to ACPI. If I am correct your model is from the UK? 

It's generally considered a Linux bug if Windows handles an unmodified DSDT and Linux does not.

If you really want to geek out and feel motivated, you can retrieve your dsdt file from your bios and debug it.

The directions to do that and the place to get started is at

[http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)

Also, another very good thread that helped me is

[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

GOOD LUCK

---

### Post by blop on 2007-06-03
cpt: thanks for your reply....but DSDT files and debugging sounds a bit like Flux Capaicators and Tri-Litiumn crystals to me dude... :)

there appears not to be a p200 DSDT file for my lappy on that site anyway...

---

### Post by tumnus on 2007-06-03
Hmmm, this does seem rather odd. _[THIS](http://66.249.91.104/translate_c?hl=en&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fid%3D122388&prev=/search%3Fq%3Dtoshiba%2Bp200%2Bcard%2Breader%2Bubuntu%26hl%3Den%26safe%3Doff%26sa%3DG)_ french Ubuntu user has a P200-157 with the same chipset and yet his problem was fixed with just the 'options snd-hda-intel model=3stack' in /etc/modprobe.d/alsa-base if I'm reading the (poor) translation right.

cptcrunch may well be right. One way to test if it is the ACPI affecting sound is to (re)boot and at the GRUB boot menu, press the key 'e' and add the following to the end of the kernel boot string (with a space before it):

acpi=off

then press return and it should temporarily boot with ACPI off. I wouldn't run it for long with this off as battery and temperature control is disabled, but it shouldn't harm it for this test and rebooting will re-enable ACPI under Linux.

I also wonder whether the BIOS version has any effect, since some have had success with simple fixes and others don't. I notice on the Toshiba website there is a fairly recent BIOS update which you could try:
_[BIOS Update Page](http://uk.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/download_driver_details.jsp?service=UK&selCategory=2&selFamily=2&selSeries=152&selProduct=727&language=13&selOS=null&selType=null&yearupload=&monthupload=&dayupload=&useDate=null&mode=allMachines&search=&action=search&macId=&country=8&selectedLanguage=13&type=null&page=1&ID=57762&OSID=-1&driverLanguage=42)_

 (DISCLAIMER: while I wouldn't try some hacked BIOS file from an unofficial source, a download from Toshiba *should* be fine. Even so, it is entirely up to you to try the BIOS update.)

---

### Post by crimsun on 2007-06-03
> **blop said:**
> Suspect driver is faulty as i dont have a master volume bar in my audio setup or alsa mixer.

It is NOT a driver bug for there not to exist a 'Master' control element.  Not all codecs even have this register, and many instances, we hack around it by binding.  Please make sure you use current hg alsa-kernel and alsa-driver (search the forum, or join #alsa on IRC).  Better yet, file a bug report against the `linux-source-2.6.20' source package (if you're using feisty).

---

### Post by DonLorenzo on 2007-06-08
This worked for me on a Toshiba P200-ST2071
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards)

---

### Post by DonLorenzo on 2007-06-08
This worked for me. Toshiba P200-ST2071
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards)

---

### Post by tumnus on 2007-06-15
Well, I took the plunge and got a Toshiba P200-155 myself and it's a stunning laptop!

I'm not sure what you did, but all I had to do to get sound to work after a clean install of Kubuntu 7.04 was add the line:

options snd-hda-intel model=3stack

to /etc/modprobe.d/alsa-base and reboot. That's it! In KDE I also right clicked the speaker icon and set the master channel to PCM which allows the volume control on the front of the laptop to set the main volume.

Also working out-of-the-box:

WiFi (with WEP encryption using KnetworkManager)
Trackpad
SD Card reader
Power management (haven't tested suspend/hibernation yet)

Got Beryl working fine for a 3D desktop too. Had to install the Nvidia driver and correct the BusID in /etc/X11/xorg.conf to "1:0:0" in the graphics card section as nvidia-glx-config set it wrong and added ' Option &#8220;AddARGBGLXVisuals&#8221; &#8220;True&#8221; ' to the card section as well. Then I installed beryl-manager and beryl-kubuntu and it worked a treat.

Laptop BIOS Version: 1.3

I'm not too bothered about the webcam, but I might have a go at getting that to work too.

---

### Post by tumnus on 2007-06-23
Just thought I would add that I have created a full laptop testing page on the Ubuntu Wiki after getting everything working (including Sound, Bluetooth and the Webcam):

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteP200-155](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteP200-155)

Blop, I can only think that you have perhaps tried too many different things to get sound working and would be better off trying again with a fresh install and then follow the instructions I put in the testing page above.

---

### Post by blop on 2007-10-26
options snd-hda-intel model=3stack

That added to /etc/.modprobe/alsa-base defintley fixes sound in Feisty for the P200. In Gutsy sound works fine on install without any tweaking as does video...


However issues remain with no speaker mute when headphones are plugged, the webcam and mic

---

