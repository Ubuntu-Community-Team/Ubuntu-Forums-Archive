---
title: "Lenovo g555 headphone and mic jack issues"
date: 2010-08-04
forum: Hardware
---

### Post by p2ranger on 2010-08-04
I've seen a number of other threads where others have had problems getting the jack sense to work with their headphone and mic jacks on their laptop. I've read a  number of the threads and tried some of their solutions but I'm still not getting it to work right. 

I have a Lenovo g555 laptop that I recently put Ubuntu 10.4 on. I have a headset that plugs into the microphone and headphone jacks. It worked just fine on my old dell laptop with Ubuntu 9.10 on it.

Now, when I plug it into the jacks, the laptop speakers don't shut off. Also, I can't get it to detect that the microphone is plugged in. I've tried using GNOME Alsamixer. With that, I can cut off the microphone for the computer, but I can't get it to pick up from the microphone that is plugged in.

Quite honestly, I'm not sure what the labels for each slider correspond to. 

Master - I assume is the main volume control
PCM - I think that goes with the laptop speakers. moving that up and down changes the volume of sound coming out of there.However, it also changes the sound coming out of the headphones.
Front Mi - I'm assuming this is the microphone jack
Mic - the controls for this seem to mute and unmute the external laptop microphone

Currently, the sound does come out of the headphones, but it also comes out of the laptop speakers at the same time.

How do I go about getting jack sense to work in a way that turns off the laptop speakers when headphones are plugged in.
How do I go about getting the microphone jack to pick up on my headset?

Thanks for any help

Jason

---

### Post by p2ranger on 2010-08-06
bump

---

### Post by utilitytrack on 2010-08-06
1) What you did (what solutions you tried)
2) Post output of these commands:

```
$ uname -r
$ dpkg -l alsa-*
$ lspci -nn | grep Audio
$ cat /proc/asound/card0/codec#0 | grep Codec
$ cat /etc/modprobe.d/alsa-base.conf
# hwinfo --sound
```

and your PC/laptop model

---

### Post by p2ranger on 2010-08-08
I followed lidex's suggestion here:
[http://ubuntuforums.org/showpost.php?p=9570213&postcount=4](http://ubuntuforums.org/showpost.php?p=9570213&postcount=4)
That included editing the alsa-base.conf file by adding the following:

```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
```

I changed around the alsa mixer settings. I tried doing it by using the alsamixer command in the console. 

I also got the gnome alsamixer interface that someone else suggested. I think it just does the same thing, but a different interface. I used that to check and uncheck Rec. for the Front Mi and Mic settings. If I check Rec. for Mic, it picks up audio. I don't know if its picking up audio from the headset or from the laptop mic. The only problem is that causes echo for the person on the other end as it seems to be picking up audio from the laptop speakers as well. When I check Rec. for Front Mi and uncheck Rec. from Mic it doesn't pick up any audio at all.

I've also tried adjusting the microphone sliders and haven't gotten that to work the way I want. My guess is that when I plug into the jacks, for some reason its not turning off the laptop speakers and mic.

So something isn't working correctly, and I am at a loss as to how to fix it.

Here's the output for the commands you asked me to do:

```
2.6.32-24-generic

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  alsa-base      1.0.22.1+dfsg- ALSA driver configuration files
un  alsa-oss       <none>         (no description available)
ii  alsa-utils     1.0.22-0ubuntu ALSA utilities

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]

Codec: Conexant ID 5069

----------------------------------------------------------------
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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

#added from ubuntuforums.org
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

------------------------------------

20: PCI 14.2: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4383
  Unique ID: 5Dex.j3SXOQfquFE
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia (Intel HDA)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 "SBx00 Azalia (Intel HDA)"
  SubVendor: pci 0x17aa "Lenovo"
  SubDevice: pci 0x3938 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xd2400000-0xd2403fff (rw,non-prefetchable)
  IRQ: 16 (237565 events)
  Module Alias: "pci:v00001002d00004383sv000017AAsd00003938bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

The laptop is a Lenovo G555

Thanks for your help

Jason

---

### Post by Yellow Pasque on 2010-08-08
Bug is documented here: [https://bugzilla.redhat.com/show_bug.cgi?id=612769](https://bugzilla.redhat.com/show_bug.cgi?id=612769)

---

### Post by simosx on 2010-08-08
> **utilitytrack said:**
> 1) What you did (what solutions you tried)
2) Post output of these commands:

```
$ uname -r
$ dpkg -l alsa-*
$ lspci -nn | grep Audio
$ cat /proc/asound/card0/codec#0 | grep Codec
$ cat /etc/modprobe.d/alsa-base.conf
# hwinfo --sound
```

and your PC/laptop model

I think it's better to ask users to run alsa-info.sh from the Alsa-Project.org website. It includes the information you ask and much more.

To run alsa-info.sh,

[FONT="Courier New"]wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
[/FONT]

You are prompted to send the details to the alsa-project.org website; select Yes and write down the URL you will be given. This URL has your soundcard information; reply here with this URL.

---

### Post by utilitytrack on 2010-08-08
> **simosx said:**
> I think it's better to ask users to run alsa-info.sh from the Alsa-Project.org website. It includes the information you ask and much more.

No. I very good know about this script, my friend. But I think that it is important that users learn to work with the command line.

---

### Post by Zircon12 on 2010-08-22
Has anyone found a solution to this problem yet? I have tried so many different things to get my laptop working I am about to go insane :mad:.

Here are the details on my system:

[http://www.alsa-project.org/db/?f=90811e099107267fe1b43c10bc43a36d08bfa081](http://www.alsa-project.org/db/?f=90811e099107267fe1b43c10bc43a36d08bfa081)

Chip-set: AMD M880G
laptop: Lenovo G555
Codec: Conexant CX20585

I am miffed right now as to what to do I have attempted just about every model there is available in the HD-audio-models.txt. So far none of them have done anything to improve the status of my sound system. 

A little bit of history on what I have done so far. My system started out just like p2ranger's was. Running ALSA 1.0.22.1+dfsg and Conexant ID 5069. When it was in this state I was having the exact same problem with the HP's playing without shutting off the external speakers. I messed with the various  models from the the above mention txt file placing them in gedit /etc/modprobe.d/alsa-base.conf using the snd code: snd-hda-intel model=xxxxx. I was unable to have any success with any of these settings. I however found the ALSA update script and updated to version 1.0.23. At this point my Codec changed over to Conexant CX20585. Now I can play music out of the speakers, but no sound from the head phone unless I go into the HDA analyzer and manually activate node 0x19 for OUT and HP. This only allows sound to come out of the headphones though and still has no effect on deactivating the external speakers..... I have tried all of the same, and more models in the snd command with no improvement. 

What bothers me is that by changing the ALSA version the codec changed. I would have assumed that the codec wouldn't vary since it should be standardized by the BIOS or so I have read. Also according to this site: [http://www.zdnet.com/reviews/product/laptops/lenovo-g555-087326u-black-amd-athlon-ii-x2-dual-core-m320-210ghz-3200mhz-1mb/34115555](http://www.zdnet.com/reviews/product/laptops/lenovo-g555-087326u-black-amd-athlon-ii-x2-dual-core-m320-210ghz-3200mhz-1mb/34115555) the codec is supposed to be CX20561...... Is there a way that I can force ALSA to run this codec or am I proverbially up S*** creek without a paddle?

I have been trying to work this out for about 3 days now, and I haven't gotten made any progress. I know there has to be something that I can do, but being fairly new to Linux I know I am missing it. Thank you guys for any help you can provide.

---

### Post by Zircon12 on 2010-08-22
Ahhh I feel like an idiot now, after a little break and some fresh reveiwing I happened across some interesting information in the file /usr/share/alsa/init/HDA, it mentions two codecs one for the realtek ALC880, and the other Analog Devices AD1984. For ALC880 it say if true go too Acer travelmate 8100, and for AD1984 go to Lenovo T61. By referring to HDA-audio-models.txt I found that the Lenovo T61 thinkpads model ID was thinkpad. By inserting that into snd-hda-intel model=thinkpad I managed to get the computer sound working exactly like its supposed too. 

Overall the simple quick-fix for the HP detection problem with Lenovo G555 is to:

1.) Upgrade your Alsa kernal to 1.0.23 using the update script found here: [http://ubuntuforums.org/showthread.php?]("http://ubuntuforums.org/showthread.php?p=6589810")p=6589810 

2.) run sudo gedit /etc/modprobe.d/alsa-base.conf and add this line to the bottom: snd-hda-intel model=thinkpad 

3.) restart your computer, and walla!! Your sound system will be running like a charm!

I cant believe took me nearly three days to figure this out #-o....

---

### Post by geadamson on 2010-08-28
I want to use earphones and turn off speakers.  I have a lenovo G555 
Ubuntu started with kde but  alternate between xfce and kde.
updated to  10.0.023 Alsa 
Before up date both  earphones and speakers worked but speakers would not work now earphones do not work. 
 ]geo@geo:~$ uname -r
2.6.32-24-generic
geo@geo:~$ dpkg -l alsa-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  alsa-base                1.0.22.1+dfsg-0ubuntu3   ALSA driver configuration files
un  alsa-headers             <none>                   (no description available)
un  alsa-oss                 <none>                   (no description available)
ii  alsa-utils               1.0.22-0ubuntu5          ALSA utilities
geo@geo:~$ lspci -nn | grep Audio
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
geo@geo:~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Conexant CX20585
geo@geo:~$ 
geo@geo:~$ cat /ect/modprobe.d/alsa-base.conf
cat: /ect/modprobe.d/alsa-base.conf: No such file or directory
#hwinfo  --sound (nothing happened_)
thanks for the help

---

### Post by lidex on 2010-08-29
> **geadamson said:**
> I want to use earphones and turn off speakers.  I have a lenovo G555 
Ubuntu started with kde but  alternate between xfce and kde.
updated to  10.0.023 Alsa 
Before up date both  earphones and speakers worked but speakers would not work now earphones do not work. 
 ]geo@geo:~$ uname -r
2.6.32-24-generic
geo@geo:~$ dpkg -l alsa-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  alsa-base                1.0.22.1+dfsg-0ubuntu3   ALSA driver configuration files
un  alsa-headers             <none>                   (no description available)
un  alsa-oss                 <none>                   (no description available)
ii  alsa-utils               1.0.22-0ubuntu5          ALSA utilities
geo@geo:~$ lspci -nn | grep Audio
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
geo@geo:~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Conexant CX20585
geo@geo:~$ 
geo@geo:~$ cat /ect/modprobe.d/alsa-base.conf
cat: /ect/modprobe.d/alsa-base.conf: No such file or directory
#hwinfo  --sound (nothing happened_)
thanks for the help
Your directory name is misspelled and our alsa is an older version. Let me capsulize for you. First, if you have alsa-backports installed, remove it. Now upgrade your alsa install using the alsa-upgrade link in my sig. Finally, do this using copy-and-paste for the terminal commands. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=thinkpad  
```
Save. Close. Reboot. 
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

### Post by geadamson on 2010-08-29
thanks for the help, by the time I got your advice and reinstalled ubuntu- this time I went with xubuntu..
all is well except still have the orginal problem.  Cannot mute main speakers, .....followed you instructions,  pasted the thinkpad line to bottom of correct file.  All is well except cannot mute earphones which should mute when eaphones are pluged in...

Codec is cx 20585
machine lenovo g555
Device ati 0403
             hdi 4383
 Only one drive is offered when running alsamixer in terminal

any help would be appreaciated, 
Sorry to be so much trouble.

---

### Post by lidex on 2010-08-29
No trouble. Try changing thinkpad to dell-vostro in alsa-base.conf
You'll need to reboot to see changes. You may still need a newer alsa version.

---

### Post by geadamson on 2010-08-30
thanks the upgrade to alsa 10.0.23 did it.  I am so happy!

---

### Post by lidex on 2010-08-30
Sweet. Please mark thread solved using 'Thread Tools' up top.

---

### Post by martula on 2010-09-03
I followed all the steps Zircon12__ mentioned and I solved the speakers issue, but the microphone still doesn't work. Any ideas?

Thanks!

---

### Post by deokisu on 2010-09-28
I did everything as it was stated in the previous posts, but my microphone now doesn't work at all. It worked before, but my headphones didn't and now situation is opposite. Please, if anyone found solving to this problem, submit it here so people like me could easily resolve it. Thank you.

---

### Post by lidex on 2010-09-29
> **deokisu said:**
> I did everything as it was stated in the previous posts, but my microphone now doesn't work at all. It worked before, but my headphones didn't and now situation is opposite. Please, if anyone found solving to this problem, submit it here so people like me could easily resolve it. Thank you.
Copy and paste this command into a terminal and press enter. When you are prompted to upload your info enter Y and press enter key. You will be given a link to the uploaded data. Provide the url please.

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh

```

---

### Post by deokisu on 2010-09-29
Here is my [link]("http://www.alsa-project.org/db/?f=c79b2f3cc5d51f094ed6af311ae0e4828f227517"). Thank you for helping.

---

### Post by lidex on 2010-09-29
> **deokisu said:**
> I did everything as it was stated in the previous posts, but my microphone now doesn't work at all. It worked before, but my headphones didn't and now situation is opposite. Please, if anyone found solving to this problem, submit it here so people like me could easily resolve it. Thank you.
You somehow have 2 models selected. How did you update your alsa install and what is this output:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by deokisu on 2010-09-29
I am dealing with this problem for a long time and did a lot to make everything work. Anyway here is the output.

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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=thinkpad
```

---

### Post by lidex on 2010-09-29
Can you post any output from this command please:
```
cat /etc/modprobe.d/sound.conf 
```

---

### Post by deokisu on 2010-09-29
```
cat: /etc/modprobe.d/sound.conf: No such file or directory

```

---

### Post by LeapingLlama on 2010-09-29
I had the same bug on my Lenovo G555 where the speakers didn't mute when headphones were plugged in, and my mic didn't work. I DID find a solution, however, that lets me use both my headphones and mic properly.

There are three steps, and I don't know if they have to be done in any particular order, so I'll give the order I used.
1) I ran the upgrade script from [lidex's sig]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810").

2) I added the following lines to the end alsa-base.conf:
```
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
```
If you are unsure how to edit alsa-base.conf, open a terminal and run the following command:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
You should end up with a text editor. Copy the two lines mentioned above into the bottom of the file, and exit, saving your changes.

3) My final step involved downloading and installing the linuxant driver. You can find the .deb package you need [here]("http://www.linuxant.com/alsa-driver/").

You must now reboot. A reboot might also be required after each step.

I do not know how this approach fixes the sound, but it does. Your speakers should mute when you plug in your headphones. To use the mic however, there is one more small step, no downloading or installing required.

Open a terminal and run alsamixer (just type the word alsamixer and press enter). You will have to press F4 to switch to the capture options. There, you will have to navigate to the last column on the right with your arrow keys, then press the up or down arrow keys until "Mic_B" is selected. You may also need to increase one of the amplification options for the mic to pick up any noise. No reboot required for this step. (Check the attached screenshot to see what it should look like).

This approach has worked for me, and I hope it will also work for any others of you who had the same frustrating problem as me. Hope this helps!

Additional Info I left out:
For some reason, after upgrading to a newer kernel, the sound once again stops working properly. You may need to repeat the above procedure every time you update you kernel, or just refrain from updating.

---

### Post by Yellow Pasque on 2010-09-29
If that works for you, then after there's a kernel update, mark the linuxant.deb package for reinstallation. After that, you'll need to restart (or restart alsa using init script).

---

### Post by LeapingLlama on 2010-09-30
> **Temüjin said:**
> If that works for you, then after there's a kernel update, mark the linuxant.deb package for reinstallation. After that, you'll need to restart (or restart alsa using init script).

Yep, that did the trick ^_^

---

### Post by deokisu on 2010-10-01
Thank you very much for solving the problem i've been dealing with for a long time.

---

### Post by p2ranger on 2010-10-07
Wow, thanks so much for how to outline the fix. It works on my Lenovo G555 now too. Will have to see what happens with the next updated as you stated. One question, do you have to go through all three of your steps to get it to work again, or just some of them.

Thanks

Jason

---

### Post by lidex on 2010-10-07
> **p2ranger said:**
> Wow, thanks so much for how to outline the fix. It works on my Lenovo G555 now too. Will have to see what happens with the next updated as you stated. One question, do you have to go through all three of your steps to get it to work again, or just some of them.

Thanks

Jason

Should work just re-installing linuxant driver.

---

### Post by Gabbodo on 2011-01-06
> **Zircon12 said:**
> Ahhh I feel like an idiot now, after a little break and some fresh reveiwing I happened across some interesting information in the file /usr/share/alsa/init/HDA, it mentions two codecs one for the realtek ALC880, and the other Analog Devices AD1984. For ALC880 it say if true go too Acer travelmate 8100, and for AD1984 go to Lenovo T61. By referring to HDA-audio-models.txt I found that the Lenovo T61 thinkpads model ID was thinkpad. By inserting that into snd-hda-intel model=thinkpad I managed to get the computer sound working exactly like its supposed too. 

Overall the simple quick-fix for the HP detection problem with Lenovo G555 is to:

1.) Upgrade your Alsa kernal to 1.0.23 using the update script found here: [http://ubuntuforums.org/showthread.php?]("http://ubuntuforums.org/showthread.php?p=6589810")p=6589810 

2.) run sudo gedit /etc/modprobe.d/alsa-base.conf and add this line to the bottom: snd-hda-intel model=thinkpad 

3.) restart your computer, and walla!! Your sound system will be running like a charm!

I cant believe took me nearly three days to figure this out #-o....


I have a Lenovo G555 too, and I'm having the exact problem with the mic and the head set, I updated the alsa thing, and before adding that line to the alsa-base.conf i checked on the sound option on system/preferences/sound to see how the input levels were, and i notices that they weren't grayed out anymore, and so i went on to add the line and restarted the computer, after that, i checked again the input levels, and they were grayed out and even audacity fails to record, i get an error message saying "Error while opening sound device. Please check the input device settings and the project sample rate." then i tried to erase the line a added, but it wont let me, I'm not an advance Ubuntu user so i don't know how to do it, any help?

---

### Post by lidex on 2011-01-06
> **Gabbodo said:**
> I have a Lenovo G555 too, and I'm having the exact problem with the mic and the head set, I updated the alsa thing, and before adding that line to the alsa-base.conf i checked on the sound option on system/preferences/sound to see how the input levels were, and i notices that they weren't grayed out anymore, and so i went on to add the line and restarted the computer, after that, i checked again the input levels, and they were grayed out and even audacity fails to record, i get an error message saying "Error while opening sound device. Please check the input device settings and the project sample rate." then i tried to erase the line a added, but it wont let me, I'm not an advance Ubuntu user so i don't know how to do it, any help?

Enter this in a terminal and copy and paste the text output in your next post
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by Trollinger on 2011-02-23
Hello there,
I've read every page of this site and tried everything. Two problems occur:

1. The update for alsa is no longer available. 
2. I do not get access to the text document which is supposed to be edited. And i am not the owner, so i cannot do anything about that.

Can someone help me with this problems?

Edit: No access meaning i cant edit that. It is protected.
Edit2: The Cat-command made me find out that my alsa version actually is 1.0.23, so i guess i dont need the update. A pity that doesnt help me with the write protection of the alsa-conf file

Edit3: The gksu command enabled me to edit the file. I dont see much logic in that, but i wont complain...

Edit4: I typed the 2 commands,

options snd_hda_intel model=laptop 
options snd-hda-intel position_fix=1 enable=yes

and i want to continue with the 3rd step, downloading and installing the linuxant drivers. Download is no problem (I assume i was supposed to chose the .deb package), but at the end of the install process i get an error of the installer and nothing changes. I guess thats the reason why nothing happens with my jacks.
The error tells me that there is a mistake in aptdaemon.

Okay, i found my mistake. I installed the unstable, newer version of Ubuntu. I've downloaded the stable version and your guide works. Thanks!

---

### Post by Burnout54 on 2011-03-15
I got the jacks to work using linuxant... but I can't figure out how to get the build-in(webcam) mic to work.

---

### Post by frizzo on 2011-04-01
Upgrade your kernel to 2.6.38 version thru ppa:

[https://sites.google.com/site/lightrush/random-1/howtoinstalllinuxkernel2638onubuntu1004lucidfromubuntu1104nattytheeasyway](https://sites.google.com/site/lightrush/random-1/howtoinstalllinuxkernel2638onubuntu1004lucidfromubuntu1104nattytheeasyway)


or downloading deb packages for your architecture :

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-natty/")

Then for graphic cards that use proprietary drivers only , 

here for nvidia:

[https://sites.google.com/site/lightrush/random-1/updatenvidiabinarydriverinubuntulucidormaverickviappa](https://sites.google.com/site/lightrush/random-1/updatenvidiabinarydriverinubuntulucidormaverickviappa)

here for ATi :

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1604-howto-install-ati-display-driver-in-ubuntu](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1604-howto-install-ati-display-driver-in-ubuntu)


Remember to install pavucontrol and enable the microphone as external audio input, unlock the channels and put one of them to zero level. 

Now microphone works great!

Enjoy !:popcorn:

---

