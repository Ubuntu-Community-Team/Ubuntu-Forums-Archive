---
title: "Intel HD audio (how to install?)"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by adrislayer on 2005-07-30
Hi, since little (this morning) I wanted to install ubuntu on my new pc, so I inserted the cd etc and all worked fine.

But I haven't any sound...

My motherboard is an INTEL Desktop Board D915PCY and has an Intel Hight Definition audio device onboard.

So I went to [www.intel.com](www.intel.com) to get the drivers [http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=1679&DwnldID=7760&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=1679&DwnldID=7760&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

but there isn't any .deb or something like that... I tried to do it manually like it is said on the readme file but... I simply cannot do it myself.

So please, help me, without sound, a computer isn't interesting...

I don't know how to do...

thanks for all

---

### Post by jasmuz on 2005-07-30
Did you check into your alsamixergui program, sometimes sound is unabled there.

---

### Post by GrootBrak on 2005-07-30
[QUOTE=adrislayer]Hi, since little (this morning) I wanted to install ubuntu on my new pc, so I inserted the cd etc and all worked fine.

But I haven't any sound...

My motherboard is an INTEL Desktop Board D915PCY and has an Intel Hight Definition audio device onboard.

So I went to [www.intel.com](www.intel.com) to get the drivers [http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=1679&DwnldID=7760&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=1679&DwnldID=7760&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

but there isn't any .deb or something like that... I tried to do it manually like it is said on the readme file but... I simply cannot do it myself.

So please, help me, without sound, a computer isn't interesting...

I don't know how to do...

thanks for all[/QUOTE]
 Bet you will battle yourself blue!!! I have the D915GEV board. Same problem with the intel driver. Got to "make install" and then it won't. So I went the forum Linuxquestions.org. Got some better help there. Search under this username "GreatBrak" and see if the info will get yours up and running. Still won't work for me, though. I've tried the method in the [www.alsa-project.org](www.alsa-project.org), but still dead quite around here. Dunno why fairly "simple" instructions won't work.

If your sound comes on, let me know how you did it, OK?

BTW Running  command alsamixer gives me this error "function snd_ctl_open failed for default: No such device" And yes alsamixer is installed.

---

### Post by adrislayer on 2005-07-30
I have started to look around and tried some things but since I'm beginer, it isn't easy for me.

So, may I ask U some simple question?

how do I know if alsa is correctly installed? also, i installed alsa-source with
apt-get install alsa-source
I don't know where it put the sources, I found only one archive in /usr/src/ but it is still compressed...

I have followed the readme of manual installation much more further than before. I arrive at step 9 but i've got some errors when tried to do ./build.sh install

[ftp://aiedownload.intel.com/df-support/7760/ENG/IntelReadme_HD_Audio_1.5_Beta.pdf](ftp://aiedownload.intel.com/df-support/7760/ENG/IntelReadme_HD_Audio_1.5_Beta.pdf)
for the readme file.

And of course I will warn U if I get it to work fine.

---

### Post by traaf on 2005-07-31
i have this audio soundcard on a MB asus p5gd1
it is based on a realtek chipset
i found appropriate driver here
[http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs)

---

### Post by GrootBrak on 2005-07-31
[QUOTE=adrislayer]I have started to look around and tried some things but since I'm beginer, it isn't easy for me.

So, may I ask U some simple question?

how do I know if alsa is correctly installed? also, i installed alsa-source with
apt-get install alsa-source
I don't know where it put the sources, I found only one archive in /usr/src/ but it is still compressed...

I have followed the readme of manual installation much more further than before. I arrive at step 9 but i've got some errors when tried to do ./build.sh install

[ftp://aiedownload.intel.com/df-support/7760/ENG/IntelReadme_HD_Audio_1.5_Beta.pdf](ftp://aiedownload.intel.com/df-support/7760/ENG/IntelReadme_HD_Audio_1.5_Beta.pdf)
for the readme file.

And of course I will warn U if I get it to work fine.[/QUOTE]
 > I have followed the readme of manual installation much more further than before. I arrive at step 9 but i've got some errors when tried to do ./build.sh install

Got to the same point with the Intel driver installation. Got nowhere after spending at least 40 hours just reading, downloading, and trying to install sound!!! If you check Intel's website, they list our boards as having the ALC860 codecs but the install manaul instructs to use ALC880. 

I will try the download from realtek and hope that it will work. As mentioned, go to [www.linuxquestions.org](www.linuxquestions.org) and search under username Greatbrak, there you will find an ever growing list of things that goes "bump." The oaks trying to help me is superstars, but unfortunately their patience has not rewarded them. Neither have the given up it seems!

---

