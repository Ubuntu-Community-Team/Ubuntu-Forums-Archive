---
title: "Cannor install driver for sound card"
date: 2017-11-09
forum: Hardware
---

### Post by icit2 on 2017-11-09
I have just got an Asus Xonar DGX sound cardand while the icon comes up on the screen I just hav no idea on what to do with soem of the info presented and I am wondring if 16.04 MATE actually supports the card. 

Any ideas please because I am new to this OS or at least I haven't used it since version 11.4 and not much then because i was so perplexed by the use of the terminal feature.

---

### Post by coffeecat on 2017-11-09
The icon, as you call it, looks as though it is for a CD. Did you put the CD that (presumably) came with the sound card into your optical drive? The screenshot you post shows what looks like what you would expect from inserting a manual and driver CD - the contents of the CD. 

Have you tried simply using the card? Perhaps checking your sound settings? I can't tell you where exactly to look because I have no recent experience of the Mate desktop. The reason I ask is that if what you show is simply the contents of a manual/driver CD, that will be for Windows, and it could be that all the necessary Linux drivers for the device are already compiled into the Ubuntu kernel.

**Edit**: and did you read the readme.txt file? The hint is in the filename. That might have some useful information.

---

### Post by icit2 on 2017-11-09
THanks coffecat mate I wil have another loook but I a begining to think I may have a version of Ubuntu that looks to be really quite compkicated.  thoguht I would surely just install the carsd and thn the driver because the card dosn't work without thet driver I don't know and I shall hav to rethink my options on a Linux based ssytem as it seems everythign i try to do is just so convoluted and there are now obvious simple control panel type apps

---

### Post by vasa1 on 2017-11-09
I had previously asked you to install **inxi** and then provide certain information to let people understand your system. Do you have difficulty doing that? Where are you getting stuck?

See [https://ubuntuforums.org/showthread.php?t=2376908&p=13708441#post13708441](https://ubuntuforums.org/showthread.php?t=2376908&p=13708441#post13708441)

---

### Post by Yellow Pasque on 2017-11-09
The driver is already installed as part of the kernel (module is named snd-oxygen). When I had my Xonar DG, I had to change this setting:
[https://askubuntu.com/a/687812/738808](https://askubuntu.com/a/687812/738808)

---

### Post by icit2 on 2017-11-09
> **Temüjin said:**
> The driver is already installed as part of the kernel (module is named snd-oxygen). When I had my Xonar DG, I had to change this setting:
[https://askubuntu.com/a/687812/738808](https://askubuntu.com/a/687812/738808)

Ok so I got to the alsamixer but it is not showing up my Xonar card and am at a loss at what to do about it because I cannot add a driver for it .

Coffecat I have no idea of what inxi means and I am again wondering if I have a version of Ubuntu that I can use reasonably easy. Look I am really sorry but having to work through the terminal all the time is an absolute mystery to me because I don't have the experience of it in Linux.

---

### Post by coffeecat on 2017-11-10
@icit2, if other members post links, you need to read them and follow them without making assumptions. There is nothing about adding a driver in Temüjin's link. As Temüjin said, the necessary driver is already installed as part of the kernel. Also, vasa1's link about getting information from inxi is clear. That is at least twice now that vasa1 has asked for that information, and twice that you have not provided it. To get help here, you have to meet others half-way - help others to help you. By not following advice you have already lost one of the people who were trying to help you - they have unsubscribed from this thread. And, by the way, it was vasa1, not myself, who mentioned inxi.

You don't have to work with the terminal "all the time", but occasionally it becomes not just necessary, but valuable. This is true of all versions of Ubuntu, and indeed of all Linux distros.

---

### Post by Yellow Pasque on 2017-11-11
The card doesn't show up in alsamixer when you hit "F6"?
Get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

I'm also completely lost on what you're trying to do with the CD. The screenshots don't indicate there is anything other than Windows drivers on it. Even if there was a Linux driver on it, it would probably be too old to be useful.
Once again, kernel driver support for the DGX was added back in 2012 in kernel 3.5, so you shouldn't need to install a driver. This is not Windows!

---

