---
title: "Sound on Gateway Laptop MX3416"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by Serenader on 2006-12-07
Hello,

I recently got a gateway mx3416 laptop. However, I do not get any sound on it. The laptop has a SigmaTel Audio card. I tried the unchecking External Amp option as posted in other threads, however I do not find such option either on Dapper or Edgy. Can anyone please help me.

---

### Post by crazedgremlin on 2006-12-07
try running
```
sudo alsamixer
```
and unmuting all the things in 'output'

good luck :)

---

### Post by Serenader on 2006-12-07
> **crazedgremlin said:**
> try running
```
sudo alsamixer
```
and unmuting all the things in 'output'

good luck :)

Thanks gremlin for the reply, but it doesnt work. I ran sudo alsamixer, but I dont see anything that says output.

---

### Post by Serenader on 2006-12-07
> **crazedgremlin said:**
> try running
```
sudo alsamixer
```
and unmuting all the things in 'output'

good luck :)

By the way I am trying this from the Edgy Live CD

---

### Post by crazedgremlin on 2006-12-07
when you start alsamixer, you're in the output section by default.... I believe you have to hit tab to change sections.

so go through the sound thingies with the left and right buttons and when something is muted bring it up to around 50 (up and down buttons).

While you're doing this try playing some music (you probably need proprietary codecs like mp3) so you get instant output.

It'll be tricky to do this while you're running from the live cd, like installing mp3 codecs.  Plus everything will be really slow.
If it's possible, for easiness' sake, install ubuntu to the disk and then get it working.

---

### Post by Serenader on 2006-12-07
> **crazedgremlin said:**
> when you start alsamixer, you're in the output section by default.... I believe you have to hit tab to change sections.

so go through the sound thingies with the left and right buttons and when something is muted bring it up to around 50 (up and down buttons).

While you're doing this try playing some music (you probably need proprietary codecs like mp3) so you get instant output.

It'll be tricky to do this while you're running from the live cd, like installing mp3 codecs.  Plus everything will be really slow.
If it's possible, for easiness' sake, install ubuntu to the disk and then get it working.

Gremlin, thanks again for the quick reply. I tried playing the nelson mandela clip from the live cd, but no sound. I will install it and try if it works.

---

### Post by crazedgremlin on 2006-12-07
> **Serenader said:**
> Gremlin, thanks again for the quick reply. I tried playing the nelson mandela clip from the live cd, but no sound. I will install it and try if it works.

You don't need proprietary codecs to play the mandela clip; it's ogg or something.

Ok I think I might have something.  Run
```
sudo gedit /etc/modprobe.d/options
```
and at the end of the file add
```
options snd-hda-intel position_fix=1
```
save the file, close gedit, and reboot (I could find a command to restart alsa but a reboot is so much easier)


BTW don't do this while you're installing because it will edit the cd's config file, not the one on the hard disk.

---

### Post by Serenader on 2006-12-08
> **crazedgremlin said:**
> You don't need proprietary codecs to play the mandela clip; it's ogg or something.

Ok I think I might have something.  Run
```
sudo gedit /etc/modprobe.d/options
```
and at the end of the file add
```
options snd-hda-intel position_fix=1
```
save the file, close gedit, and reboot (I could find a command to restart alsa but a reboot is so much easier)


BTW don't do this while you're installing because it will edit the cd's config file, not the one on the hard disk.


I did that, no luck :-(. Any other ideas.

---

### Post by Serenader on 2006-12-08
I guess this is a known problem and ubuntu doesnt support this soundcard yet. If anyone has had luck with sound on gateway, please let me know.

---

### Post by crazedgremlin on 2006-12-08
Any more information about the problem would be nice... like the model (if possible) of the SigmaTel card.
:)

---

### Post by crazedgremlin on 2006-12-08
now that it's installed on the hard drive, try running alsamixer again.  Maybe without the sudo.

in alsamixer use the 'm' key to mute/unmute.

good luck

---

### Post by Serenader on 2006-12-08
> **crazedgremlin said:**
> now that it's installed on the hard drive, try running alsamixer again.  Maybe without the sudo.

in alsamixer use the 'm' key to mute/unmute.

good luck

Thanks gremlin again for your reply. 

I tried teh alsamixer again without sudo, but no luck.
Here are more details from my system.

$lsmod | grep snd
snd_hda_intel          23452  5 
snd_hda_codec         219392  1 snd_hda_intel
snd_pcm_oss            57344  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm               108168  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              31112  2 snd_pcm
snd                    79016  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              14112  1 snd
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When I play a song in winamp, it looks like its playing it. I can see the bars go up and down. So, its not complaining that it can't find the soundcard. But, I cant hear the volume from the speakers or from the headphones.

Let me know if you want any further information from my system.

Thanks in Advance.

---

### Post by Serenader on 2006-12-08
Here is the output from lspci

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8185 (rev 20)

---

### Post by crazedgremlin on 2006-12-08
It's looking like this is just a card that most people can't get to work.  I'm sorry, but I don't have the expertise to make it work. :(

oh well...

---

### Post by Serenader on 2006-12-08
> **crazedgremlin said:**
> It's looking like this is just a card that most people can't get to work.  I'm sorry, but I don't have the expertise to make it work. :(

oh well...

Hmm, too bad, I too checked in some other website that nVidia has stopped providing driver support for its card in Linux. thanks for all your repsonses. Hopefully a fix comes out for it soon.

---

### Post by brandoncolorado on 2006-12-18
Any news on a fix for this?  I have the same problem with MX3414

---

### Post by darkhatter on 2006-12-18
same problem on mx 3410 its suppose to work with kernel 2.6.20 and alsa 1.0.14 I'm on the ubuntu current so that update should come out soon, I'll write back if something happens

---

### Post by StormGuy on 2006-12-20
I have the same problem on my Gateway MX6448, which has the same soundcard.  All Linux distros I've tried (openSUSE, Sabayon, and Ubuntu) have been unable to make sound.

---

### Post by Serenader on 2006-12-20
> **StormGuy said:**
> I have the same problem on my Gateway MX6448, which has the same soundcard.  All Linux distros I've tried (openSUSE, Sabayon, and Ubuntu) have been unable to make sound.

Yup, I have tried all of them too, but no sound at all. Someone, posted on Gentoo forums that he was able to get it working with the new version of alsa driver. But, that requires me to recompile the kernel because alsa is already compiled in the kernels supplied by all those distros.

---

### Post by darkhatter on 2006-12-20
> **Serenader said:**
> Yup, I have tried all of them too, but no sound at all. Someone, posted on Gentoo forums that he was able to get it working with the new version of alsa driver. But, that requires me to recompile the kernel because alsa is already compiled in the kernels supplied by all those distros.

can you post the link , I'll do anything to get sound

---

### Post by Serenader on 2006-12-20
> **darkhatter said:**
> can you post the link , I'll do anything to get sound

Try the following links.

[http://hp-dv6000z.blogspot.com/2006/12/sound-off.html](http://hp-dv6000z.blogspot.com/2006/12/sound-off.html)

---

### Post by hoodsy on 2006-12-26
I have a gateway desktop and I have trouble with sound for a long time. Try to switch from digital to analog and see if it helps. In Ubuntu 6.10, open the volume controls and go to the last tab - there should be a check box to switch from digital to analog - Click it and save - Hopfully you will have sound. 
If you can't find that switch you can also switch from digital to analog in alsamixer but I don't remember how to do it. 

Hope this helps, 

Hoodsy

---

### Post by Serenader on 2006-12-26
> **hoodsy said:**
> I have a gateway desktop and I have trouble with sound for a long time. Try to switch from digital to analog and see if it helps. In Ubuntu 6.10, open the volume controls and go to the last tab - there should be a check box to switch from digital to analog - Click it and save - Hopfully you will have sound. 
If you can't find that switch you can also switch from digital to analog in alsamixer but I don't remember how to do it. 

Hope this helps, 

Hoodsy

The digital to analog switch in alsamixer is marked as IEC958. Check the following link.
[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=TroubleShooting](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=TroubleShooting)
However, unchecking or checking the option doesn't seem to change to anything.

---

### Post by darkhatter on 2006-12-27
I think this is good news, using Kernel 2.6.19 doesn't detect the sound card anymore, I'm not sure if this is done on purpose or if its a bug. I hope we see some results in the 2.6.20 I'll report back when that goes stable.

---

### Post by usergentoo on 2007-01-01
I have no sound also mine is the MX6448. After searching for the past year I found this bug report and they have a patch to test. [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2146](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2146)

If anyone gets sound working please let me know. I dont have time to try it out just yet trying to repair a bedroom caused by rain damage.

---

### Post by StormGuy on 2007-01-02
I managed to get sound working, but you have to use a USB headset.  I plugged mine in, changed the settings in preferences > sound so that all of the sound options were set to USB sound. 

My only problem now is that I can't get sound on Swiftfox/Firefox.  Still, that's minor at the moment.

Hurray, music :D

---

### Post by usergentoo on 2007-01-02
The USB headsets may work for you but it still don't solve the real problem.

---

### Post by darkhatter on 2007-01-02
is the audio chip in MX6448 the same as the mx3410

---

### Post by Serenader on 2007-01-03
> **darkhatter said:**
> is the audio chip in MX6448 the same as the mx3410

Most likely, but not necessarily. Does it use a sigmatel codec and an nVidia chipset?

---

### Post by usergentoo on 2007-01-03
The sigmatel codec on the MX6448 is 7634 but Im not sure on the other.

---

### Post by usergentoo on 2007-01-05
The patch worked and now I have sound.

But I need to figure out where to add this line at. So I have it at boot.
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe-mask=1

Fixed see below

---

### Post by Serenader on 2007-01-05
> **usergentoo said:**
> The patch worked and now I have sound.

But I need to figure out where to add this line at. So I have it at boot.
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe-mask=1

Thats great. But, can you please provide the series of steps you followed so that it will help others who want to get sound working.

Thanks.

---

### Post by darkhatter on 2007-01-05
does this work for other models mainly the mx34xx series

---

### Post by usergentoo on 2007-01-05
This is what worked for me


```

sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
sudo apt-get --purge remove alsa-base alsa-utils
sudo apt-get install build-essential linux-headers-$(uname -r)
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc1.tar.bz2
tar -jxvf alsa-driver-1.0.14rc1.tar.bz2
mv gateway.patch.txt /alsa-driver-1.0.14rc1/alsa-kernel/gateway.patch
cd alsa-driver-1.0.14rc1/alsa-kernel
patch -p1 <gateway.patch
cd ..
./configure --with-cards=hda-intel --with-debug=detect ; make
sudo su
pushd /lib/modules/`uname -r`/kernel
tar -zcvf oldsound.tgz sound/
find sound -name "snd*" -exec rm -f {} \;
popd
make install
mv /etc/modprobe.d/alsa-base.bak /etc/modprobe.d/alsa-base
dmesg -c >/dev/null
modprobe -r snd-hda-intel
modprobe snd-hda-intel probe_mask=1
exit
## Test and see if you have sound Remeber that your sound will be muted
## If all goes well in order for it to work at boot do this
sudo echo options snd-hda-intel probe-mask=1 >> /etc/modprobe.d/alsa-base
sudo echo alias snd-card-0 snd-hda-intel >> /etc/modules

```

---

### Post by usergentoo on 2007-01-05
Im not sure if it will work on the mx34xx. 
Try this ```
cat /proc/asound/card0/codec*
```
and look at the top of the line and see if it says "Codec: SigmaTel STAC9250".If you see that it may work.

---

### Post by usergentoo on 2007-01-06
One thing to add. Save your alsa-base file located /etc/modprobe.d/alsa-base and add at the bottom 
```
options snd-hda-intel probe-mask=1
```

Also add ```
alias snd-card-0 snd-hda-intel
``` to /etc/modules

---

### Post by darkhatter on 2007-01-07
> **usergentoo said:**
> Im not sure if it will work on the mx34xx. 
Try this ```
cat /proc/asound/card0/codec*
```
and look at the top of the line and see if it says "Codec: SigmaTel STAC9250".If you see that it may work.

mine (ours) is a stac9200, and I saw some bug reports on alsa but no one has done anything about them

---

### Post by harmeet on 2007-01-10
Just to update that I applied usergentoo's gateway patch on my Gateway MX3410 which has 9200 codec (usergentoo's is 9250). It didn't work for me. ](*,) 

So, if you have the same laptop as mine, you will have to wait. There is a bug against it and you can track it at - 

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2469](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2469)

I have wasted two weeks after this trying to fix it. :evil: 

BTW: Now it is not detecting any sound cards -

```
harmeet@harmeet-laptop:~$ cat /proc/asound/cards
--- no soundcards ---
```


](*,)

---

### Post by brandoncolorado on 2007-01-13
> **harmeet said:**
> Just to update that I applied usergentoo's gateway patch on my Gateway MX3410 which has 9200 codec (usergentoo's is 9250). It didn't work for me. ](*,) 

So, if you have the same laptop as mine, you will have to wait. There is a bug against it and you can track it at - 

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2469](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2469)

I have wasted two weeks after this trying to fix it. :evil: 

BTW: Now it is not detecting any sound cards -

```
harmeet@harmeet-laptop:~$ cat /proc/asound/cards
--- no soundcards ---
```


](*,)

I saw that bug request too.  I would say that it is a pretty serious bug request considering the popularity of this particular sound card setup.  This bug report was filed in August of 2006.  What is the usual turn around time on bugs like this?  I know that this is a free OS, so I don't want to complain, but isn't this a long time to wait for a bug fix like this one?

I read this thread: [http://www.nvnews.net/vbulletin/showthread.php?t=75129&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=75129&page=3)
It talks about a new set of drivers.  Where can I find information about these and if they have been released?  If they have been released, how would I use them?

---

### Post by elv on 2007-01-14
Been watchin this thread for awhile now and finally got sound working on my Gateway.So thanks alot to usergentoo for his howto.

---

### Post by darkhatter on 2007-01-14
> **elv said:**
> Been watchin this thread for awhile now and finally got sound working on my Gateway.So thanks alot to usergentoo for his howto.

what model do you have?

---

### Post by elv on 2007-01-15
> **darkhatter said:**
> what model do you have?

The MX6426

---

### Post by zvandiver on 2007-01-16
Alsa has posted version 1.0.14rc2 as of today.  The documentation specifically mentions the SigmaTel chips and Gateway laptops.
Quote:   Module snd-hda-intel
            STAC9202/9250/9251
	       ref		Reference board, base config
	       m2-2		Some Gateway MX series laptops
	       m6		Some Gateway NX series laptops

I will post results after installing.
Zane

---

### Post by brandoncolorado on 2007-01-16
> **zvandiver said:**
> Alsa has posted version 1.0.14rc2 as of today.  The documentation specifically mentions the SigmaTel chips and Gateway laptops.
Quote:   Module snd-hda-intel
            STAC9202/9250/9251
	       ref		Reference board, base config
	       m2-2		Some Gateway MX series laptops
	       m6		Some Gateway NX series laptops

I will post results after installing.
Zane

Awesome!  I hope it works.  If it does can you give me some pointer for installing?

Appreciate it!

---

### Post by zvandiver on 2007-01-16
I compiled the new alsa drivers/libs/firmware/plugins/utils and modified the /etc/modprobe.d/alsa-base file to identify the laptop model.
The new alsamixer showed the options for surround sound and front speakers that I didn't have before, but I still do not get any sound.  Also, when I rebooted, alsamixer would not start giving an error message "function snd-mixer-load failed: Invalid argument".
I had hoped this new release would work since it listed options for Gateway laptops.
I guess I will have to wait for the next alsa update.
Zane

---

### Post by zvandiver on 2007-01-16
Donn just gave me this tip from this thread:
[http://www.ubuntuforums.org/showthread.php?p=2022926#post2022926](http://www.ubuntuforums.org/showthread.php?p=2022926#post2022926)
and it worked!
You may need to add this to your /etc/modprobe.d/alsa-base file at the end.
 
 
Quote:
 alias snd-card-0 snd-hda-intel
 options snd-hda-intel model=test enable-msi=1 probe-mask=1 

 Donn
Thanks again to Donn.
Zane

---

### Post by darkhatter on 2007-01-16
any news on the stac9200......:sad:

---

### Post by brandoncolorado on 2007-01-18
> **darkhatter said:**
> any news on the stac9200......:sad:

The Bug Report hasn't moved a tad since August.

---

### Post by darkhatter on 2007-01-18
has anyone tried Solaris or Bsd....I'm starting to get sick of this...

---

### Post by zvandiver on 2007-01-19
darkhatter,
This is the quote from the Alsa-Configuration.txt file included with the latest alsa drivers, 1.0.14rc2.

STAC9200/9205/9220/9221/9254
	  ref		Reference board
	  3stack	D945 3stack
	  5stack	D945 5stack + SPDIF

Have you tried listing the 3stack option in your /etc/modprobe.d/alsa-base file?
You might also try adding the listing in my earlier reply #46.
Zane

---

### Post by susiekins on 2007-01-29
I was following usergentoo's instructions, but at "mv /etc/modprobe.d/alsa-base.bak /etc/modprobe.d/alsa-base", it turned out both files are missing, alsa-base.bak and alsa-base. I checked the system authentication logs for when i made the back-up with sudo, and I didn't misspell anything [I don't remember any errors], so I'm not really sure what happened, [I'm pretty new to linux]. Is there a way to recover these files, or am I simply looking in the wrong directory [/etc/modprobe.d]?

---

### Post by darkhatter on 2007-01-29
> **zvandiver said:**
> darkhatter,
This is the quote from the Alsa-Configuration.txt file included with the latest alsa drivers, 1.0.14rc2.

STAC9200/9205/9220/9221/9254
	  ref		Reference board
	  3stack	D945 3stack
	  5stack	D945 5stack + SPDIF

Have you tried listing the 3stack option in your /etc/modprobe.d/alsa-base file?
You might also try adding the listing in my earlier reply #46.
Zane
'
I'm going to try again, I'm kind of noobish when it comes to alsa, what should I add the the final line?

---

### Post by zvandiver on 2007-01-30
> **darkhatter said:**
> '
I'm going to try again, I'm kind of noobish when it comes to alsa, what should I add the the final line?

darkhatter,
I will post my alsa-base file for you tomorrow as an example.
Zane

---

### Post by zvandiver on 2007-01-31
darkhatter,
Here is my alsa-base file.
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# options snd-hda-intel model=m2
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=test enable-msi=1 probe-mask=1

In the last line where it says "model=test" put 3stack in place of test.
Zane

---

### Post by darkhatter on 2007-01-31
thanks zvandiver, I'll reinstall (k)ubuntu, and try it again.

bugzilla update:

the mic works (still no sound) alsa rc2
not compiling any alsa gets system beeps from the speaker

---

### Post by brandoncolorado on 2007-02-04
Have you tried 1.0.14 RC2?

---

### Post by blackrob on 2007-02-05
*Make sure that external amplifier is OFF in alsamixer( Press  'm' and till it has 'mm'). This gave my gateway sound :)  *

---

### Post by brandoncolorado on 2007-02-05
> **blackrob said:**
> *Make sure that external amplifier is OFF in alsamixer( Press  'm' and till it has 'mm'). This gave my gateway sound :)  *

Do you mean in alsamixer?  When I do this, it makes my master channel mute.

---

### Post by Serenader on 2007-02-05
Do we have any hope any time soon. I am itching to go back to Linux, but can't do that until I get back sound.

---

### Post by brandoncolorado on 2007-02-05
> **Serenader said:**
> Do we have any hope any time soon. I am itching to go back to Linux, but can't do that until I get back sound.

I think there is an off chance with 1.0.14RC2 because the model is mentioned in the documentation.  However, I am not able to compile it and install it as I am a linux noob.

---

### Post by nodows on 2007-03-04
Any luck anyone?  Serenader specifically?  I have the same setup as you (Gateway mx3416).  I've tried all the different methods on this post and others, and still no luck.  I even recompiled the 2.6.20 kernel and still no luck.    Any help would be greatly appreciated... this no sound thing is really startin to get old...

---

### Post by Aaronb2245 on 2007-03-04
I just fixed the sound on my gateway laptop. Go here and read this this is worked for me and I almost promise it will for you.

[http://www.goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/](http://www.goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/)

Enjoy your snd. I jumped for joy when I heard Motorhead play after 1 1/2 days trying diff things.

Aaron

---

### Post by brandoncolorado on 2007-03-04
For anyone with the MX3414, or the MX3416.  I have verified that this is a bug.  Upgrading to 1.0.14RC2 will yield no results.  The problem lies in ALSA and is currently being worked on.  The best advice I can give is to find the bug reports and to add your name to them so that the community knows about this problem.

---

### Post by Russell Doucette on 2007-03-09
Yah I'm pretty sure it's a major flaw in ALSA as well.  I heard of some poeple on the internet claiming they had custom-patched some source code and got sound out of their speakers, but it was real crappy quality and unstable, and would cause the kernel to panic or something like that.  Actually I don't think it's customized patches, I believed they used the newest CVS snapshot at that time.

BTW I have a Gateway MX3410.  The soundcards are almost identical in a lot of the 34xx models, which is why so many people are having problems.

I still have a few things to try.  I guess we'll just have to wait until some good news comes out. :(

---

### Post by brandoncolorado on 2007-03-10
Do we know if 1.0.14 will make it out for Feisty?

---

### Post by Serenader on 2007-03-12
> **nodows said:**
> Any luck anyone?  Serenader specifically?  I have the same setup as you (Gateway mx3416).  I've tried all the different methods on this post and others, and still no luck.  I even recompiled the 2.6.20 kernel and still no luck.    Any help would be greatly appreciated... this no sound thing is really startin to get old...

Sorry nodows, I haven't had a chance to play around with Linux lately (though I miss it a lot). Too many other important things... :-)

---

### Post by brandoncolorado on 2007-03-12
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

---

### Post by Russell Doucette on 2007-03-12
Alsa-project's main page seems to be down.

Would anyone know on hand if there is a scheduled time for the release of 1.0.14, or at least a stable new release of the development version (rc4 or something)?

---

### Post by blazer34i on 2007-03-13
I have gone through all the hoops with Kubuntu on my MX3416, I downloaded all the patches from the ALSA site merged, compiled loaded, reloaded. Nothing. I sure hope they fix and release it soon.  I have found countless other post stating the same issues exist will other distros and various other gateway laptops. To Ubuntu's credit though, it installed all my other hardware just fine.

---

### Post by brandoncolorado on 2007-03-13
Sometimes I feel like this is a lost cause.  I have been tracking/posting/posting on bug sites/IRC'ing and offering to pay people to get this resolved since August when I got this laptop.  I am really frustrated.  I know that the bug has been posted twice on ALSA's bug site, and I know that Ubuntu's ALSA maintainer knows of it.  I don't blame them, there is a lot to do, but I want to get this fixed, and I don't see it happening.

:( :confused:

---

### Post by darkhatter on 2007-03-13
> **brandoncolorado said:**
> Sometimes I feel like this is a lost cause.  I have been tracking/posting/posting on bug sites/IRC'ing and offering to pay people to get this resolved since August when I got this laptop.  I am really frustrated.  I know that the bug has been posted twice on ALSA's bug site, and I know that Ubuntu's ALSA maintainer knows of it.  I don't blame them, there is a lot to do, but I want to get this fixed, and I don't see it happening.

:( :confused:

I've been searching since aug as well and its really started to annoy me, I continue to check alsa every single day, I've been doing this for so long its just habit. I alsa opened a bug at the linux kernel bugzilla and that died as well.

I compiled the new alsa rc3 and got no luck, hopefully we'll rc4 will be good news

---

### Post by brandoncolorado on 2007-03-14
Maybe we can put some kind of bounty out on this bug's head.   haha

---

### Post by Russell Doucette on 2007-03-14
To tell you the truth, Linux support on laptops is literally crap.  I went into using Ubuntu on my MX3410 knowing that there would be some problem, and I wasn't suprised when my sound card didn't work.  64-bit or 32-bit, it's still the same thing.  It works beautifully on my tower at home.

I've also been hearing things about the microphone being able to work (referencing the ALSA bug ID 2469).  As I'm pretty sure the MX3414 has the same chipset, has anyone been able to confirm this?

---

### Post by blk_jack on 2007-03-15
> **darkhatter said:**
> I've been searching since aug as well and its really started to annoy me, I continue to check alsa every single day, I've been doing this for so long its just habit. I alsa opened a bug at the linux kernel bugzilla and that died as well.

I compiled the new alsa rc3 and got no luck, hopefully we'll rc4 will be good news

I have the same laptop as you guys and no luck for me either since August.  I just spent a good hour on rc3 and tried every combination with no luck.

Lets hope 9200 gets some more love in rc4, this bug has been open forever and I wish the alsa guys luck in finding a solution for us poor lunix users. :(

---

### Post by yamel on 2007-03-16
This advice seems to me to be incomplete and should be used with some caution.  It may be something peculiar to my system and a few others, but the second line (sudo apt-get --purge remove alsa-base alsa-utils) purges quite a bit of information.  Any glitch or failure to connect problems after that line will result in the loss of GUI and who-knows what else, as it has on my Gateway MX3414.

I think I'm to the point where I have to do a complete reinstall of my system.  Those of you with similar laptops will know what a chore it is to fix resolution, NVidia drivers, (sound!), etc.  A search of the above command in the forum reveals that I am not alone in this situation and no one seems to have found the solution.

Thanks.  Hope you'll all be able to rock on someday with full sound (if rocking on suits you.)

---

### Post by brandoncolorado on 2007-03-16
> **yamel said:**
> This advice seems to me to be incomplete and should be used with some caution.  It may be something peculiar to my system and a few others, but the second line (sudo apt-get --purge remove alsa-base alsa-utils) purges quite a bit of information.  Any glitch or failure to connect problems after that line will result in the loss of GUI and who-knows what else, as it has on my Gateway MX3414.

I think I'm to the point where I have to do a complete reinstall of my system.  Those of you with similar laptops will know what a chore it is to fix resolution, NVidia drivers, (sound!), etc.  A search of the above command in the forum reveals that I am not alone in this situation and no one seems to have found the solution.

Thanks.  Hope you'll all be able to rock on someday with full sound (if rocking on suits you.)

One trick for this laptop that made my life easier was to get this for video drivers:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Best script ever, works wonders.  Let me know if you have other things that you can't get working.  Also, I heard back in another forum that the Wireless drivers are being updated which is huge for people like me that need signal strength!

---

### Post by Russell Doucette on 2007-03-17
> **yamel said:**
> Hope you'll all be able to rock on someday with full sound (if rocking on suits you.)

We're all waiting for that day :D

---

### Post by brandoncolorado on 2007-03-18
I wonder if this problem is just really complicated or something.  It seems as though the bugs get attention from people who know what they are talking about until a certain point and then they are just ignored.  Maybe it is one of those things.  :(

---

### Post by Russell Doucette on 2007-03-18
I agree, I haven't heard or read any status updates on the problem.  

I'm not too sure how it works, but I think the situation might be different for everyone if the chipsets are configured differently for every laptop, making a single driver that would work on every laptop impossible.  

Then again that's one of my theories, but I'd still like to see some sort of status update from time to time. :P

---

### Post by brandoncolorado on 2007-03-20
Can someone that handles ALSA bugs chime in?  Let us know what may be or what is the problem?

---

### Post by rabbi1337 on 2007-03-20
I've seen your bug report at ALSA and if my registration would ever work, I would chime in and report the same things you have. Maybe part of it is that nobody else is saying anything about your report so they pass it off as not really important because its just one guy or something...

---

### Post by darkhatter on 2007-03-20
so your also having problems signing up then. Cause it always gives me a error message and I don't get a email

---

### Post by lvleph on 2007-03-20
> **yamel said:**
> This advice seems to me to be incomplete and should be used with some caution.  It may be something peculiar to my system and a few others, but the second line (sudo apt-get --purge remove alsa-base alsa-utils) purges quite a bit of information.  Any glitch or failure to connect problems after that line will result in the loss of GUI and who-knows what else, as it has on my Gateway MX3414.

I think I'm to the point where I have to do a complete reinstall of my system.  Those of you with similar laptops will know what a chore it is to fix resolution, NVidia drivers, (sound!), etc.  A search of the above command in the forum reveals that I am not alone in this situation and no one seems to have found the solution.

Thanks.  Hope you'll all be able to rock on someday with full sound (if rocking on suits you.)

I can verify a loss of GUI. It sucked.

---

### Post by Russell Doucette on 2007-03-21
Alsa's registration system's half broken, it gave me some crap smtp error and robbed my username from me!  I can't use it anymore!

EDIT: I was wrong, it worked for me (this time).

---

### Post by rabbi1337 on 2007-03-21
I finally was able to get to brandoncolorado's entry to add my own comments to the alsa bugtracker. If you can, lets see if we can get some more attention to our problems so they don't think it's more or less an isolated incident.

the MX3414 issue:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

---

### Post by brandoncolorado on 2007-03-23
> **rabbi1337 said:**
> I finally was able to get to brandoncolorado's entry to add my own comments to the alsa bugtracker. If you can, lets see if we can get some more attention to our problems so they don't think it's more or less an isolated incident.

the MX3414 issue:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

here, here!

---

### Post by nvydis on 2007-04-14
any updates of the "STA9200" yet? i have MX3702.

aplay -l:
Card 0: SB [hda ati sb], Device 0: STA92xx analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
Card 0: SB [hda ati sb] , device 1: STA92xx Digital [STAC92xx Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

no sound! HELP!!!!!!!!!!!!!!!!!!!!!!! im a noobie.

---

### Post by richardhickling on 2007-04-21
Hi - have a look at this thread.  This may help with Ubuntu also:
[http://mepislovers.org/forums/archive/index.php/t-4721.html](http://mepislovers.org/forums/archive/index.php/t-4721.html)
Please post a reply if this works - I'm thinking of getting a MX3702.

---

### Post by blk_jack on 2007-04-21
I have a MX3414 and the audio chip is completely different than the replies to that link you posted.

---

### Post by LMelior on 2007-04-24
Nobody mentioned the MT3705 in this thread, which has the same problem.  I posted about some things I've tried in [this other thread]("http://ubuntuforums.org/showpost.php?p=2523872&postcount=16"), outside of all the typical fiddling with the options in alsa-base.

Hopefully some ALSA developer gets one of our laptops so this can be resolved.

---

### Post by dracflamloc on 2007-05-06
This seriously needs to be looked at! What the heck, no sound >=(

---

### Post by AJYablo on 2007-05-07
> **dracflamloc said:**
> This seriously needs to be looked at! What the heck, no sound >=(

Indeed.
I've got the same problem on my MX3422.

---

### Post by razzek on 2007-05-16
hello....i'm new on Ubuntu (Feisty Fawn)....and have the same problem  sound ....my Notebook is MX3416 and i already have the  alsa-drive,alsa-lib, and alsa-utils source.....and i tried to compile that but not works...or look that.....i tried to fallow some configurations of someones but not work....... i dunno if  this is because compile bad  the alsa-drivers or....if i am doing something wrong....

thanks for everthing

---

### Post by harmeet on 2007-05-18
Hey Guys

I almost forgot about this bug. I spent almost 4 weeks trying to make it work back in December 2006! Then I  bought USB travel speakers. Works great!! I haven't checked back again if this issue was resolved or not!

I bought these - [http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1176845&CatId=2891](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1176845&CatId=2891)

But, you can buy any USB speaker. Google "usb speakers" and you will see tons!

And the USB skype phones work great as well!

Hope this helps.

Harmeet

---

### Post by Andrewie on 2007-05-23
anyone try alsa 1.0.14rc4 ?

---

### Post by Andrewie on 2007-06-06
Alsa 1.0.14 has went stable, has anyone tried it. 

P.S. I'm going to try it and see what happens

---

### Post by blk_jack on 2007-06-08
Dang there are a ton of changes/bugfixes to the HDA codec... I'm gonna check this out too.

---

### Post by fairlie on 2007-06-08
Let us know how it goes :)
Have a feeling it wont work still though.

---

### Post by Serenader on 2007-06-09
I tried alsa1.0.14rc4, but no luck.

---

### Post by blk_jack on 2007-06-10
Just tried alsa1.0.14 (final?) with of course no luck.

Nothing has changed, same problems as before.  Appears as though there's sound, but no sound from headphones or speakers.  I have a Gateway MX3412 PC Notebook and I've been without sound for almost a year now.

What's the point of having bugtraq if something like this goes untouched for a year?

With releases coming every few months, I guess I'll wait around until after the summer to see if any progress has made.

If I had known this when I initially got the laptop, I definitely wouldn't have bought it.

---

### Post by thorpe@gte.net on 2007-07-10
I also have a Gateway Laptop MX3416 that has Freespire 2.0 Ubuntu release on it, and no sound.  I took the advice and bought USB Triton Sound Bite speakers and still no sound.   Does anyone know how to get this working either thru the laptop or USB speakers ?

Ray:confused:

---

### Post by asetSDU on 2007-08-15
YES..
MT3705 I got Audio drivers..:guitar:

---

### Post by Andrewie on 2007-08-15
I've been watching the bug for a year. I can't believe its been a year :(. They haven't solved the problem but they are getting closer.

---

### Post by Nu-Buntu on 2007-08-20
> **asetSDU said:**
> YES..
MT3705 I got Audio drivers..:guitar:So you got Ubuntu working with sound on the MT3705? How'd you do it? I am also in need of this fix.

---

### Post by Robbie Pence on 2007-08-21
I have a gateway mx6453 laptop, with sigmatel audio.
When I installed Ubuntu, it worked with sound,
but when I updated, it stopped working...

Can I downgrade ALSA? How?
Would it help?

---

### Post by Andrewie on 2007-08-22
> **Robbie Pence said:**
> I have a gateway mx6453 laptop, with sigmatel audio.
When I installed Ubuntu, it worked with sound,
but when I updated, it stopped working...

Can I downgrade ALSA? How?
Would it help?

that is really weird :confused: which kernel are you using?

---

### Post by Robbie Pence on 2007-08-23
I'll have to check GRUB, but whatever one 7.04 uses. 
Sorry for soundling noobish.

---

### Post by Robbie Pence on 2007-08-23
If I try copying the original ALSA from the disc, and replacing
the new one, would it work?

Also, I've heard of other ALSA like sound managers;
any way to try those?

---

### Post by Andrewie on 2007-08-23
> **Robbie Pence said:**
> If I try copying the original ALSA from the disc, and replacing
the new one, would it work?

Also, I've heard of other ALSA like sound managers;
any way to try those?

if you want to use the alsa drivers you have to remove the alsa drivers out of your kernel.

---

### Post by Robbie Pence on 2007-08-23
I tried that, running as root, but it wouldn't even let me open the .deb.

---

### Post by Andrewie on 2007-08-23
> **Robbie Pence said:**
> I tried that, running as root, but it wouldn't even let me open the .deb.

you have to recompile your kernel, and remove the alsa sound system. Then you need to compile the alsa drivers against you new kernel. Its not a easy task.

---

### Post by brandoncolorado on 2007-08-24
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

---

### Post by thorpe@gte.net on 2007-08-25
Well I got some usb speakers and i can get sound if I use xmms and pick the usb speakers in configuration and save it.  However, how do I get the system to default to the usb speakers as xmms is the only program that has this option, so basically I get sound on xmms and nothing else :(

Ray  :confused:

---

### Post by Robbie Pence on 2007-08-25
Ugh...yeah. There's no easier way unless you're a GCC wizard, huh?
Geez. I'm surprised that linux doesn't have a better driver manager yet...

I reinstalled Ubuntu, I had sound until I updated. I accidently did sudo apt-get upgrade before I remembered to de-tick  ALSA...crud.  

I'll try one more time....

---

### Post by asetSDU on 2007-08-28
> **Nu-Buntu said:**
> So you got Ubuntu working with sound on the MT3705? How'd you do it? I am also in need of this fix.

how can i share them????????????

---

### Post by Robbie Pence on 2007-09-01
Oh well. I guess it's part of another update, then.
I couldn't detick it. 

I did notice a kernel update today...
I'll see if it has sound.

---

### Post by ackray on 2007-09-03
Gateway MT3705

 alsa-driver-1.0.15rc1

Still no joy.

---

### Post by Andrewie on 2007-09-09
THE BUG IS FIXED!!!!!!!!!!!!!!!!!!!!!

I now have sound on my Gateway MX3410

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

:guitar:

---

### Post by blk_jack on 2007-09-12
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

Problem solved (except microphone??)!  After a year we finally have closure..!

I have a Gateway MX3412 and this fixed my problem.  It will solve the sound problem for many other Gateway / STAC9200 users as well.

---

### Post by Andrewie on 2007-09-12
> **blk_jack said:**
> [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

Problem solved (except microphone??)!  After a year we finally have closure..!

I have a Gateway MX3412 and this fixed my problem.  It will solve the sound problem for many other Gateway / STAC9200 users as well.

now for the wireless(wpa) and sleep problem :(

---

### Post by blk_jack on 2007-09-12
My wireless has been working since close to the start.  I just used ndiswrapper and the rest is history...

The native realtek linux driver caused too many problems I'm afraid.  As for sleep, well, it worked/works great, with the exception of when I used beryl in hte past.  I haven't tried it in forever, though, so I have no idea how it works with Compiz Fusion

---

### Post by Andrewie on 2007-09-12
> **blk_jack said:**
> My wireless has been working since close to the start.  I just used ndiswrapper and the rest is history...

The native realtek linux driver caused too many problems I'm afraid.  As for sleep, well, it worked/works great, with the exception of when I used beryl in hte past.  I haven't tried it in forever, though, so I have no idea how it works with Compiz Fusion

I can get the wireless to work, but when I use ndiswrapper I can't use the nvidia driver, and ubuntu 7.04 gets my laptop to sleep but the screen doesn't come back. I know it turns back on because the keyboard ligts turn on and off when I hit cap-lock

---

### Post by Robbie Pence on 2007-09-13
> **blk_jack said:**
> [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

Problem solved (except microphone??)!  After a year we finally have closure..!

I have a Gateway MX3412 and this fixed my problem.  It will solve the sound problem for many other Gateway / STAC9200 users as uwell.

How do I get the ALSA update?
I did a normal update, still no sound...
help please. I'm sick to death of Windows....
Now DVD's won't play under windows.... and I know it's not
hardware, tested with a livecd...:confused::confused:

---

### Post by blk_jack on 2007-09-13
You need to go here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036) and download the last two attachments with the bug.  The first I think is the patch and the second is a text file which tells you what to do.  Also read the thread on the bug and you should have it up in no time.

---

### Post by abeppu on 2007-09-16
Is anyone else having difficulty with the patch(es)?  I tried both of them, and am still without sound.  The patch definitely did something, however; my I can hear clicks out of my mic jack when I adjust the volume.  When I try to test playback in sound preferences, selecting ALSA, it gives me the following error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

I get the same thing when I select STAC92xx Analog or Digital.  Selecting OSS doesn't produce an error, but no sound either.  

I'm hoping I just have some configurations somewhere set wrong -- any suggestions?

---

### Post by Andrewie on 2007-09-16
> **abeppu said:**
> Is anyone else having difficulty with the patch(es)?  I tried both of them, and am still without sound.  The patch definitely did something, however; my I can hear clicks out of my mic jack when I adjust the volume.  When I try to test playback in sound preferences, selecting ALSA, it gives me the following error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

I get the same thing when I select STAC92xx Analog or Digital.  Selecting OSS doesn't produce an error, but no sound either.  

I'm hoping I just have some configurations somewhere set wrong -- any suggestions?

what model of laptop are you using?

---

### Post by blazer34i on 2007-10-03
After following the thread at alsa bugtrack:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036")

I now have sound on the MX3416 laptop.  My advice is to read the thread carefully to apply the patch and configure the files. The patch  covers several models of laptops. 

I used  Fiesty Fawn 7.04 for the distro (Kubuntu). I tested the beta version of Gutsy Gibbon 7.10 before going this route in hopes that the patch or fix made it to the new version but I had no sound with Gutsy either. Since this was going to be a semi-permanent installation I wanted to go with a more mature verison.

 The files I used were:

[1.0.15rc1 Patch]("https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2229&type=bug")

[1.0.15rc1 patch instuctions - Copy and paste the command lines]("https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2230&type=bug")

[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc1.tar.bz2)
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2) 

You will have to install the following packages to build properly:

build-essential 
gettext
ja-trans
libncurses-dev

You will have to remove:

alsa-base

Also note that after building alsactl is locate in the wrong directory. 

You can link between /usr/sbin/alsactl and /sbin/alsactl 
or just replace the version in /sbin with the new one located in /usr/sbin/. I chose to replace the older version 1.0.13 with the new one and it worked fine. 

Thanks to everyone that has worked on the problem. I have owned the mx3416 since Dec 06 and this is the first time I have had sound on this laptop. Now I can link to my MythTV box!!!

---

