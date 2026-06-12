---
title: "Latest two/three Ubuntu releases - PCI soundcard detection problems?"
date: 2014-02-21
forum: Hardware
---

### Post by koda95 on 2014-02-21
Hello everyone,

As the title states ... I have a question regarding the latest two/three Ubuntu versions*. *Since years back, I've been using and testing different Ubuntu releases .. including distros based on Ubuntu  (Mint, Ubuntu Studio, etc.). All these years I had no trouble with installation/recognition of my soundcard  - a PCI soundcard - Emu 1212M from Creative. As you know, it's based on the emu10k1 chip. Everytime I tried a new Ubuntu (or other ubuntu-based distros) the soundcard always just WORKED right after installation.

One and a half year ago (*approx.*)  I switched to OpenSuse* -  *and the soundcard worked as it should there too...

**Here's what gives me a headache (*since I'm  NO expert what so ever!*):**
Since last month, I've wanted to return back to Ubuntu ... or to be precise - Ubuntu Studio. After a new installation - my soundcard is NOT detected anymore what-so-ever. I tried several times .. also with Ubuntu, Mint, Ubuntu Studio ... NO WAY - no success! What the system now does ... is to install my  VIDEO-CARD'S HDMI as my _onliest_ "soundcard".  All these mentioned distro's do the same thing as described. I've installed all available ALSA-packages & libraries. 

By some reason ... my PCI soundcard is no longer recognized ... or  SEEN AT ALL. I know the _driver-files_  for emu10k1 exist amongst all other Alsa-drivers on my harddrive (*I found them*). The output of "lspci -v" showed that the card is physically present... but it's apparently "ignored" by the system/OS by some reason.

Then I came across these BUG-reports (*there's a few more bugreports out there)*: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/989955](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/989955)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1184024](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1184024)

**_Final question/summary:_**
....  [SIZE=3][COLOR=#b22222]**Is this a KNOWN issue/bug with the latest Ubuntu releases?  If so ... are there any solution to this?**[/COLOR][/SIZE]


**PS!  **Just to check it out ... I tried FEDORA 20 a few days ago ... soundcard  WORKED immediately ... but I dont want to keep the Fedora. I really want to return back to Ubuntu  (*by different reasons*).

Thanks for all info/help!

---

