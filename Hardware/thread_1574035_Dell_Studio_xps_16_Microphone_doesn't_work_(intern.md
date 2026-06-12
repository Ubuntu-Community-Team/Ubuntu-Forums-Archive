---
title: "Dell Studio xps 16 Microphone doesn't work (internal and external)"
date: 2010-09-13
forum: Hardware
---

### Post by danbaark on 2010-09-13
Hi,

I'm using Ubuntu 10.04 on a Dell XPS 16 and get no sound from the internal or external microphone (opening sound preferences and selecting the input tab doesn't even find one even if one is plugged in)

I had a similar (and possibly related) issue with external speakers not working but that was resolved by adding 

options snd-hda-intel model=dell-m6

to the alsa-base.conf file

Can anybody help me here? Thank you very much.

---

### Post by CuraHack on 2010-09-25
How have you solved this problem? I still can't hear my internal nor external mic.

I added this to my alsa-base.conf
```
options snd-hda-intel model=dell-md6
options snd-hda-intel model=dell-eq
```

---

### Post by danbaark on 2010-09-25
On mine I found that if you go into the sound preferences menu, hardware tab, at the bottom there a section called settings for the selected device. I found that mine was set to an output only setting (hence no microphone input).

I think default was Analog stereo output. Changing it to Analog surround 4.0 output + Analog stero input fixed my problem.

Hope that helps.

---

### Post by ronjouch on 2011-05-07
Hi there,

Got the same problem on my Dell Studio XPS 16 (1645 to be precise) when upgrading to 11.04 final (Natty Narwhal). The option that did the trick was
```
options snd-hda-intel model=dell-m6-dmic
```
If that doesn't work for you, here is the log of the discussion I had in #alsa on Freenode:
> <ronj> Hi, I just upgraded my Dell XPS 16 to Ubuntu 11.04. Microphone used to work great under 10.04 and 10.10, but here I can't get it to work. Pulseaudio is running and in my sound preferences I tried the various "Hardware Profiles", as well as differents "Connectors", so I am wondering if could be a ALSA issue though I'm not sure at all... Could anybody help me diagnose?
<gnubien> ronj what kind of mic? internal,external,usb,bluetooth,headset?
<ronj> gnubien, it is an internal mic
<gnubien> laptop or netbook?
<ronj> laptop. audio card is a Intel HDA
<gnubien> ronj tried any alsa model options when alsa starts?
<ronj> gnubien, I'm not sure this is what you mean (I'm a beginner regarding ALSA) but I tried adding options snd-hda-intel model=dell-md6 and options snd-hda-intel model=dell-eq in my alsa-base.conf as mentioned here: [http://ubuntuforums.org/showthread.php?t=1574035](http://ubuntuforums.org/showthread.php?t=1574035) , without success
<ronj> gnubien, that's all I tried regarding alsa, else I fiddled in ubuntu's Sound Preferences and pavucontrol
<gnubien> ronj how old is your PC? days? weeks? months? years?
<ronj> 1year, used to work fine without any configuration in the two previous ubuntu releases
<gnubien> ronj need more info; run this command and choose 'upload' when you run the script: wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
<gnubien> ronj paste the url the script prints to this channel
<ronj> gnubien, here it is: [http://www.alsa-project.org/db/?f=7861ee7cc9fe07353670f88c31d4227d74ebd9a1](http://www.alsa-project.org/db/?f=7861ee7cc9fe07353670f88c31d4227d74ebd9a1) . That's a nice diagnosis script you have here :)
<gnubien> ronj: script in use last 3 years, really helpful
<gnubien> ronj your sound card's Codec: IDT 92HD73C1X5      
<gnubien> ronj: alsa model options depend on installed alsa drivers version and card's codec
<gnubien> ronj: model options for your card: [http://sprunge.us/DVee](http://sprunge.us/DVee)
<gnubien> ronj: if analog mic try this: model=dell-m6-amic
<gnubien> ronj: if digital mic try this: model=dell-m6-dmic
<gnubien> ronj: run alsamixer after you run alsa force-reload and unmute and set volumes on any new controls, test mic
<gnubien> ronj run this command and talk into the mic and watch the volume meter for movement, volume meter is the last line of output in the terminal, report problems: arecord -f cd -vv /dev/null
<ronj> gnubien, thanks, going to try this. I should set it in /etc/modprobe.d/alsa-base.conf , right?
<gnubien> yea, that is the file to edit
<gnubien> ronj: this line in that file: options snd-hda-intel model=dell-m6-amic
<ronj> gnubien, GREAT
<ronj> dell-m6-dmic works :)
<ronj> I owe you a beer!
<gnubien> nice, have fun ;)
<gnubien> ronj: email me a cold beer ;)
<ronj> gnubien, one question about your diagnosis, how did you find "<gnubien> ronj: model options for your card: http://sprunge.us/DVee"
<gnubien> ok, got a url...
<gnubien> ronj search for the model options for your sound cards codec at [http://home.roadrunner.com/~infofiles/models/model.options.for.alsa.23](http://home.roadrunner.com/~infofiles/models/model.options.for.alsa.23)
<gnubien> ronj: search for 92HD73
<gnubien> ronj: that file is from alsa drivers source tarball, file name HDA_INTEL-MODELs or the like 
<ronj> gnubien, ok
<ronj> gnubien, last thing: do you think I should file a bug to improve the default behavior? If so, where? Linux/ALSA? Ubuntu?
<gnubien> ronj: try ubuntu forums first, if no fix found then...
<gnubien> ronj search for  at these sites? [http://news.gmane.org/gmane.linux.alsa.devel](http://news.gmane.org/gmane.linux.alsa.devel)  [http://www.mail-archive.com/alsa-user@lists.sourceforge.net](http://www.mail-archive.com/alsa-user@lists.sourceforge.net)
<ronj> ok
<gnubien> ronj: if no fix found then...
<gnubien> ronj post a email bug report at the alsa-devel forum and include the url that the alsa-info script created as a reference. file the bug under your codec for your card, its listed in the url that the alsa-info script created. [http://mailman.alsa-project.org/mailman/listinfo/alsa-devel](http://mailman.alsa-project.org/mailman/listinfo/alsa-devel)
<ronj> gnubien, perfect. thanks again :) , have a nice weekend

---

### Post by aum11 on 2011-07-19
Thanks so much...this also solved my dell studio 15 microphone problems.

---

### Post by swaroop.hangal on 2012-05-09
Hi! Sorry to reopen such an old thread...Running Ubuntu 11.04 2.6.38-14-generic on a Dell Studio 1555 laptop. Internal Mic array not working. It used to work perfectly on 10.10. tried everything given on this thread ... Please help

---

