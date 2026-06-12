---
title: "ubuntu-9.04 installed but shows all packages installed"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by spoilingmyself on 2009-09-28
hey!!
i have installed ubuntu 8.10 and then tried installing 9.04 but both are showing the same problems:

1. synaptic package manager shows all packages installed.
2. firefox always prompts to install missing plugins but when i press next it says missing file and exits saying installed.
3. wireless connection doesn't connect though wired connection works fine.
4. no media files are playing. says search for suitable codecs and then says not file containing MPEG layer-1 or ALS found....

i am totally perplexed. i have formatted ny lappy uncountable times... but to no good.
ubuntu 8.04 worked absolutely fine on this same machine. i have been using it since january'09. most of my friends installed ubuntu 8.10 using my cd but this damn cd din't work for me....

please help me.....
please do...

---

### Post by tommcd on 2009-09-29
> **spoilingmyself said:**
> 
1. synaptic package manager shows all packages installed.

You mean that when you open synaptic package manager it shows that every single package in the Ubuntu repos is installed? If so, this is very strange.
Do a clean install of Ubuntu 9.04. Then make sure that the repositories are enabled:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
be sure to click the reload button after enabling the repositories. Then open a terminal: applications > accessories > terminal) and run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
This will get you all the updates for ubuntu. 
Are you installing ubuntu inside windows with wubi? Or are you installing ubuntu to a dedicated partition on the hard drive?
> **spoilingmyself said:**
> 
2. firefox always prompts to install missing plugins but when i press next it says missing file and exits saying installed.
Any plugins you need for firefox can be installed with apt-get or synaptic.
> **spoilingmyself said:**
> 
3. wireless connection doesn't connect though wired connection works fine.

You should probably start a separate thread for your wireless. Anyway, post the output of **lspci** and
 **ifconfig** and **ifconfig -a** so we can see what wireless device you have (lspci) and what is running (ifconfig) and detected (ifconfig -a).
> **spoilingmyself said:**
> 
4. no media files are playing. says search for suitable codecs and then says not file containing MPEG layer-1 or ALS found....
For multimedia codecs enable the medibuntu repos:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
For any other codecs, open a media file with Totem (applications > sound & video > movie player). If it needs a codec it will tell you what is needed and offer to install it. Pretty nice. Or for the "everything but the kitchen sink" method to get all the restricted codecs just install the **ubuntu-restricted-extras** package.

---

### Post by spoilingmyself on 2009-09-29
hey thanks....
that repository issue solved all problems [:)]
next: wireless issue was resolved by starting the wireless in my laptop, actually i didn't press Fn+F5 before connecting to wireless... sorry, but then i remembered this and it started working.
next: firefox i don't how and why has started detecting and installing the plugins, yippie!!
next: yes totem was earlier also suggesting the codecs but it was not downloading or installing them but then today it also downloaded the gstreamer and media files have started playing.

thanks again. i think as soon as i reloaded the third party softwares in software sources, as you suggested, everthing resolved...
:guitar::P

---

