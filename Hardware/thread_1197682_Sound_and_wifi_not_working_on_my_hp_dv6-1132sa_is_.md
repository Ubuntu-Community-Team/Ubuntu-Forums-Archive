---
title: "Sound and wifi not working on my hp dv6-1132sa is there a solution?"
date: 2009-06-26
forum: Hardware
---

### Post by ajston on 2009-06-26
Hi all,

I have installed ubuntu 9.04 4 times now on my hp dv6-1132sa laptop and have ran the updates

Everything runs great apart from no sound and no wifi, I have looked into it and looks like there are lots of people with the same sort of problem but I can't find a working solution. Is there a patch or drivers for this, has anyone had any luck fixing the problem???

I am sick of using ms vista and want to take control of my computer! but I fear I'm going to have to revert back as I can't work without wifi or sound, Pleas HELP

Thanks

---

### Post by prithvi on 2009-06-26
i have compaq cq40-133tu laptop. though wireless is been supported, but there is no sound. For wireless working in your laptop activate the properiatory software for 802.xxx wireless driver. you can find that driver in System->Administration->Hardware Drivers->Activate.
If you get the solution for sound problem, please send it to me also.

---

### Post by ajston on 2009-06-26
Thanks, But the only driver in the box is an ati driver , Im currently trying to install ndiswrapper but am having trouble. If I have any success with audio problem ill be sure to let you know. grr

---

### Post by Ayuthia on 2009-06-26
Can you go into the Terminal and run alsamixer?  In the upper left hand corner will be the chip and chipset.  Please post that information here.  

As for your wireless card, please post the results of lspci -nn.  It will help us identify your wireless card.

---

### Post by wirechief on 2009-06-26
Check this thread for your sound issues: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

run this command in /home/user as user:  wget -O alsa-info.sh  [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh

knowing your codec is important for model options, the SoundTroubleshooting

will help you with the details. you can also research the alsa mail list forum here: [http://www.mail-archive.com/alsa-user@lists.sourceforge.net](http://www.mail-archive.com/alsa-user@lists.sourceforge.net)
just click on the link and use the search, knowing your codec is very helpful in that research.

/etc/modprobe.d/alsa-base.conf  is the new location for Jaunty 9.04 and forward for putting the model options coding..

---

### Post by ajston on 2009-06-26
> **Ayuthia said:**
> Can you go into the Terminal and run alsamixer?  In the upper left hand corner will be the chip and chipset.  Please post that information here.  

As for your wireless card, please post the results of lspci -nn.  It will help us identify your wireless card.
[Ayuthia]("http://ubuntuforums.org/member.php?u=286983")

Hi, Audio chip =IDT 92HD75B3X5
      Wifi adap =08:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

Any help would be muchly appreciated

Thanks

---

### Post by Ayuthia on 2009-06-26
For your wireless, try this link:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1179951](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1179951)

As for sound, you can try this link:
[http://kubuntuforums.net/forums/index.php?topic=3104351.0](http://kubuntuforums.net/forums/index.php?topic=3104351.0)

It looks like your sound card should work.  You might check alsamixer and make sure that the sound is not muted (It will be listed as 00 if it is not muted and MM if it is muted--to unmute, press M)

---

