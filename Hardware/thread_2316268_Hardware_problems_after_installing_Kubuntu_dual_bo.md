---
title: "Hardware problems after installing Kubuntu dual boot XPS 13"
date: 2016-03-06
forum: Hardware
---

### Post by noam4 on 2016-03-06
Hi

I have installed Kubuntu 15.10 on my Dell XPS 13 2015 9343 laptop in a dual boot alongside windows 10.
So far seems OK except for some problems:

1) WIFI doesn't work even after installing according to [Dell's instructions]("http://www.dell.com/support/article/uk/en/ukbsdt1/HOW10806/en"). I was able to get internet via an Ethernet - USB adapter. I would mention that when i tested WIFI in the live USB it worked very well.
2) Audio isn't coming out the speakers. Tried to mess a little bit with the settings and was able to get a test voice throughout the settings menu's test. When tried an youtube audio it just didn't work.

Hope for a little help
Thanks

---

### Post by weatherman2 on 2016-03-06
Dell's instructions were for Ubuntu 15.04, so I'm not completely surprised they didn't work for 15.10.  There is a separate Networking & Wireless forum for these kinds of problems (you could request to have this thread moved there); the Broadcom question is a frequently-asked question, should only be a few lines in a terminal to fix itl.  You can probably find a few pages of solutions by web search.  You'll want that Ethernet - USB adapter handy again to download any new packages.

Do you realize you will have to upgrade Ubuntu 15.10 after support ends in a few months?  Did you consider 14.04 LTS which is supported until April 2019 without any upgrades required before then?

If you were able to hear sound in the audio test, then it's probably a matter of playing with the sound settings.  Sorry, I'm not familiar with the sound settings in 15.10.  Try to see if you can listen to say an MP3 file; if you can, then maybe it's something to do with flash.  Are you using Firefox or Chrome or another browser?

---

### Post by noam4 on 2016-03-07
Alright problem solved

Installed [this driver]("https://launchpadlibrarian.net/219070203/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu7_amd64.deb") and work OK.
Had to set the internal audio device (laptop's speakers) to default via settings. Noticed that after rebooting from another OS (i.e Windows) you should cold reset twice in order for audio to work.
Things I haven't tested yet: Bluetooh, Hard Graphics

---

### Post by mörgæs on 2016-03-07
> **noam4 said:**
> Alright problem solved

Good, please mark the thread so.

---

