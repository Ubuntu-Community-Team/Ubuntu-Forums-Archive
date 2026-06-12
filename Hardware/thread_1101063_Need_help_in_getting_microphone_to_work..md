---
title: "Need help in getting microphone to work."
date: 2009-03-19
forum: Hardware
---

### Post by abrahamt on 2009-03-19
Hey everyone, I am a relative newbie to Ubuntu and I am having some trouble getting my microphone to work. I am currently using a Dell Inspiron 1318 notebook and the Intrepid Ibex release of Ubuntu. I am very unfamiliar with entering commands within the console and I think I am gonna need some step by step instructions. My web cam, bluetooth, wireless all work fine. Can anyone help me? I am really wanting to ditch the windows platform.

Abraham
[email]abrahamtorres@live.com[/email]

---

### Post by teamsuperoxide on 2009-04-01
Hi, I have the same problem with the same laptop! The microphone is not working. I'm running Ubuntu 8.04 (Hardy Heron?).

How did you get bluetooth and WiFi to work? Both were not working on Windows so I've changed to Ubuntu in hope that I can get them running.

---

### Post by Dportner on 2009-11-06
same problem... im running 9.10 tho

---

### Post by darshana on 2009-11-07
Open a terminal and type ```
alsamixer
```from there check whether the mic is muted.

or else right click on the volume control button on the gnome pannel and open the Volume control. Check whether the Mic is muted.

---

### Post by Dportner on 2009-11-09
i tried the alsamixer thing and in that i can only choose between line in or mic in...there is no mute or sound controlls for it :\...and in volume prefrences there is no device to choose from

---

### Post by dillandriskell on 2009-11-10
Same issues as you Dportner :/
I'll update if I find a fix or at least make progress.

I remember I had the same issues in 9.04, but managed to fix it by going to **Applications > Sound & Video > Sound Recorder** then from there I did **File > Open Volume Control**.  I fixed it somewhere in this menu and tested it in the sound recorder until I got it to work, but now it's changed and I'm lost as to how to make the computer detect it.  I faintly remember having to check off an option that corresponded to the microphone.  I'll keep looking, good luck.

---

### Post by dillandriskell on 2009-11-10
I just got my microphone to work with 9.10, I don't know how much this will help Abrahamt or teamsueroxide but this should work for Dportner.

Go to **Applications > Sound & Video > Sound Recorder **then **File > Open Volume Control** like I was talking about before.  Then open the **input** tab and **uncheck "mute"** if either input or output are muted, then change the **connector** to **microphone 2**.  The default settings were a little low for me so I had to increase the **amplify** level.  

Test to make sure it works by going back to **Sound Recorder** and clicking **Record**.  If the bar in the bottom right shows it picking up your voice then you're in good shape, click stop to hear the audio replayed.  Make changes as needed to the volume levels and you should be set.  Hope this helped!

---

### Post by teamsuperoxide on 2009-12-06
upgraded to 9.10 and tried the solution by dillandriskell but there is no other input options other than "Internal Audio Analog Stereo".
It seems the hardware is not recognised. Is there anyway find it?

---

### Post by dolphinsonar on 2010-05-14
Looking around for solutions, but none found so far.  Same issue here.

---

### Post by ger_macaco on 2010-05-14
Also having the same issue. I could never make it work.

---

### Post by dolphinsonar on 2010-05-16
Okay folks, I hope you are subscribed to this thread because I found the answer -- at least for those of us using a Dell Inspiron 1318, Lucid Lynx 64-bit.  Open a terminal and enter these commands.


[LIST]
[*]This edits your ALSA configuration:
[/LIST]
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```


[LIST]
[*]Copy and paste this at the very bottom of the ALSA configuration file you just opened:
[/LIST]
```
options snd-hda-intel model=dell-bios power_save=10 power_save_controller=N
```

[LIST]
[*]This restarts the ALSA daemon:
[/LIST]
```
 killall pulseaudio&&sudo alsa force-reload&&pulseaudio -D
```

[LIST]
[*]Just for fun, restart your computer -- but bookmark this page so you can tell us if you got it working!
[/LIST]
I hope that helps somebody other than just me!

---

### Post by dolphinsonar on 2010-05-16
Better late than never.  If you are using Intrepid Ibex or later on a 64-bit (might work for x86 also) Dell Inspiron 1318 laptop, here is the solution: 

[http://ubuntuforums.org/showthread.php?p=9307284](http://ubuntuforums.org/showthread.php?p=9307284)

Works for Lucid Lynx (mine).

---

### Post by immoweichert on 2010-05-16
Hi, I've had the same problem on my wife's Dell Dimension C521. Thanks for the post, dolphinsonar,  all works a treat now !

---

### Post by glencollins on 2010-05-17
I have tried every solution posted that I can find but cannot restore the external mic (for my headset) to functionality.  It worked FINE with Skype for a while, and suddenly the microphone no longer is detected. 
All Alsamixer settings are correct, no mic input is muted anywhere.  The Sound Recorder application says "Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System-Preferences menu."  BUT there are no combination of settings which make the Sound Recorder happy. 
What gets me is that this microphone USED TO work on Skype running this same OS Ubuntu 10.04 LTS Lucid Lynx 64-bit, but now nothing I do makes it function.  Thanks for any help you can provide.

---

### Post by lidex on 2010-05-17
> **glencollins said:**
> I have tried every solution posted that I can find but cannot restore the external mic (for my headset) to functionality.  It worked FINE with Skype for a while, and suddenly the microphone no longer is detected. 
All Alsamixer settings are correct, no mic input is muted anywhere.  The Sound Recorder application says "Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System-Preferences menu."  BUT there are no combination of settings which make the Sound Recorder happy. 
What gets me is that this microphone USED TO work on Skype running this same OS Ubuntu 10.04 LTS Lucid Lynx 64-bit, but now nothing I do makes it function.  Thanks for any help you can provide.

If skype is the only mic issue, try this fix:
Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

Reboot.

---

### Post by glencollins on 2010-05-21
Thanks, Lidex, however the mic does not work at all. (I did use your suggestions and rebooted, but no dice).
I have verified the mic itself is working, but the OS doesn't 'see' it at all.  Sound Recorder will not run (gives 'you have invalid settings' error message) yet no combination of settings makes it happy.  Functionally, the sound portion of my setup performs as if no mic was connected at all; yet it IS connected but undetected.  Still no joy...

---

### Post by lidex on 2010-05-21
> **glencollins said:**
> Thanks, Lidex, however the mic does not work at all. (I did use your suggestions and rebooted, but no dice).
I have verified the mic itself is working, but the OS doesn't 'see' it at all.  Sound Recorder will not run (gives 'you have invalid settings' error message) yet no combination of settings makes it happy.  Functionally, the sound portion of my setup performs as if no mic was connected at all; yet it IS connected but undetected.  Still no joy...

What is your info?
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by glencollins on 2010-05-22
My hardware is a Coolermaster tower with an AMD Athelon 64-bit +3200 processor and about 2GB of memory

# uname -a
Linux CommonSense 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 21 2010 for kernel 2.6.32-22-generic (SMP).

# head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

---

### Post by lidex on 2010-05-22
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

---

### Post by kltpzyxm on 2010-05-29
Thanks lidex, everything's working perfectly now. 

I think a lot of people's issues might be with the fact that ubuntu doesn't enable the microphone input by default. That's the problem I was facing, as well as a friend, and your guide just solved it for both of us.

For new users: Even when you go to sound preferences and check your input, you see all the settings working and assume that there's sound coming in. **But showing microphone input in Sound Preferences DOES NOT MEAN that it is enabled!** You still need to enable your mic-in ports through the gnome-alsamixer.

Follow lidex's instructions after that and you should be up and running. I have an Asus P5N-E SLI motherboard with Realtek ALC883 onboard audio - which is notorious for not working well with Alsa (even alsa's wiki says so). But now, everything is working smoothly!

---

### Post by glencollins on 2010-05-31
I am very happy for those who have been successful getting the mic to work.  Sadly, I am not one of those.  I have verified every possible mic setting, mute/unmute, input option, etc. with zero sound detected from the mic.
Thank you all for your assistance.  My apologies that it simply will not work for me. (BTW, I have verified that the headset works, by using it on another computer, so the mic itself is OK). :?

---

### Post by artesm8 on 2010-06-10
Hi, I recently upgraded to 10.04, and still I cannot get the microphone to work. I have a HP Pavilion dv2000

#uname -a
Linux art-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux


#aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



#cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 21 2010 for kernel 2.6.32-22-generic (SMP).

#head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20551 (Waikiki)

I would appreciate any help.

---

### Post by lidex on 2010-06-11
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Linye on 2010-06-19
Just wanted to say that dolhpinsonar post #11 worked beautifully for me on a Dell Inspiron 1318.

---

### Post by afrodeity on 2010-07-02
Friend of mine just upgraded to lucid and doesn't have an ISP, he is having trouble with getting cheese to see his microphone and it is not showing up in sound preferences. Any help appreciated

#uname -a
Linux balloonzoo-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
  
#aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

#cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 14 2010 for kernel 2.6.32-23-generic (SMP).

#head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC272

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG

---

### Post by lidex on 2010-07-05
> **afrodeity said:**
> Friend of mine just upgraded to lucid and doesn't have an ISP, he is having trouble with getting cheese to see his microphone and it is not showing up in sound preferences. Any help appreciated

#uname -a
Linux balloonzoo-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
  
#aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

#cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 14 2010 for kernel 2.6.32-23-generic (SMP).

#head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC272

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG

What is the PC make and model?

---

### Post by Pinetina on 2010-07-19
Hi!
I have an Asus Lamborghini VX1 laptop, and I have a problem with microphone, too.

When I try to register something I get only background noise, unless I try to knock directly on the microphone, in that case I can hear something but with very low volume. If I connect an external microphone, I get immediately a loud beep, I guess due to the fact that the speakers play all what the microphone registers.
The microphone works fine in Windows, so it is not damaged.

I have tried several solutions to solve my problem with my built-in microphone, but nothing has worked for me so far.
* I have tried several programs to unmute and set the volume of the microphone (alsamixer, gnome-alsamixer, sound preferences, PulseAudio Volume control, ...)
* I have created the file client.conf in ~/.pulse, adding the line "autospawn =no".
* I have updated the ALSA drivers
* I have tried to modify my etc/modprobe.d/alsa-base.conf:

```
options snd-hda-intel model=auto position_fix=1
options snd-hda-intel model=3stack position_fix=1
options snd-hda-intel model=laptop
options snd-hda-intel model=3stack
options snd-hda-intel index=-2 model=laptop
options snd-hda-intel model=laptop position_fix=1
options snd-hda-intel model=laptop power_save=10 power_save_controller=N
options snd-hda-intel model=laptop-eapd
options snd-hda-intel model=laptop-automute

```
(of course not all together).

More details about my sound setup can be found here:

[http://www.alsa-project.org/db/?f=9b070ba659d921ab742adf0cb4eeae16d4157e0f](http://www.alsa-project.org/db/?f=9b070ba659d921ab742adf0cb4eeae16d4157e0f)

Can please anybody help me? I really need it to work, skype is the only way to stay in contact with my family!

---

### Post by lidex on 2010-07-19
*Pinetina*,
Wow, I don't recall having seen that much dmesg output in alsa-info. Go ahead and remove the custom entries from alsa-base.conf and rename/move any custom alsa conf files you may have added. Now this:
```
sudo apt-get update
sudo apt-get upgrade
```
**Reboot**

Next get the output of this command:
```
dpkg -l | grep "alsa"
```
Also this:
```
aplay -l
```

---

### Post by Pinetina on 2010-07-19
Thank you very much for helping me! :D
I have generated that file through the command:

```
wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh
```indeed quite a lot of informations!

So, I have done what you have written and here is the result:

```
$ dpkg -l | grep "alsa"
ii  alsa-base                                          1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                         1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                         4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                    0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                 0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-23-generic        2.6.32-23.201007060500                          Ubuntu-supplied Linux modules for version 2.

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Since with aplay I couldn't find out with precision which model of chipset the machine mounts, I have run this:

```
$ tail /proc/asound/oss/sndstat

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Analog Devices AD1986A
```

Looking at the HD-Audio-Models.txt file ([http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD](http://git.alsa-project.org/?p=alsa-kernel.git;a=blob;f=Documentation/sound/alsa/HD-Audio-Models.txt;hb=HEAD)) my chipset correspond to:

```
243 AD1986A
244 =======
245   6stack        6-jack, separate surrounds (default)
246   3stack        3-stack, shared surrounds
247   laptop        2-channel only (FSC V2060, Samsung M50)
248   laptop-eapd   2-channel with EAPD (ASUS A6J)
249   laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
250   ultra         2-channel with EAPD (Samsung Ultra tablet PC)
251   samsung       2-channel with EAPD (Samsung R65)
252   samsung-p50   2-channel with HP-automute (Samsung P50)

```

but honestly I have no idea what eapd means, I have just found out that I should use "laptop", but it does not work.

Thanks!

---

### Post by lidex on 2010-07-19
To go with one of the generic models, you need to take into account the number of audio channels supported and the number of audio jacks. What do you have?

---

### Post by Pinetina on 2010-07-19
> **lidex said:**
> To go with one of the generic models, you need to take into account the number of audio channels supported and the number of audio jacks. What do you have?

Now it starts coming out how few I know about audio devices.. :oops:
There are 2 jacks, one for external microphone and one for headset... I hope it's enough to deduce the rest...

---

### Post by lidex on 2010-07-19
Sorry if you've done these already, but I need to know...
OK. Have you tried using sound preferences, and changing the profile on the hardware tab? Also, on the input tab making sure volume is up and unmuted?
Using pulseaudio volume control, on the input devices tab, unlocking the sliders for the mic and turning the left all the way down?

---

### Post by Pinetina on 2010-07-19
Thank you so much that you're helping me!
I have tried all the profiles and done all the tests, but it's always the same effect.
I am trying to upload a short ogg file made with the Sound Recorder, just to have an idea of what happens when I knock on the mic while recording.

---

### Post by ejbrant_ibo on 2010-08-14
I've checked many different posts. Some people share my problem with hearing line in audio through my computer speakers but it doesn't record or show up in any program. I've tried everything in every post, but most of the posts are for older versions of Ubuntu. Can someone please help me? I'm running UbuntuStudio 10.04 and I'm trying to record through the line in jack. When using alsamixer, I've found that the CD volume slider controls it. I can mute the external audio by muting the CD track. I am so frustrated with this as I have stayed up till the wee morning hours the past two nights and haven't come to any conclusion.

---

### Post by lidex on 2010-08-15
> **ejbrant_ibo said:**
> I've checked many different posts. Some people share my problem with hearing line in audio through my computer speakers but it doesn't record or show up in any program. I've tried everything in every post, but most of the posts are for older versions of Ubuntu. Can someone please help me? I'm running UbuntuStudio 10.04 and I'm trying to record through the line in jack. When using alsamixer, I've found that the CD volume slider controls it. I can mute the external audio by muting the CD track. I am so frustrated with this as I have stayed up till the wee morning hours the past two nights and haven't come to any conclusion.

Please start a new thread with pertinent system info. These issues are hardware dependent. Also go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by ejbrant_ibo on 2010-08-25
Sorry I didn't respond in a while. I was out on vacation last week. I will post a new thread and any help would be greatly appreciated. Thanks.

---

### Post by Dportner on 2010-12-11
still works in 10.10 :)

---

### Post by robn30 on 2010-12-11
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

I have a Gateway NV59 and am having the same issues, mic not showing up in the sound preferences, and therefore not working.  Is there anyway to get it working?  Thanks.

uname -a
Linux rob-NV59 2.6.35-23-generic-pae #41-Ubuntu SMP Wed Nov 24 10:35:46 UTC 2010 i686 GNU/Linux


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272X Digital [ALC272X Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC272X

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card0/codec#3 <==
Codec: Intel IbexPeak HDMI

---

### Post by lidex on 2010-12-12
@robn30
Try this - it works for the NV79.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-dig 
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

### Post by robn30 on 2010-12-12
> **lidex said:**
> @robn30
Try this - it works for the NV79.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-dig 
```Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Thanks for the reply.  I am attaching some screen shots because I dont think I am doing everything right or Ubuntu is not using the correct sound device.  Hopefully these will help to identify what I am doing wrong.

[IMG]http://ubuntuforums.org/%3Ca%20href=http://s833.photobucket.com/albums/zz255/hotrodbob1976/?action=view&current=Screenshot.jpg%20target=_blank%3E[IMG]http://i833.photobucket.com/albums/zz255/hotrodbob1976/th_Screenshot.jpg[/IMG][[IMG]http://i833.photobucket.com/albums/zz255/hotrodbob1976/th_Screenshot.jpg[/IMG]]("http://s833.photobucket.com/albums/zz255/hotrodbob1976/?action=view&current=Screenshot.jpg")

[[IMG]http://i833.photobucket.com/albums/zz255/hotrodbob1976/th_Screenshot-1.jpg[/IMG]]("http://s833.photobucket.com/albums/zz255/hotrodbob1976/?action=view&current=Screenshot-1.jpg")

[[IMG]http://i833.photobucket.com/albums/zz255/hotrodbob1976/th_Screenshot-2.jpg[/IMG]]("http://s833.photobucket.com/albums/zz255/hotrodbob1976/?action=view&current=Screenshot-2.jpg")

[[IMG]http://i833.photobucket.com/albums/zz255/hotrodbob1976/th_Screenshot-3.jpg[/IMG]]("http://s833.photobucket.com/albums/zz255/hotrodbob1976/?action=view&current=Screenshot-3.jpg")

[[IMG]http://i833.photobucket.com/albums/zz255/hotrodbob1976/th_Screenshot-4.jpg[/IMG]]("http://s833.photobucket.com/albums/zz255/hotrodbob1976/?action=view&current=Screenshot-4.jpg")
[IMG]http://ubuntuforums.org/[IMG]http://i833.photobucket.com/albums/zz255/hotrodbob1976/Screenshot-3.png[/IMG]
Thanks for your help.  Hopefully I can get this working, would be nice to have a microphone.

EDIT: Changed my sound setting to duplex and now I have a faint microphone.  Progress but I don't think it is quite right.

---

### Post by lidex on 2010-12-14
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by buzzterrier on 2011-01-29
Just a note for people who are doing a dual boot. I have a TP w510 that I dual boot into Win7 and Ubuntu. I went through all the tricks in this thread, and the mic still would not work. When I booted into Win7 I noticed that the mic was muted. When I turned it on and booted back into linux the mic worked.

---

### Post by ethan1701 on 2011-02-10
> **lidex said:**
> @robn30
Try this - it works for the NV79.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack-dig 
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

I have a Gateway NV7915u, and following this advice, I got my micropphone to work for the first time. Thanks!
However, now the headphone jack doesn't play any sound.
In Alsamixer, the Headphone option only has a Mute/Unmute option, without a volume slider over it.
In Gnome-Alsamixer there's a Headphone checkbox, but no volume bar.
In sound preferences -> output, when I select the Analog Headphones Connector, nothing changes.

Can you help with this?
Extra points if you can help me get it so plugging in the headphones will automatically mute the speakers.

Thanks!
-Ethan

---

### Post by likes2skate on 2011-03-01
I took my motherboard in, and my repair guy showed me that the mic works in Windows, but it is not working for me in kubuntu.

```
rick@Bill:/tmp/files$ dpkg -l | grep "alsa"
ii  alsa-base             1.0.22.1+dfsg-0ubuntu3  ALSA driver configuration files
ii  alsa-utils            1.0.22-0ubuntu5         ALSA utilities
ii  bluez-alsa            4.60-0ubuntu8           Bluetooth audio support
ii  libsdl1.2debian-alsa  1.2.14-4ubuntu1.1       Simple DirectMedia Layer (with X11 and ALSA 

rick@Bill:/tmp/files$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I am running kubuntu 10.04 AMD64.

I would appreciate some suggestions on getting the mic working.

Thanks,

---

### Post by lidex on 2011-03-01
Try this and if no joy then run the alsa-info script. 
Try updating your alsa-driver-modules.
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

Alsa-info script:
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by blue_bird on 2011-03-03
Hi everyone, I'm totally a newbie to ubuntu and also have problem with the microphone. I have tried everything but it's still not working. I have ASUS A42F series and this is my info.

#uname -a
Linux wardhana-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

#aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

#cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

#head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX


Please help me, I'm totally clueless. :confused:  Thanks in advance for your help.

---

### Post by lidex on 2011-03-04
> **blue_bird said:**
> Hi everyone, I'm totally a newbie to ubuntu and also have problem with the microphone. I have tried everything but it's still not working. I have ASUS A42F series and this is my info.

#uname -a
Linux wardhana-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

#aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

#cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

#head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX


Please help me, I'm totally clueless. :confused:  Thanks in advance for your help.
Follow the instructions in my post just previous to yours.

---

### Post by blue_bird on 2011-03-04
wow, you're a genius. It's working now. Thank you for your help lidex.=D>:D

---

### Post by lidex on 2011-03-06
> **blue_bird said:**
> wow, you're a genius. It's working now. Thank you for your help lidex.=D>:D

Not really, just studious. You're welcome!

---

### Post by likes2skate on 2011-03-10
lidex,

Something may not have worked right.  On the install, I got:

E: Couldn't find package linux-alsa-driver-modules-2.6.32-29-generic


> rick@Bill:sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
[sudo] password for rick: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: public key "Launchpad Ubuntu Audio Dev team PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
rick@Bill:/tmp$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-29-generic



> Your ALSA information is located at [http://www.alsa-project.org/db/?f=c4e7bb358577fcd58e2a908c5a13aaad2a714acf](http://www.alsa-project.org/db/?f=c4e7bb358577fcd58e2a908c5a13aaad2a714acf)

Please inform the person helping you.


There is a lot of info there, I hope it helps.

Thanks,

---

### Post by lidex on 2011-03-17
@likes2skate
In your case you might be better off with an alsa upgrade. Follow the upgrade link in my sig for the script *Temüjin* is maintaining.

---

### Post by likes2skate on 2011-03-22
lidex,

I upgraded, but the mic still does not work.

cat /proc/asound/version

says

Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Mar 22 2011 for kernel 2.6.32-29-generic (SMP).

I logged the compile and install but not the download.

The speakers still work fine, but I cannot hear my own voice when I do a skype test call from this PC.  I tried the ports on the motherboard's back plate and the ports on the front of the box.  With the same mic or headset, I can hear my own voice when I do a skype test call from my laptop.

My motherboard repair guy showed me that the mic works in Windows, so I do not think there is a problem with the motherboard.

I would appreciate any additional suggestions.

Thanks,

---

### Post by lidex on 2011-03-22
@likes2skate

First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

No joy? Post an updated alsa-info link.

---

### Post by likes2skate on 2011-03-23
lidex,

I installed the gnome-alsamixer (on a kubuntu box, so it needed some extras) and made sure everything was turned on, but I still cannot hear my own voice in a skype test call.

Updated alsa-info is here:

[http://www.alsa-project.org/db/?f=72609d470fe674d5af7bad6043e790cefce979d2](http://www.alsa-project.org/db/?f=72609d470fe674d5af7bad6043e790cefce979d2)

Thanks for taking a look.

---

### Post by lidex on 2011-03-23
> **likes2skate said:**
> lidex,

I installed the gnome-alsamixer (on a kubuntu box, so it needed some extras) and made sure everything was turned on, but I still cannot hear my own voice in a skype test call.

Updated alsa-info is here:

[http://www.alsa-project.org/db/?f=72609d470fe674d5af7bad6043e790cefce979d2](http://www.alsa-project.org/db/?f=72609d470fe674d5af7bad6043e790cefce979d2)

Thanks for taking a look.

Your thread title says ubuntu, so i assumed gnome. Your capture controls are off:
```
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [21.00dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 7 [50%] [10.50dB] [off]
  Front Right: Capture 7 [50%] [10.50dB] [off]
```
Try toggling them on.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by likes2skate on 2011-03-24
lidex,

It is now working.  Thank you.

I was getting error messages from gnome-alsamixer, and I could not hear my own voice doing a skype test call.  So I opened the kde mixer, and voila!  I could hear my own voice doing a skype test call.

I uploaded screen shots.

From the documentation, I did not understand that I needed to click on the "Capture" check box. "... both 'Capture Volume' and 'Capture Switch' have to be set properly ...."  What is properly?  Assuming that the "Capture" check box needs to be checked, if the documentation had said exactly that, I would have understood.

Thank you for getting this working.

---

### Post by joculi on 2011-03-25
I have a Dell Latitude E6510 laptop.  Running Ubuntu 10.04.  To the best of my ability, I've tried to follow the instructions in this thread (and quite a few others), with no luck.  

My webcam works, but my built in microphone does not.  Sometimes I can adjust the settings so I see some activity in the level indicator in Sound Recorder, but I think that is just when i have the amplification maxed out and it is just white noise.  

When I record my voice in Sound Recorder, all I hear on playback is white noise.  My main goal is to use Skype.  I have the same problem there.

here is some data that was requested of someone else in a prior post.  I hope one of you can help me make sense of it.  Thanks in advance.

```

$ uname -a
Linux lucca 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1C5

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID b


```

---

### Post by joculi on 2011-03-26
I tried upgrading ALSA as described here: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/).  The upgrade was successful, but it did not change the microphone problem.

---

### Post by joculi on 2011-03-26
I have posted the results of alsa-info and other commands at:

[https://answers.launchpad.net/ubuntu/+question/150558](https://answers.launchpad.net/ubuntu/+question/150558)

These were suggested by the directions at: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by gladbagz on 2011-03-27
Hello everyone.  I seem to be having the same problem as everyone else here.  My integrated microphone will not work and I have tried every suggestion on this thread and others I think.  My laptop is a Compaq Presario V6000.  Here is the rest of my info.

# uname -a
Linux laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Mar 26 2011 for kernel 2.6.35-28-generic (SMP).

# head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20549 (Venice)

My Alsa information is at [http://www.alsa-project.org/db/?f=5321fd21901c3216d24a6b07f14a6ed108b00b11](http://www.alsa-project.org/db/?f=5321fd21901c3216d24a6b07f14a6ed108b00b11)

Help would be appreciated.  I just want to talk to my wife and children over skype while I am gone.

---

### Post by lidex on 2011-03-31
@joculi
Please remove this from alsa-base.conf:
```
options snd-hda-intel model=dell-bios power_save=10 power_save_controller=N
```
And replace with this:
```
options snd-hda-intel model=dell-s14
```
Save file, close, and reboot.
You're using kubuntu?

---

### Post by coolglobal on 2011-05-01
Compaq Presario CQ60
Model: CQ60-302AU

No Microphone? Help with internal microphone? Please.

---

### Post by lidex on 2011-05-01
> **coolglobal said:**
> Compaq Presario CQ60
Model: CQ60-302AU

No Microphone? Help with internal microphone? Please.

Have you gone through the thread?

---

### Post by coolglobal on 2011-05-01
Happy to know you're still on this thread lidex :). This is my output. I read the thread but couldn't work out how you're joining the dots. If all fails I'll be buying a headset for this laptop for my friend. 

$ uname -a
Linux blackbird 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20561 (Hermosa)

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP77/78 HDMI

---

### Post by lidex on 2011-05-01
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

A better diagnostic tool is the alsa-info script, so if no joy:
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by coolglobal on 2011-05-01
Your ALSA information is located at

[http://www.alsa-project.org/db/?f=9c43d2cd9cde686ca2cb31911da5da80437c1487]("http://www.alsa-project.org/db/?f=9c43d2cd9cde686ca2cb31911da5da80437c1487")

---

### Post by lidex on 2011-05-01
I see you ran that command but alsa isn't picking up the ideapad model. Try reloading alsa:
```
sudo alsa force-reload
```


EDIT: Your internal mic is turned off:
```
Simple mixer control 'Internal Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 0 [0%] [-74.00dB] Playback [on]
  Front Right: 0 [0%] [-74.00dB] Playback [on]

```
Well, not turned off, but turned down.

---

### Post by coolglobal on 2011-05-01
Thanks Lidex this one is solved. Used Gnome Alsa Mixer to adjust "internal" bar. The GUI is unusual as the orange bar appears to be upside down. Must be a mixing board thing.

---

### Post by coolglobal on 2011-05-01
The internal microphone is ok now, using Sound Recorder.
Skype fails to record with internal microphone.
Tried this post:

> If skype is the only mic issue, try this fix:
Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
Code:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

No joy. With this output.

> $ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
[sudo] password for: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: public key "Launchpad Ubuntu Audio Dev team PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

$ sudo apt-get update
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty InRelease
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports InRelease                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty Release.gpg                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports Release.gpg                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports Release                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main Sources                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe Sources                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe Sources                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                              
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/main i386 Packages            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/restricted i386 Packages      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/universe i386 Packages        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/multiverse i386 Packages      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/main TranslationIndex         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/multiverse TranslationIndex   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/restricted TranslationIndex   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/universe TranslationIndex     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main Translation-en_AU                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse Translation-en_AU            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted Translation-en_AU            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main Translation-en                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe Translation-en_AU              
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main Translation-en_AU          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse Translation-en_AU    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted Translation-en_AU    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe Translation-en_AU      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe Translation-en         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/main Translation-en_AU        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/main Translation-en           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/multiverse Translation-en_AU  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/multiverse Translation-en     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/restricted Translation-en_AU  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/restricted Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/universe Translation-en_AU    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-backports/universe Translation-en       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_AU               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_AU                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_AU                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_AU           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_AU     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_AU     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_AU       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_AU                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_AU
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en
Fetched 72 B in 16s (4 B/s)
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules-2.6.38-8-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-2.6.38-8-generic'

---

### Post by lidex on 2011-05-01
Yeah, ignore that old info, Your alsa has that patch anyway. Skype can be a bear, here are some references:
[http://ubuntuforums.org/showthread.php?p=10719241#post10719241](http://ubuntuforums.org/showthread.php?p=10719241#post10719241)
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)
[https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)

---

### Post by coolglobal on 2011-05-01
Much appreciated Lidex. No joy with Pulse Audio Volume Control, recording tab, with Skype test call.

Am going to let this one go through to the keeper, and buy a two plug headset for Skype. Will be far better quality Skype calls in any case.

Laptops are such a challenge, Skype was my last hurtle on this one. Over two days have solved a brother printer/scanner, number pad, wireless broadband, sd card reader and all the multimedia compatability. Truly my preference is for old school hard wires on everything with an actual desktop workstation. I find the new unity interface to be unpleasant (and unsuitable for a touchpad mouse) so strictly classic interface for me. I genuinely hope that the classic interface continues to be maintained into the future. Am going to set this laptop to update only natty and let it ride. Hopefully not see it again until it self-implodes :-\". Thanks again for your help.

---

### Post by piratemari on 2011-05-03
So glad I saw this thread before posting a new one. :) 

After upgrading to 11.04, my mic suddenly stopped working. It was working fine before  the upgrade, and as I usually use a headset I didn't notice that it had stopped working until the day before yesterday, so there is a possibility it could be something else other than the upgrade.But I did use it before I upgraded, the very day, actually, and it was still working. I have checked the gnome-alsamixer settings and made sure they weren't on mute or anything.

Here's my alsamixer disgnostic information.
[http://www.alsa-project.org/db/?f=ab94542d9522085dedfcd389a104eb92ec5cc3d6]("http://www.alsa-project.org/db/?f=5643837da3f4b04025aaff7611292ef8f795b813")

I'd really appreciate the help, thank you!

---

### Post by lidex on 2011-05-03
> **piratemari said:**
> So glad I saw this thread before posting a new one. :) 

After upgrading to 11.04, my mic suddenly stopped working. It was working fine before  the upgrade, and as I usually use a headset I didn't notice that it had stopped working until the day before yesterday, so there is a possibility it could be something else other than the upgrade.But I did use it before I upgraded, the very day, actually, and it was still working. I have checked the gnome-alsamixer settings and made sure they weren't on mute or anything.

Here's my alsamixer disgnostic information.
[http://www.alsa-project.org/db/?f=ab94542d9522085dedfcd389a104eb92ec5cc3d6]("http://www.alsa-project.org/db/?f=5643837da3f4b04025aaff7611292ef8f795b813")

I'd really appreciate the help, thank you!

Try changing the model in alsa-base.conf from dell-m6 to dell-eq

To edit:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```

---

### Post by piratemari on 2011-05-04
Thanks a bunch for helping me with this, Lidex. 
I edited it like you said, rebooted, and nothing changed, unfortunately.

---

### Post by lidex on 2011-05-04
What is your amixer output now:
```
amixer
```

---

### Post by piratemari on 2011-05-04
Here you go. 
```
mari@lappeh3k:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',1
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Line In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 1 [33%] [-12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]

```

---

### Post by lidex on 2011-05-04
When dealing with alsa, the digit 0 signifies the first, or default, device. I'm assuming this is an internal mic? 

From ubuntu wiki:
> Changing default subdevice configuration

Some sound devices have multiple capture subdevices (eg. hda-intel), 
but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. 
ALSA may not be configured to use your preferred device as subdevice #0 by default.

Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), 
so we are watching for movements that correspond to our voice. 

Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), 
and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case) 
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, 
even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized 
until it was repeated. This also works if you use the "Options" tab in the standard mixer app to do the same thing.

```
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Line In'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
```

---

### Post by piratemari on 2011-05-04
Okay, followed the directions, here are my results. I am not at all positive I got everything, so if I missed something,please let me know. The images are not all a uniform size, and some of them are big-ish so I'm just linking them from my photobucket.

Also,yes, that's my internal mic. 

So, firs step,I actually had to install the PulseAudio meter. then when it was done I ran it, this was what it looked like: 
[http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot.png](http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot.png)

Then I opened Alsamixer to test some settings.  My voice did not make any difference whatsoever, but  changing the amplification had a huge difference:
[http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-1.png](http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-1.png)
[http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-2.png](http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-2.png)
[http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-3.png](http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-3.png)

Then I ran alsamixer -c 0, went to F4,this was what it looked like:
[http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-5.png](http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-5.png)

After that I went back to the sound properties alsamixer again and tried changing the amplification to see if it had a similar effect, it was  already at 100% amplified:
[http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-6.png](http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-6.png)
[http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-7.png](http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-7.png)
[http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-8.png](http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-8.png)

I'm not sure what to do now, but I found it very off that when un-amplified my mic volume and capture mutes - previously my mic almost never had to be amplified because my mic is really sensitive.

---

### Post by lidex on 2011-05-04
OK. The one thing we're missing here is the 'Mic Jack Mode'. See if you can enable that with gnome-alsamixer and then change the value to 'Mic In'.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by piratemari on 2011-05-04
Luckily I already had that installed. 
I got an error message when I enabled it, AND when I first opened it: ```
** (gnome-alsamixer:6390): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "Mic Jack Mode"!
```[http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-9.png](http://i767.photobucket.com/albums/xx320/piratemari/Ubuntu/Screenshot-9.png)

Also, the first Capture is down because mic is un-amplified.when I turn it back up the mic goes back to 100% amplification.

---

### Post by lidex on 2011-05-04
I'm leaning toward another model in alsa-base.conf - the options:
```
STAC92HD73*
===========
  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  intel		Intel DG45* mobos
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  alienware	Alienware M17x
  auto		BIOS setup (default)

```
It may actually be intel as you seem to have the ibexpeak chipset.

---

### Post by piratemari on 2011-05-05
Well I tried intel, my mic started working but my speakers stopped. So then I tried dell-m6-amic, which made the speakers work again but no mic, and then dell-m6-dmic which FIXED IT! :D

Thank you so, so, **so** very much for your help, Lidex! Especially for that list with the options. <3

---

### Post by lidex on 2011-05-05
> **piratemari said:**
> Well I tried intel, my mic started working but my speakers stopped. So then I tried dell-m6-amic, which made the speakers work again but no mic, and then dell-m6-dmic which FIXED IT! :D

Thank you so, so, **so** very much for your help, Lidex! Especially for that list with the options. <3

Nice. You're welcome. Please mark the thread solved using 'Thread Tools' up top.

---

### Post by piratemari on 2011-05-05
>> I actually don't have that option, probably since I didn't create the thread. :/

---

### Post by lidex on 2011-05-05
> **piratemari said:**
> >> I actually don't have that option, probably since I didn't create the thread. :/

Yeah, what was I thinking? This thread will never be solved. Who is the actual OP? I know I'm not going back to the first post;)

---

### Post by Zeak on 2011-05-29
> **dillandriskell said:**
> I just got my microphone to work with 9.10, I don't know how much this will help Abrahamt or teamsueroxide but this should work for Dportner.

Go to **Applications > Sound & Video > Sound Recorder **then **File > Open Volume Control** like I was talking about before.  Then open the **input** tab and **uncheck "mute"** if either input or output are muted, then change the **connector** to **microphone 2**.  The default settings were a little low for me so I had to increase the **amplify** level.  

Test to make sure it works by going back to **Sound Recorder** and clicking **Record**.  If the bar in the bottom right shows it picking up your voice then you're in good shape, click stop to hear the audio replayed.  Make changes as needed to the volume levels and you should be set.  Hope this helped!
Thank You dillandriskell your fix put my microphone to work on my Dell E510 Desktop running Linux Mint 11 Kayta.  My Skype is working again.  Zeak

---

### Post by dr.twinny on 2011-06-12
Could anyone help with getting my mic to work? I'm running ubuntu 11.04 on a HP dv6. I've tried searching online for reliable fixes, but nothing I tried ever worked. Help plz!:(

---

### Post by lidex on 2011-06-12
> **dr.twinny said:**
> Could anyone help with getting my mic to work? I'm running ubuntu 11.04 on a HP dv6. I've tried searching online for reliable fixes, but nothing I tried ever worked. Help plz!:(
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-dv5 enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by dr.twinny on 2011-06-13
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-dv5 enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Thanks alot Lidex!!!:D It's working now, but the only issue I have now is the clarity of it. I'm fiddling with the sliders in pulse audio control, but so far not good enough quality.

---

### Post by lidex on 2011-06-13
> **dr.twinny said:**
> Thanks alot Lidex!!!:D It's working now, but the only issue I have now is the clarity of it. I'm fiddling with the sliders in pulse audio control, but so far not good enough quality.
Post your amixer output:
```
amixer
```

---

### Post by dr.twinny on 2011-06-14
My amixer results

> Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 38 [59%] [-19.50dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Bass Speaker',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2'
  Item0: 'Digital Playback'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 6 [40%] [9.00dB] [off]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 3 [100%] [30.00dB]
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

---

### Post by lidex on 2011-06-15
These values may need tweaking:
```
Simple mixer control [COLOR="DarkRed"]'Capture',0[/COLOR]
Capabilities: cvolume cswitch penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 15
Front Left: Capture 0 [0%] [0.00dB] [off]
Front Right: Capture 6 [40%] [9.00dB] [off]

Simple mixer control [COLOR="DarkRed"]'Internal Mic',0[/COLOR]
Capabilities: cvolume penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 3
Front Left: Capture 0 [0%] [0.00dB]
Front Right: Capture 3 [100%] [30.00dB]

Simple mixer control [COLOR="DarkRed"]'Mux',0[/COLOR]
Capabilities: cvolume penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 3
Front Left: Capture 0 [0%] [0.00dB]
Front Right: Capture 0 [0%] [0.00dB] 
```

---

### Post by chopurtito on 2011-06-17
Hello, I have the same problem. I tried everything but steel without a solution. This is my alsa information:

[http://www.alsa-project.org/db/?f=b9e33b280b75de4a1bda43363ebe8237a22b1d81](http://www.alsa-project.org/db/?f=b9e33b280b75de4a1bda43363ebe8237a22b1d81) 

Please help me!!!!.

---

### Post by lidex on 2011-06-18
> **chopurtito said:**
> Hello, I have the same problem. I tried everything but steel without a solution. This is my alsa information:

[http://www.alsa-project.org/db/?f=b9e33b280b75de4a1bda43363ebe8237a22b1d81](http://www.alsa-project.org/db/?f=b9e33b280b75de4a1bda43363ebe8237a22b1d81) 

Please help me!!!!.

Please edit alsa-base.conf and remove the line you added:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Remove this line:
```
options snd-hda-intel model=hp-g60 enable_msi=1
```
Replace with this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
Save. Close. Reboot.

---

### Post by chopurtito on 2011-06-18
> **lidex said:**
> Please edit alsa-base.conf and remove the line you added:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Remove this line:
```
options snd-hda-intel model=hp-g60 enable_msi=1
```
Replace with this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
Save. Close. Reboot.

Than you, but it didn't work.

---

### Post by lidex on 2011-06-18
> **chopurtito said:**
> Than you, but it didn't work.
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

From ubuntu wiki:
> Changing default subdevice configuration

Some sound devices have multiple capture subdevices (eg. hda-intel), 
but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. 
ALSA may not be configured to use your preferred device as subdevice #0 by default.

Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), 
so we are watching for movements that correspond to our voice. 

Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), 
and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case) 
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, 
even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized 
until it was repeated. This also works if you use the "Options" tab in the standard mixer app to do the same thing.

---

### Post by chopurtito on 2011-06-18
In the input tab of Sound Preferences, there aren't a device to select.

---

### Post by dr.twinny on 2011-06-18
> **lidex said:**
> These values may need tweaking:
```
Simple mixer control [COLOR="DarkRed"]'Capture',0[/COLOR]
Capabilities: cvolume cswitch penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 15
Front Left: Capture 0 [0%] [0.00dB] [off]
Front Right: Capture 6 [40%] [9.00dB] [off]

Simple mixer control [COLOR="DarkRed"]'Internal Mic',0[/COLOR]
Capabilities: cvolume penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 3
Front Left: Capture 0 [0%] [0.00dB]
Front Right: Capture 3 [100%] [30.00dB]

Simple mixer control [COLOR="DarkRed"]'Mux',0[/COLOR]
Capabilities: cvolume penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 3
Front Left: Capture 0 [0%] [0.00dB]
Front Right: Capture 0 [0%] [0.00dB] 
```

Did some tweaking on all three and now I can hear myself rather clearly. Thanks again.

---

### Post by dr.twinny on 2011-06-18
Okay, so the mic works ok whenever I'm using sound recorder. But strangely, whenever I try to use it in skype or any other call service, eg. Google Voice, the mic settings always seem to automatically go to the lowest level during calls. I've tried to fix it in alsamixer but I can clearly see the sliders go all the way down by themselves! :o:confused:

---

### Post by lidex on 2011-06-18
> **dr.twinny said:**
> Okay, so the mic works ok whenever I'm using sound recorder. But strangely, whenever I try to use it in skype or any other call service, eg. Google Voice, the mic settings always seem to automatically go to the lowest level during calls. I've tried to fix it in alsamixer but I can clearly see the sliders go all the way down by themselves! :o:confused:

In skype you'll need to disable option allowing it to control audio levels.

---

### Post by dr.twinny on 2011-06-21
> **lidex said:**
> In skype you'll need to disable option allowing it to control audio levels.

Oh yeah. Forgot about that option.

---

### Post by chopurtito on 2011-06-22
I solve my problem, it was so stupid...

So, in the tab Hardware of Sound Preferences you have to select the right profile, in my case was Analog Stereo Duplex or Digital Stereo (IEC958) Output + Analog Stereo Input, by mistake i had it in Analog Stereo Output only.Anyway, dont make the same mistake that me please, hahaha. Thanks a lot for all your responses.

---

### Post by mad_max0204 on 2011-08-02
With new version I get my mic working but its crappy and bad quality.
With previous kernel and previous patch it was working nice.

---

### Post by eric3938 on 2011-08-03
Just because I've been working on this for quite a while tonight......

Using Ubuntu 10.04 (Lucid) on a HP Pavillion DV7-3165DX, I could not get my microphone to work, searching this thread and everywhere else. My output of "aplay -l" was
```

eric@Eric-UE:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

So, I was looking for a solution for an ATI device. However, through some searching I found this [http://www.ubuntu.com/certification/catalog/component/pci:4383:1002-AUDIO](http://www.ubuntu.com/certification/catalog/component/pci:4383:1002-AUDIO) indicating that it was in fact an Intel chipset. So I decided to try lidex's previous suggestion to someone else.

> **lidex said:**
> Please edit alsa-base.conf ............

```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```Save. Close. Reboot.

Now my microphone works, and with some tweaking I should be able to improve the sound quality.
I want to thank everyone who participated in this thread and especially lidex for all of the suggestions they provided throughout the thread. Between all of you, and some dumb luck on my part, MY MIC WORKS! =D>=D>=D>=D>

---

### Post by lidex on 2011-08-16
> **eric3938 said:**
> Just because I've been working on this for quite a while tonight......

Using Ubuntu 10.04 (Lucid) on a HP Pavillion DV7-3165DX,<snip> 
[/CODE]

So, I was looking for a solution for an ATI device. However, through some searching I found this [http://www.ubuntu.com/certification/catalog/component/pci:4383:1002-AUDIO](http://www.ubuntu.com/certification/catalog/component/pci:4383:1002-AUDIO) indicating that it was in fact an Intel chipset. So I decided to try lidex's previous suggestion to someone else.


Now my microphone works, and with some tweaking I should be able to improve the sound quality.
I want to thank everyone who participated in this thread and especially lidex for all of the suggestions they provided throughout the thread. Between all of you, and some dumb luck on my part, MY MIC WORKS! =D>=D>=D>=D>

I too have a dv7 and the standard tweak for it that I was aware of is:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

The msi option seems to be important for mic functionality.

Having said that, after upgrading to maverick I find this in alsa-base.conf:
```
options snd-hda-intel enable=1 enable_msi=1 single_cmd=0 power_save_controller=0 power_save=0
```
Now, I'm not sure how that got there, but it seems to work albeit with a later version of alsa.

---

### Post by RoshJay on 2011-08-22
Thank you Dillandriskell! It works :D

---

### Post by helobubba on 2011-09-13
Hello - I am a relative newb having trouble getting my Plantronics Voyager 510 USB bluetooth mic to work in Google Talk.  I have also tried a wired mic via the mic jack with no joy.  I am running Xubuntu 11.04 on an HP ENVY 14...I also replaced the taskbar mixer with gnome alsamixer plugin.  Tried many of the solutions on this great post, but nothing seems to work for me.  Would appreciate any help from anyone - thanks!

Linux xxxxxx-HP-ENVY-14-Notebook-PC 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Advanced Linux Sound Architecture Driver Version 1.0.23.


==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1X5

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

# info from tail of alsa-base.conf
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

#alsa config info link:
[http://www.alsa-project.org/db/?f=f94266be65f890103c2672d29f0d83b522179bd8](http://www.alsa-project.org/db/?f=f94266be65f890103c2672d29f0d83b522179bd8)

---

### Post by lidex on 2011-09-14
> **helobubba said:**
> Hello - I am a relative newb having trouble getting my Plantronics Voyager 510 USB bluetooth mic to work in Google Talk.  I have also tried a wired mic via the mic jack with no joy.  I am running Xubuntu 11.04 on an HP ENVY 14...I also replaced the taskbar mixer with gnome alsamixer plugin.  Tried many of the solutions on this great post, but nothing seems to work for me.  Would appreciate any help from anyone - thanks!

Linux xxxxxx-HP-ENVY-14-Notebook-PC 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Advanced Linux Sound Architecture Driver Version 1.0.23.


==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1X5

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

# info from tail of alsa-base.conf
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

#alsa config info link:
[http://www.alsa-project.org/db/?f=f94266be65f890103c2672d29f0d83b522179bd8](http://www.alsa-project.org/db/?f=f94266be65f890103c2672d29f0d83b522179bd8)
Plug in your mic and run this command and see if anything happens:
```
sudo modprobe snd-usb-audio
```
The only sound modules loading are hda-intel

---

### Post by helobubba on 2011-09-14
> **lidex said:**
> Plug in your mic and run this command and see if anything happens:
```
sudo modprobe snd-usb-audio
```The only sound modules loading are hda-intel

Lidex: many thanks for your help.  I ran the above at the Command line, but still no sound in google talk..  Two bits of info I forgot to add: internal mic works fine in google talk, as does the Plantronic headset audio.  Just can't get the mic to work, or any other plug-in mic either.  I assumed the hda-intel device was the onboard sound, and the hdmi device was for the hdmi out.  ...Is there something else that should be loading?

---

### Post by lidex on 2011-09-18
> **helobubba said:**
> Lidex: many thanks for your help.  I ran the above at the Command line, but still no sound in google talk..  Two bits of info I forgot to add: internal mic works fine in google talk, as does the Plantronic headset audio.  Just can't get the mic to work, or any other plug-in mic either.  I assumed the hda-intel device was the onboard sound, and the hdmi device was for the hdmi out.  ...Is there something else that should be loading?

Post your amixer output:
```
amixer
```

---

### Post by Kartik Raj Kanna on 2011-09-23
same problem. though running it on ubuntu 11.04 on desktop. Sound works fine. in the sound control thingy the bar which senses input amount works fine but sound recorder and RecordMyDesktop doesn't work
Please help

---

### Post by lidex on 2011-09-23
> **Kartik Raj Kanna said:**
> same problem. though running it on ubuntu 11.04 on desktop. Sound works fine. in the sound control thingy the bar which senses input amount works fine but sound recorder and RecordMyDesktop doesn't work
Please help

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by ubun2geek on 2011-10-06
THanks sooo much!

---

### Post by helobubba on 2011-10-11
> **lidex said:**
> Post your amixer output:
```
amixer
```

Lidex: thanks for your patience.  I work overseas and connectivity is poor.  Here is my amixer output, with the bluetooth headset plugged in.

In Gnome Alsamixer, on the ' IDT 92HD81B1X5' tab I have 'Internal' turned all the way down, 'Capture' and 'Mic' turned all the way up, and the 'Rec' box checked.  I have tried the USB bluetooth mic with in google talk with both the 'Mic Jack Mode' box checked (Question for you: what is this exactly?) and unchecked (no joy for either).

In Gnome Alsamixer, I have the 'ATIR6xx HDMI' tab, I have the 'IEC958' box checked.  I am not sure what this box is, but I have it checked.  And another stupid question: this tab is for my HDMI out, correct, so it should have no bearing on any other sound?

In Gnome Alsamixer, I have a third tab titled 'USB Mixer' that appears when my bluetooth headset is plugged in.  I have both the 'PCM' and the 'Mic' on this tab turned all the way up.  Can't seem to find these in my amixer output.  Thanks again for your help!!

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 53 [83%] [-8.25dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 63 [98%] [0.75dB] [on]
  Front Right: Playback 63 [98%] [0.75dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.00dB]
  Front Right: Capture 3 [100%] [30.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Line In'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]

---

### Post by ScThSh on 2011-10-20
Hello everyone, I need some help. I am relatively new to Ubuntu, and I am having issues with my internal mic on my Gateway ZX4300. I'm running 11.04 (natty)  I can't get the mic to work at all. There are no input devices listed in my sound panel.

---

### Post by stephenbbb on 2011-10-23
to lidex:

I have alsa and everything and system settings show no input device. I added this to my conf and still nothing.

scb@scb-Aspire-5250:~$ tail /etc/modprobe.d/alsa-base.conf
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel position_fix=1

the ridiculous thing is it used to work fine with skype and all, and now it stopped. not sure if it is after the upgrade or it worked after the upgrade for a week

scb@scb-Aspire-5250:~$ uname -a
Linux scb-Aspire-5250 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux
scb@scb-Aspire-5250:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.

---

### Post by helobubba on 2011-11-02
> **helobubba said:**
> Lidex: thanks for your patience.  I work overseas and connectivity is poor.  Here is my amixer output, with the bluetooth headset plugged in.

In Gnome Alsamixer, on the ' IDT 92HD81B1X5' tab I have 'Internal' turned all the way down, 'Capture' and 'Mic' turned all the way up, and the 'Rec' box checked.  I have tried the USB bluetooth mic with in google talk with both the 'Mic Jack Mode' box checked (Question for you: what is this exactly?) and unchecked (no joy for either).

In Gnome Alsamixer, I have the 'ATIR6xx HDMI' tab, I have the 'IEC958' box checked.  I am not sure what this box is, but I have it checked.  And another stupid question: this tab is for my HDMI out, correct, so it should have no bearing on any other sound?

In Gnome Alsamixer, I have a third tab titled 'USB Mixer' that appears when my bluetooth headset is plugged in.  I have both the 'PCM' and the 'Mic' on this tab turned all the way up.  Can't seem to find these in my amixer output.  Thanks again for your help!!

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 53 [83%] [-8.25dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 63 [98%] [0.75dB] [on]
  Front Right: Playback 63 [98%] [0.75dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.00dB]
  Front Right: Capture 3 [100%] [30.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Line In'
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Lidex: I made a recent discovery which may be of some importance.  Apparently, the HP Envy 14 does NOT have a mic jack; it has a Smartphone Jack, and to use this jack with a regular mic an adapter plug is required.  Have not tried the hardware adapter yet.  But would this fact affect the hardware...is what is listed as "mic" in alsamixer really a smartphone device of some sort?  Maybe you could shed some light on this new info.  Thanks again for your help.

- Bubba

---

### Post by tmow on 2011-11-27
Hello,

First of all thanks so much for your professionalism!!!

I've the same issue as everybody, I've tried all the above /trying to understand)But I cannot fix it.

I've posted my config here:

[http://www.alsa-project.org/db/?f=4a3eea3e0051ad5ea52448ce8004de384bba9029](http://www.alsa-project.org/db/?f=4a3eea3e0051ad5ea52448ce8004de384bba9029)

I cannot download your scripts as I don't the right priviledges.

I cannot use the ppa dev

```
W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
```

Any ideas please?

Thanks in advance!!!

---

### Post by tmow on 2011-11-27
> **tmow said:**
> Hello,

First of all thanks so much for your professionalism!!!

I've the same issue as everybody, I've tried all the above /trying to understand)But I cannot fix it.

I've posted my config here:

[http://www.alsa-project.org/db/?f=4a3eea3e0051ad5ea52448ce8004de384bba9029](http://www.alsa-project.org/db/?f=4a3eea3e0051ad5ea52448ce8004de384bba9029)

I cannot download your scripts as I don't the right priviledges.

I cannot use the ppa dev

```
W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
```

Any ideas please?

Thanks in advance!!!
I can doenload the scripts now... Doing and I'll be back

---

### Post by tmow on 2011-11-27
> **tmow said:**
> I can doenload the scripts now... Doing and I'll be back
I finally found the setting that was causing me headaches..

[[IMG]http://i.imgur.com/gf8iv.png[/IMG]](http://imgur.com/gf8iv)

---

### Post by lidex on 2011-12-31
> **ScThSh said:**
> Hello everyone, I need some help. I am relatively new to Ubuntu, and I am having issues with my internal mic on my Gateway ZX4300. I'm running 11.04 (natty)  I can't get the mic to work at all. There are no input devices listed in my sound panel.

Sorry, had to step aside for a while.
Can you open a terminal? If so use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by /dev/random/username on 2012-01-03
I saw this thread and decided to post my problem here, instead of making a new one.

I have the same problem as those guys.. microphone just wont work. I've tried editing alsa-base.conf with different settings, installed pavucontrol and made mic run at 1 channel, also tried removing pulseaudio and installing esound.. and again mic wouldn't work.

This is a fresh install of Ubuntu 11.10 since my last one got so messed up while trying to figure it out.
Here is a link to my alsa config: [http://www.alsa-project.org/db/?f=5668913791f2fed8d6efada94c4b56902d9d7f61](http://www.alsa-project.org/db/?f=5668913791f2fed8d6efada94c4b56902d9d7f61)

Thanks in advance.

---

### Post by librechick on 2012-01-03
I know that your want to get you mic working and I don't have a solution. At least not a software one. This is clearly an ongoing problem. You might just want to try going the easy route and get a new microphone. I've had good experience with USB microphones from [http://www.thinkpenguin.com/ ]("http://www.thinkpenguin.com/")

Those mics are audio standards compliant so they should work with just about anything.

---

### Post by lidex on 2012-01-03
> **/dev/random/username said:**
> I saw this thread and decided to post my problem here, instead of making a new one.

I have the same problem as those guys.. microphone just wont work. I've tried editing alsa-base.conf with different settings, installed pavucontrol and made mic run at 1 channel, also tried removing pulseaudio and installing esound.. and again mic wouldn't work.

This is a fresh install of Ubuntu 11.10 since my last one got so messed up while trying to figure it out.
Here is a link to my alsa config: [http://www.alsa-project.org/db/?f=5668913791f2fed8d6efada94c4b56902d9d7f61](http://www.alsa-project.org/db/?f=5668913791f2fed8d6efada94c4b56902d9d7f61)

Thanks in advance.
What is your MB info:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by /dev/random/username on 2012-01-03
Bios
```
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1904   
    Release Date: 09/07/2010
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 2048 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 8.15

Handle 0x003E, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 6
        zh|TW|BIG5
        zh|CN|GB2312-80
        ja|JP|unicode-1
        fr|FR|iso8859-1
        de|DE|iso8859-1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

```Motherboard
```
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: Crosshair III Formula
    Version: Rev 1.xx
    Serial Number: 101927950000394
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x003C, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:   To Be Filled By O.E.M.

```

---

### Post by lidex on 2012-01-04
> **/dev/random/username said:**
> Bios
```
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: Crosshair III Formula
    Version: Rev 1.xx
    Serial Number: 101927950000394
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x003C, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:   To Be Filled By O.E.M.

```

Bios is auto probing your codec so should probably provide a model. ```
echo "options snd-hda-intel model=6stack-dig" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Next provide the amixer output please:
```
amixer
```

---

### Post by /dev/random/username on 2012-01-04
amixer
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 35 [90%] [-6.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB]
  Front Right: Playback 254 [100%] [0.20dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 39
  Mono: Capture [off]
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Mono',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 53 [98%] [21.00dB] [on]
  Front Right: Capture 0 [0%] [-58.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 39 [72%] [0.00dB] [off]
  Front Right: Capture 39 [72%] [0.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 39 [72%] [0.00dB] [off]
  Front Right: Capture 39 [72%] [0.00dB] [off]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'HDMI',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB]
  Front Right: Playback 39 [100%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Line' 'Mic' 'CD' 'Mix'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Line' 'Mic' 'CD' 'Mix'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Front Mic' 'Line' 'Mic' 'CD' 'Mix'
  Item0: 'Front Mic'

```

---

### Post by lidex on 2012-01-04
> **/dev/random/username said:**
> amixer


Where are you plugged in, or is it internal mic? Mixer is showing 'front mic' and just 'mic'.

---

### Post by /dev/random/username on 2012-01-04
> **lidex said:**
> Where are you plugged in, or is it internal mic? Mixer is showing 'front mic' and just 'mic'.

Its a separate microphone, and yes I've checked to see if its been plugged in the wrong jack, microphone is working perfectly on windows so its not a hardware malfunction.

I don't have webcam, idk why it shows 2 microphones

EDIT: Just connected the microphone to my laptop which is running centos 6.2 and worked fine.

---

### Post by lidex on 2012-01-04
> **/dev/random/username said:**
> Its a separate microphone, and yes I've checked to see if its been plugged in the wrong jack, microphone is working perfectly on windows so its not a hardware malfunction.

I don't have webcam, idk why it shows 2 microphones

EDIT: Just connected the microphone to my laptop which is running centos 6.2 and worked fine.

No, I'm referring to your mixer elements. Is this a laptop with internal mic? Or PC with multiple mic ports? What port is it plugged into? Front panel, back panel?

---

### Post by /dev/random/username on 2012-01-04
> **lidex said:**
> No, I'm referring to your mixer elements. Is this a laptop with internal mic? Or PC with multiple mic ports? What port is it plugged into? Front panel, back panel?

Mic is plugged in the back panel of the Desktop case.
And about the laptop I was merely stating that the microphone works with another OS.

EDIT: now that i think.. I have my front Audio IN/OUT panel connected to the sound card, maybe that's why amixer shows 2 microphones?

---

### Post by /dev/random/username on 2012-01-04
Microphone is working now... I've removed the cable that was connecting my front panel to the sound card, booted the OS.. ran skype test call and everything is fine now. Thanks again for the help.

---

### Post by lidex on 2012-01-04
> **/dev/random/username said:**
> Microphone is working now... I've removed the cable that was connecting my front panel to the sound card, booted the OS.. ran skype test call and everything is fine now. Thanks again for the help.

Sweet. Have fun.

---

### Post by silverfilling on 2012-01-14
Hi all, I have a laptop HP Pavilion dv1000. Ubuntu version 11.04, brand new webcam kinobo 5 and the microphone doesn't want to work. I followed the suggestion made on page 3 for a pavilion dv2000, but I still have the same problem. in Alsamixer the mic level is at its maximum but the mic does not work in skype, sound recording, pulseaudio. Thanks in advance

---

### Post by niekas on 2012-01-15
Could someone help with my microphone problem in ubuntu. I have dell inspiron 6000. Microphone works fine when booted in windows on the same machine. Tried a lot of suggestions screwed settings. Reseted sound settings to defaults again. I'm lost.

Microphone is regular not USB.

---

### Post by Sascaroth on 2012-02-17
..

---

### Post by slotto on 2012-05-05
Thanks anyway. I've been battling with my internal mic since 10.04. But after installing 12.04 all of my problems are solved!

---

### Post by helobubba on 2012-07-05
> **helobubba said:**
> Lidex: I made a recent discovery which may be of some importance.  Apparently, the HP Envy 14 does NOT have a mic jack; it has a Smartphone Jack, and to use this jack with a regular mic an adapter plug is required.  Have not tried the hardware adapter yet.  But would this fact affect the hardware...is what is listed as "mic" in alsamixer really a smartphone device of some sort?  Maybe you could shed some light on this new info.  Thanks again for your help.

- Bubba

Problem: SOLVED.  Addition of Pulseaudio Mixer App fixed the random defaulting behavior of my mic in Pulseaudio.  I was not paying attention to the Pulseaudio sound server and focusing on alsa instead...perhaps this fix is peculiar to Xubuntu, perhaps not.  Hopefully someone else may read this and learn from my simple, yet painful, mistake.  Thanks to Lidex and others for their help.

---

### Post by ShparkyEg on 2013-01-31
Hi all, It looks like i am not available to fix my microphone just using google, so i will really appreciate your help.
Script link :
[http://www.alsa-project.org/db/?f=8d716ff043c227bf0315abb480e408bda8832d4a](http://www.alsa-project.org/db/?f=8d716ff043c227bf0315abb480e408bda8832d4a)

Thanks.

Hmm, solved, by switching channels in alsamixer from 6 to 2/4. It looks loke it was set 5.1 :)

---

