---
title: "Which Ubuntu (if any) should I put on this old machine?"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2009-01-19
I built my dad a new computer and nothing from his old one was compatible so I took it off his hands (I'm such a nice guy!). So now I have this machine that's about 7 years old, I think it's a Pentium 3 with a 64 bit video card, 1.1 USB ports and a CD burner. I want to run Linux on it, maybe even set it up as a media/file/Zoneminder server, who knows. I want to run Linux on it, which distribution would you suggest for this? Will it run Ubuntu? Should I do something else instead? Here are the hard drives I have sitting around that I can throw in it:
40 gig
60 gig
80 gig
3.2 gig

---

### Post by eatberrys on 2009-01-19
Should run ubuntu fine i have instaled it on really old stuff before if not try xubuntu or add fluxbox that will speed it up if its running choppy

---

### Post by theozzlives on 2009-01-19
I'd put the 80 GB in it.

---

### Post by virtuallinux on 2009-01-19
I've run Ubuntu on several P3's in the past, and it seems to do pretty well.  RAM is probably going to be the biggest factor; I wouldn't try running it on less than 256MB.  Xubuntu is a little better suited for older hardware.  If it's an older P3, you may be better off with a more lightweight distro; one I like is Vector Linux.

---

### Post by pansz on 2009-01-19
I don't think any recent desktop will run reasonably well on this computer if you don't have at least 512M memory.

However, if all you planned is a server, it might be better to install the ubuntu-server. Which runs reasonably well under systems with 64M memory.

Setup a server, setup the apache2, php, samba, nfs-kernel-server, ssh-server, etc. it has many greate potentials. When setted up, your server only need a network-wire and the power-cord! no keyboard, no mouse, no monitor is reqired at all. (saves power!)

Mainly you can use ssh to access the server, you can write some php code on your own web page to do simplyfy something as well.

The official ubuntu server guide is very good material to start with.

---

### Post by felker2 on 2009-01-19
As "virtuallinux" says: RAM is an imortant factor. My experience:

400 Mhz & 256 MB RAM with xubuntu: too slow to handle
866 Mhz & 256 MB RAM with xubuntu: nice server

So: how much memory is in the machine? And which CPU frequency?

---

### Post by jrusso2 on 2009-01-19
It would help if we knew how much ram you have.  At least 512 mb to run most things at a decent speed.  Less then that and you make some sacrifices.

---

### Post by DJonsson2008 on 2009-01-19
I loaded Ubuntu Hardy on a PIII with 512 Ram, it worked but was slow not too slow for basic stuff.  NOTE, that 3GB drive will be a bit of a squeeze, rather than mess around with squeezing something on a 3GB drive your time would be better spent picking up a second hand 40 or 80 gig drive for starters, working with a slightly faster 7200rpm model drive seemed to help my experiments here.

---

### Post by jrusso2 on 2009-01-19
A 3.2 gig hard drive is going to be pretty useless unless you want to run FreeDOS or something small like Damn Small or Puppy Linux

---

### Post by HavocXphere on 2009-01-19
I wouldn't put ubuntu on it. It would work...but with periods of sluggishness. I'd rather go with xubuntu and benefit from a bit of extra snappiness.:)

---

### Post by Maheriano on 2009-01-19
Thanks guys, if I install Ubuntu Desktop (I probably won't), then will it run 8.1 or should I go with an older version? I'll most likely end up installing just the server edition and using it that way, plus I'll use a scheduler to fire backups of my files to it every night.

As for specifications, not sure how I forgot to mention how much RAM I have, I think it's 512 but I can always get more super cheap from other people upgrading. I think the front side bus is 800 but don't completely remember, and I think the CPU is 2 gigahertz but again I may have dreamed that. It hasn't been turned on since before I loaded it into my suitcase to take back across the country!

---

### Post by joey-elijah on 2009-01-19
I wouldn't say Ubuntu Desktop is too "beffy" for it. If an ubuntu desktop can run fine on a 630Mhz Celron netbook - it'll fun fine on a PIII.

I hear a lot of people telling people to install some gawd darn awful "mini" lightweight linux that looks like its mother is windows BSOD. 512 RAM and a 2Ghz processor is more than adequete, imo. 

(For future reference, when people imply Ubuntu is too beefy to run on netbooks - but XP isn't - they liken Ubuntu's requirements to Vista. hmm)

---

### Post by snowpine on 2009-01-19
> **Maheriano said:**
> Thanks guys, if I install Ubuntu Desktop (I probably won't), then will it run 8.1 or should I go with an older version? 

Ubuntu 8.04 (April 2008 ) is the long term support release; it will be supported through April 2011. A good choice if you want a stable system you don't have to update often.

Ubuntu 8.10 (October 2008 ) is the current release; it will be supported through April 2010. A good choice if you want the latest version and don't mind updating occasionally.

No reason to go with a pre-2008 release, in my opinion. You'll run into problems when support ends and you stop receiving security updates and bug patches.

---

### Post by Kevbert on 2009-01-19
If you want to use a version of *buntu I'd try Xubuntu which can be found [COLOR="Red"][here]("http://www.xubuntu.org/")[/COLOR].  I'm using it on an Athlon 900MHz with 256Mb RAM. Click on Get Xubuntu and go for 8.04 as it has long term support (and IMHO more stable than 8.10).

---

### Post by DJonsson2008 on 2009-01-19
I ran Ubuntu 8.4 on a PIII 500MHZ 512Mg Ram today with a 7200 rpm drive, and it wasn't bad at all. 

This was an old Intel 440, which I believe has a slower bus, the RAM at least is running at PC100, bus and I think the hds run at ATA33.

---

### Post by Montblanc_Kupo on 2009-01-19
I'm doing something similar. I just got ahold of 4 dell optiplex PIII's that a friend and I are reassembling and plan on putting linux on for... who knows what. heh

I booted them off the LiveCD just to check them out with Ubuntu 8.10 (that's what I had lying around and handy).. they took a little while to boot up, but once I was in the OS they seemed to run okay.

Now I just need to figure out what to do with 4 old linux boxes... heh.

---

### Post by Kevbert on 2009-01-20
> **Montblanc_Kupo said:**
> I'm doing something similar. I just got ahold of 4 dell optiplex PIII's that a friend and I are reassembling and plan on putting linux on for... who knows what. heh

I booted them off the LiveCD just to check them out with Ubuntu 8.10 (that's what I had lying around and handy).. they took a little while to boot up, but once I was in the OS they seemed to run okay.

Now I just need to figure out what to do with 4 old linux boxes... heh.

The biggest problem generally with old PCs is the amount of memory that they support on-board. 
You could try using one as a mail server, another as a customized answer phone for example.

---

### Post by Circus-Killer on 2009-01-20
I recommend the following. Number 1 is both the best choice but also the most resource intenstive. Number 3 would be the least fanciful choice, but will run on really old computers (P2's).

[LIST=1]
[*]Xubuntu
[*]Fluxbuntu
[*]Puppy Linux (not based on ubuntu at all)
[/LIST]

---

### Post by Montblanc_Kupo on 2009-01-21
> **Kevbert said:**
> The biggest problem generally with old PCs is the amount of memory that they support on-board. 
You could try using one as a mail server, another as a customized answer phone for example.

I have no use for those... I was thinking about dedicating them as a SETI farm. hehe

---

### Post by boof1988 on 2009-01-22
> **Montblanc_Kupo said:**
> I have no use for those... I was thinking about dedicating them as a SETI farm. hehe

If you are interested, you could use them for [Folding@Home](http://en.wikipedia.org/wiki/Folding@home).  That is... if you don't have anything against Stanford U. :)

---

### Post by Maheriano on 2009-01-22
Okay so I've decided to do a server since I really don't need a second desktop machine for anything. I see Xubuntu is stripped down but is it stripped more than the server edition of Ubuntu? Is there a server edition of Xubuntu? I guess some simple research would tell me.....but I'm going to download and install tonight hopefully, I just popped the computer together last night after pulling enough dirt out of it to make a sweater. My dad didn't clean it in 8 years of owning it. There's no thermite paste left on the CPU and the heat sink looked like a sleeping hamster.

---

### Post by snowpine on 2009-01-22
> **Maheriano said:**
> Okay so I've decided to do a server since I really don't need a second desktop machine for anything. I see Xubuntu is stripped down but is it stripped more than the server edition of Ubuntu? Is there a server edition of Xubuntu? I guess some simple research would tell me.....but I'm going to download and install tonight hopefully, I just popped the computer together last night after pulling enough dirt out of it to make a sweater. My dad didn't clean it in 8 years of owning it. There's no thermite paste left on the CPU and the heat sink looked like a sleeping hamster.

Xubuntu = Ubuntu + Xfce desktop environment, therefore there is no "Xubuntu server."

Ubuntu server is a command line minimal install plus server applications, and I think what you are looking for in this situation. Good luck!

---

### Post by Maheriano on 2009-01-22
Cool. Last question, do I need a monitor at all to install this? How do I navigate the install menu and making partitions without a monitor? Do I just hook it up desktop style until the install is complete?

After it's installed, how do I connect to it to control it? For example: installing LAMP and Webmin.

---

### Post by boof1988 on 2009-01-22
The way I did it was:
[LIST=1]
[*]Hook up a monitor and install Ubuntu Server
[*]Reboot (due to the install) and check to make sure it boots up properly
[*]Make sure it's hooked to my network
[*]Log onto it from another computer (on my network) using (from terminal):
```
ssh user@local_lan_address #use your user and host address
```
[*]Make sure I can log onto the machine (over my network)
[*]Power off the server:
```
sudo poweroff
```
[*]Remove monitor from server (It only needs the power-cable and the network-cable to function)
[*]Power on server and wait sufficient time for it to boot
[*]Log on to server from a different computer and enjoy
[/LIST]

Sorry if this is not clear or anything... I'm just pretty excited that I was able to get it work, so I wanted to share my experience.

---

