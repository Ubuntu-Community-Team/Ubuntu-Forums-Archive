---
title: "Is there a Tiny Ubuntu OS??"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by iheartubuntu on 2009-04-11
Yesterday, a friend of mine brought over a very small computer. He bought it on ebay for something like $40. It used to be inside of a slot machine in vegas! Its one of those little tiny mac mini's of a computer. It has a celeron processor with 256mb of ram (no case). It doesnt have wifi, but it does have video input/output, two usb ports, firewire, audio jacks, plugin for hard drive (he has a 40gb), plug for a dvd drive, keyboard and mouse jacks, pretty much everything you would need for the most part. We hooked it up, and I tried to install Jaunty Ubuntu, Kubuntu and Xubuntu.... no luck. Almost as if the processor doesnt like anything Ubuntu?  I browsed the web for some smaller linux distros and found [Damn Small Linux]("http://damnsmalllinux.org/index.html") (50mb) which we didnt like, then tried [Puppy Linux]("http://www.puppylinux.org/home") (100mb) which looks great but it didnt want to install onto the HD, and ended up using [TinyMe linux]("http://en.wikipedia.org/wiki/TinyMe") (200mb) which looks awesome and feels like a debian/ubuntu setup. It works great, but since its not Ubuntu, I have to screw around to find different settings since Im used to Ubuntu.

So, my question... Does Ubuntu have a tiny Ubuntu OS we could use? Id rather is it! Is there anything in the works by Ubuntu? Does Ubuntu support any tiny versions out there? Xubuntu just wouldnt work on this system. It was incredibly slow trying to boot up into it. TinyMe booted up quick to the disc, and installed quick to the HD and works pretty good, I must say. But... would love to have a TinyUbuntu. Would Ubuntu Remix do the job?

---

### Post by Aubergines on 2009-04-11
I personally a big fan of [Crunchbang](http://crunchbanglinux.org/) Linux which is basically Ubuntu with Openbox.

[U-Lite](http://u-lite.org) is quite nice too, again based on Ubuntu. It uses LXDE and themed in such a way it looks and feel's much like standard Ubuntu. Screenshots [here](http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Ubuntulite%200.8%20RC2).

---

### Post by cmay on 2009-04-11
i use crunch bang. which is great. but it still needs as many ressurses as ubuntu does. 
i may suggest that you get the debian lenny  lxde+openbox image and try that. if anything should work on a older computer i think it should be this one. i use it on more than one old pc of mine that cant run ubuntu eihter.

---

### Post by ibuclaw on 2009-04-11
TinyME uses the LXDE Desktop. So you could try any of the other Ubuntu/Debian based distros that use it enlisted here: [http://lxde.org/lxde](http://lxde.org/lxde)

Or you could just get the Debian 5.0 XFCE/LXDE Install CD: [http://ftp.tw.debian.org/debian-cd/5.0.0/i386/iso-cd/debian-500-i386-xfce+lxde-CD-1.iso](http://ftp.tw.debian.org/debian-cd/5.0.0/i386/iso-cd/debian-500-i386-xfce+lxde-CD-1.iso)

Regards
Iain

---

### Post by iheartubuntu on 2009-04-11
They ALL look great, thanks for these tips everyone. I also have an older desktop I use here at work to run the music library all day long :) It had "gOS" installed and Ive even upgraded the memory and it is still SLOW. Installing Ubuntu 8.10 on it helped a bit, but not much.

I'll try out the recommendations here. Many thanks!

PS... wouldnt it make sense that these other versions take advantage of the EXT4 file system? I put Jaunty with EXT4 onto my dads new netbook and the thing boots up in 20 seconds. Its just awesome.

---

### Post by Vexed Arcanist on 2009-04-11
> **shirteesdotnet said:**
> They ALL look great, thanks for these tips everyone. I also have an older desktop I use here at work to run the music library all day long :) It had "gOS" installed and Ive even upgraded the memory and it is still SLOW. Installing Ubuntu 8.10 on it helped a bit, but not much.

I'll try out the recommendations here. Many thanks!

PS... wouldnt it make sense that these other versions take advantage of the EXT4 file system? I put Jaunty with EXT4 onto my dads new netbook and the thing boots up in 20 seconds. Its just awesome.

How much ram on the work desktop?  I would recommend CrunchBang, Full or Lite version.  The difference is only in the number of included packages.

For that odd Vegas machine go with a Ubuntu minimal install then use the CrunchBang lite script.  [From the wiki:](http://crunchbanglinux.org/wiki/downloads#lite_edition1)

**CrunchBang Lite Edition**

[1]Prepare a “CLI” only installation of Ubuntu. I find that using the [Ubuntu MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) is best for this.

[2]Download the script with the following command:
```

wget http://crunchbanglinux.org/build-scripts/crunchbang-lite-installer-8.10.02.sh
```

[3]Make the script executable with the following command:

```
chmod +x crunchbang-lite-installer-8.10.02.sh
```

[4]Run the script as root with the following command:

```
sudo ./crunchbang-lite-installer-8.10.02.sh
```

[5]Follow the on-screen instructions and reboot when finished.

---

### Post by iheartubuntu on 2009-04-11
The music computer is one of these cheap emachines (i think thats what it is) that used to be for sale last year at walmart. It had gOS installed, but now using ubuntu 8.x. Got it on a markdown for under $200 since it was a floor model. It had either 256 or 500 mb ram installed and I maxed it out to 1gb just to help it along. Still dog slow really. I just burned and tried Crunchbang on my computer here at home... nice. clean. awesome and it all looks like what im used to, so thanks. Since the music machine at work is used by a few different people, Im wondering if I can get a start/applications button or put stuff on the desktop for everyone at work? Just to make it a bit easier. I hadnt really spent too much time with it.. Busy now that Im home. 

I'll give LXDE a shot and Ubuntu Lite a shot also before I make my final decision. I couldnt seem to find a livecd version of Ubuntu Lite though. Is there such a thing?

---

