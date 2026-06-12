---
title: "How do you get HDMI audio out in ubuntu 13.04?"
date: 2013-05-22
forum: Hardware
---

### Post by swagz101 on 2013-05-22
I plugged in and hdmi cable into my laptop so i can use ubuntu on my tv. everything works perfectly, except the sound. It only plays from my laptop. How do i get the sound working? BTW I dont think its a hardware problem because the sound works in my windows partition when its connected from there. 


I dont know what info i need to give you guys, Ill just give my pc specs, and if anything i will be more than willing to tell you anything you ask.

lenovo u310 

Intel® Core™ i5-3317U CPU @ 1.70GHz × 4 
Intel® Ivybridge Mobile 
64-bit ubuntu 13.04

---

### Post by fj401971 on 2013-05-23
I don't know if this applies to your computer or not, but when I had audio issues with HDMI, I fixed it by going into alsamixer and unmuting "S/PDIF".  

So, go in a terminal, startup alsamixer by typing "alsamixer" and then enter.  Scroll over to "S/PDIF" using the arrow keys to see if this category or any other category that could be related to hdmi audio is muted.  

And obviously, in your sound settings you have to make sure that HDMI audio is selected and that the volume is turned up.  

Just something quick to check, I haven't used 13.04.

---

### Post by swagz101 on 2013-05-23
when I typed in alsamixer and the menu comes up, the s/pdif controller is off. And there is like no way to turn it on.

---

### Post by fj401971 on 2013-05-23
Use the 'm' key to mute/unmute the selection....  It'll show "MM" above "S/PDIF" if it is muted and "00" if it is unmuted.

Sorry...I forgot about that part.  It's been awhile since I messed with this.

---

### Post by swagz101 on 2013-05-23
thanks for your helo fj401971!! You were right, it was an issue of dealing s/pdif controller. to find the found the solution all i had to do was:
 
[B]1.)install pulse audio control, 
       [/B]sudo apt-get install pavucontrol

**2.) install the alsa mixer  daily builds.found here:** [https://code.launchpad.net/~ubuntu-a...aily/+packages]("https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages")
 
**3.) Once i did that, i opened pulse audio, went to configuration tab, and in the profile drop down menu there was an option for hdmi audio out. select it and kaboom, it works!**
 
when i checked the terminal again, the S/pdif controller was working. Previously it was disabled.

once you do that, the hdmi controls will appear in the sound volume menu, and you can adjust the volume levels from there.



Thanks for your help, its greatly appreciated!

---

### Post by nortexoid on 2013-06-06
Probably if you're using the latest mainline kernel you don't need to install the daily alsa packages. In any case, this worked for me too. I'm using KDE and on my AMD system I don't need to use pavucontrol to switch audio streams to the HDMI out--I can do it from kmix. But with this Intel system (Ivybridge), there is simply no way to switch audio streams through kmix. Moreover, one can't simultaneously output from analog audio and hdmi on Intel, though I can do this no problem on AMD. Interesting.

---

### Post by Yellow Pasque on 2013-06-07
I think the Ivy Bridge chips use the mobo's sound codec, rather than having a separate one.

---

### Post by MrBackhand on 2013-06-07
I am using Mythbuntu 12.04 with xfce as my HTPC setup and all of my sounds come out of my HDMI cable except for mame game sounds.  Does anyone have any suggestions on how to configure mame so it comes out of the HDMI connection?  [COLOR=#000000]MythTV see's it as ALSA:hdmi:CARD=NVidia,DEV=1. Audacity lists it as HDA NVidia: HDMI 0 (hw:1,3).  Any help is appreciated![/COLOR]

---

### Post by Yellow Pasque on 2013-06-07
^Are you using pulseaudio or not?

mame is an SDL app, so you might want to try:
```
export SDL_AUDIODRIVER=alsa
export AUDIODEV=hw:1,3
```

---

### Post by MrBackhand on 2013-06-07
I installed pulseaudio to try to solve the problem but I think it made things worse.  Your suggestion above works!  I owe you a beer!

---

### Post by Yellow Pasque on 2013-06-07
You should tack those export commands to the end of your ~/.bashrc file so they automatically run every time.

> I owe you a beer! 
I prefer shrooms. :popcorn:

---

### Post by emperorofnight on 2013-12-02
Hello, I'm using Ubuntu 13.04 and the HDMI output doesn't show on the sound config, but it does show on pulseaudio and in alsa mixer it is unmuted. When playing a video file, selecting HDMI out on pulseaudio makes the vu bar come to life as it playing sound but I can't hear a thing. Any idea?

---

### Post by Yellow Pasque on 2013-12-02
If it's AMD HDMI, see workaround 1 here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

---

### Post by Desmo75TS on 2013-12-28
Hi guys,
I installed xubuntu 12.04, and HDMI audio works great (I have a motherboard with integrated HDMI output, and the pc is connected to a TV via HDMI).
I next tried to install in dualboot Kubuntu 13.10, and also tried a live gnome 13.10: there's no way to run audio neither in Kubuntu nor in Gnome.
It 's all right, the sound is active, the card is recognized, and the system thinks that the sounds are produced properly test ... bu i can't hear any sound.
No tecnincal sound, no music sound, absolutely silent.
I wonder how it is possible to downgrade a similar performance: XFCE 12.04, which should be a distro "essential" works well.
I have no way to attach the results but alsamixer shows SPDIF '00', and teste for cards and aplay went right.
Pulseaudio is ok, and its configuration is identical to the 12.04 one.

Suggestions?
Thank you all in advance and good holidays.
Dario

---

### Post by Desmo75TS on 2013-12-31
Guys,

after discovering that my motherboard integrates a Radeon, i solved replacing into /etc/default/grub the following line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
with
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"
next 
sudo update-grub2
reboot

Enjoy!

Bye
Dario

---

### Post by Sava_Nguyen on 2014-03-03
upgrade to 13.10, it's now built-in into the Volume Control, just select "HDMI/DisplayPort built-in audio" instead of "Speaker built-in audio" (on my Lenovo x230)

---

