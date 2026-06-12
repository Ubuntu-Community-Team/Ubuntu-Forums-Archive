---
title: "Wireless Access - Sony VAIO problem"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by bullraiser on 2007-03-06
Hi, 

I made a fresh dual installation on my Sony VAIO SZ1XP/C and basic installation went smoothly except for few issues:

1. Wireless Connection NOT working. 

	I tried to open the Networking application and enabled Wireless connection by providing the correct ESSID & Network Key. I couldn't able to see any network connection made after enabling this. Do I need to do anything apart from this?

2. nVidia Graphics Card Installation

	Do anyone provide me the installation details for my nVidia card. I couldnt see the graphics card is been recognised by default/installed. 

3. Tottem Movie Player

	When I tried to play a DVD movie, I got an error with "Codec not available". Should I have to connect to the internet and download the neccessary codec first?

Appreciate, if someone can help me on this.

Cheers
--

---

### Post by renzokuken on 2007-03-06
1. wireless can be a tricky one. we need to know the make and chipset of your wireless card. the following commands may help

```
lspci
```
```
lsusb
```

2. official nvidia drivers are not included by default. tseliot's Envy script can install them for you easily  --> check out the projects / guides sections at [www.albertomilone.com](www.albertomilone.com) for Envy and a howto

3. codecs are also not installed by default. Automatix or Easybuntu can do it for you ( [www.automatix.com](www.automatix.com) )

---

### Post by Trsnrtr on 2007-03-06
> **bullraiser said:**
> Hi, 

I made a fresh dual installation on my Sony VAIO SZ1XP/C and basic installation went smoothly except for few issues:

1. Wireless Connection NOT working. 

	I tried to open the Networking application and enabled Wireless connection by providing the correct ESSID & Network Key. I couldn't able to see any network connection made after enabling this. Do I need to do anything apart from this?

2. nVidia Graphics Card Installation

	Do anyone provide me the installation details for my nVidia card. I couldnt see the graphics card is been recognised by default/installed. 

3. Tottem Movie Player

	When I tried to play a DVD movie, I got an error with "Codec not available". Should I have to connect to the internet and download the neccessary codec first?

Appreciate, if someone can help me on this.

Cheers
--

I have a Sony Vaio VGN-SZ120P and the wireless works fine.  I did have to turn off the "Wired Connection" under Networking after I set my wireless parameters.  For some reason, I can't seem to have both turned on at the same time.

As far as video goes.  I use the envy script after every install or kernel upgrade.

Dennis

---

### Post by bullraiser on 2007-03-07
[QUOTE=renzokuken;2255059]1. wireless can be a tricky one. we need to know the make and chipset of your wireless card. the following commands may help

It's Intel PRO Wireless card.
I will run the command and will let you know the results.

---

### Post by bullraiser on 2007-03-07
How's is it possible for you to have the Wireless run by default?

Can you let me know the detailed steps you have entered while setting up Wireless connection?

---

### Post by SendDerek on 2007-03-07
After installing network manager, my wireless (intel pro 3945ABG) worked fine with no further steps necissary.  I'd recommend giving networkmanager a try.

---

### Post by renzokuken on 2007-03-08
run

```
sudo apt-get install network-manager-gnome
```

---

### Post by bullraiser on 2007-03-12
> **renzokuken said:**
> run

```
sudo apt-get install network-manager-gnome
```


Since I am not connected to Internet, where would I get this package from?
Is this by default copied to the system but not installed by default?
Or, should I have to download from the internet to a storage device and then try installing it?
Or, is this package is on the installable CD?

How did you tried installing without connecting to the internet?

Let me know, as its been weird staying out of internet for quite sometime.

Thanks--

---

### Post by renzokuken on 2007-03-12
i'm assuming you are using Edgy here, but network manager can be gotten from

[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/)

you will need network-manager and network-manager-gnome (and maybe other dependencies but i dont there are any)


to install a .deb file manually run

do this first for network-manager, then network-manager-gnome (make sure you get the right architecture (i386, amd64 etc)

```

cd /path/to/deb/file
sudo dpkg -i name_of_file.deb

```

---

### Post by bullraiser on 2007-03-12
Inaddition to the above problem, I also cant able to connect to Windows shared drive through Samba or Network shared drives.

I am getting some error related to Samba. Isin't Samba is by default installed and shouldnt I be able to connect to Windows shared drive?

Let me know, if I  need to install anyother services/package ?

TIA

---

### Post by renzokuken on 2007-03-12
samba has to be set up correctly first before it will see networked windows pcs. im no expert with Samba but there are some excellent guides about in this forum and in the wiki and help pages

wiki.ubuntu.com
help.ubuntu.com
ubuntuguide.org

---

