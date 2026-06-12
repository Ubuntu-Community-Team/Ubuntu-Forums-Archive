---
title: "Problems Getting Nvidia Card To Work On Asus Laptop"
date: 2013-09-26
forum: Hardware
---

### Post by Reydil on 2013-09-26
So not too long ago I had bought an Asus laptop, specifically this one:
[http://www.bestbuy.com/site/Asus---15.6%26%2334%3B-Touch-Screen-Laptop---8GB-Memory---1TB-Hard-Drive---Black/8937158.p?id=1218954926513&skuId=8937158#tab=specifications](http://www.bestbuy.com/site/Asus---15.6%26%2334%3B-Touch-Screen-Laptop---8GB-Memory---1TB-Hard-Drive---Black/8937158.p?id=1218954926513&skuId=8937158#tab=specifications)

And before I had installed Ubuntu on it I had read up about lack of official optimus support (besides the beta drivers) and the bumblebee project, so after I installed it, the first thing I tried to get done was getting optimus/bumblebee installed and working correctly, though I ran into some problems.

Firstly, my Asus laptop defaults to my intel card, so there was no problem with overheating and things of that nature like others without bumblebee/optimus on their laptops.  And an lspci shows my nvidia card there, so it's recognized.  But I cannot get the nvidia drivers to work, or Ubuntu to switch to that card at all.
I first tried installing bumblebee, bumblebee-nvidia, primus, and primus-libs-ia32 and running a game through steam using the tutorial showed here:
[https://support.steampowered.com/kb_article.php?ref=6316-GJKC-7437](https://support.steampowered.com/kb_article.php?ref=6316-GJKC-7437)

But as soon as I clicked play, the game just crashed.  I wasn't even able to run glxgears with the nividia card.  It keeps saying that the nvidia card 'can't be accessed'.  Even switching the default driver to the nvidia one or just installing the nvidia driver doesn't work as it removes unity.

I'm really stumped, I just don't want my nvidia card to go to waste.

Thanks in advance for any help I may receive!

---

### Post by bcschmerker on 2013-09-27
This is one tricky problem to solve; I see a potential need for the pae:i386 Edition on a system that would otherwise use the AMD64 Edition.  I recently had to update an eMachines®/Acer® EL1210-09 (AMD® Athlon 64® LE-1260, mVIDIA® MCP78S chipset w/ integrated GeForce® 8200 GPU; upgraded with a 500W Shuttle® PSU and Asus® EN210/DI/512MD3(LP) ) to the Packages nvidia-319 and nvidia-settings-319, as nvidia-304 and nvidia-settings-304 could not keep up with upgrades for other Packages in Ubuntu® 12.04-LTS, AMD64 Edition.  (nVIDIA® Driver and Settings Releases 96, 173, 304, and 319 are available from the Ubuntu® Restricted Repository, as of September 2013.)

Several PPA's are necessary for getting Steam® up and running on an Ubuntu® rig.  The article "[Steam for LinUX on Optimus-enabled computer running Ubuntu 12.04-64bits]("http://cjenkins.wordpress.com/2013/01/01/steam-for-linux-on-optimus-enabled-computer-running-ubuntu-12-04-64bits/")" mentioned the following PPA's at Launchpad™:

ppa:bumblebee/stable
ppa:ubuntu-x-swat/x-updates
ppa:zhurikhin/primus

The nVIDIA® Driver and Settings Release 319 may have several bug fixes that escaped Release 310.

---

### Post by Reydil on 2013-09-27
Tried following the article.
Failed on running:
```

optirun glxspheres

```


Got this output:
```

[  185.640612] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initiate the NVIDIA GPU at PCI:4:0:0.  Please

[  185.640641] [ERROR]Aborting because fallback start is disabled.

```

---

### Post by bcschmerker on 2013-09-28
> **Reydil said:**
> Tried following the article.
Failed on running:
```

optirun glxspheres

```


Got this output:
```

[  185.640612] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initiate the NVIDIA GPU at PCI:4:0:0.  Please

[  185.640641] [ERROR]Aborting because fallback start is disabled.

```
Looks as though ye hit the same problem I had with the EL1210-09 my previous Reply; as far as I am aware, the Nouveau driver (package: xserver-xorg-video-nouveau) won't work with multiple GPU's, not with at least one later than an nVIDIA® GT1xx (as used on the GeForce® 9000 Series video-display adapters).  (My EL1210 packs a GT218 in the EN210/DI/512MD3(LP).)  I presume that jockey-text got you nowhere?

---

### Post by Reydil on 2013-09-28
> **bcschmerker said:**
> Looks as though ye hit the same problem I had with the EL1210-09 my previous Reply; as far as I am aware, the Nouveau driver (package: xserver-xorg-video-nouveau) won't work with multiple GPU's, not with at least one later than an nVIDIA® GT1xx (as used on the GeForce® 9000 Series video-display adapters).  (My EL1210 packs a GT218 in the EN210/DI/512MD3(LP).)  I presume that jockey-text got you nowhere?

Been stressing trying to find someone else who had that problem, but the only ones I could find previously were those who had lenovos for which they could just download a 'quick-fix' XD.
I had tried installing nvidia drivers with bumblebee and bumblebee-nvidia but still the same output.  Even when I completely deselected the nouveau drivers.
And this may be a silly question, but what do you mean by 'jockey-text'?

---

### Post by Yellow Pasque on 2013-09-28
It's an nvidia 745m, so you need to be using nvidia 319.xx driver. What version of Ubuntu are you using? If it's 13.04, add this PPA before installing bumblebee: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by tim21 on 2013-09-28
I have the exact same computer.
I installed nvidia 319 drivers using the Additional Drivers application, and when I restarted my computer I couldnt get back into my desktop.  It said there was a problem and wanted to revert back to old drivers, but it wouldnt work.  The only access I has was to command line.
It was the first thing I did after install so I just reinstalled ubuntu and started fresh.  I dont really want to try it again and have to reinstall Ubuntu again.

---

### Post by Yellow Pasque on 2013-09-28
^Is your BIOS set to use Optimus or just the nvidia card by itself? If Optimus, then 'Additional Drivers' should not be prompting you to install the nvidia driver because it breaks the intel driver (as you've discovered). At the prompt, remove the nvidia driver:
```
sudo apt-get purge nvidia-319
sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core
```

---

### Post by Linuxisfast on 2013-09-28
The latest Ubuntu 12.04.3 installs nvidia 319 right out of the box along with nvidia-prime. This makes the nvidia GPU work well on Optimus machine implementing the driver's Optimus solution. Bear in mind this is different than typical Bumblebee discrete switch where nvidia us turned off and then turned on with a command. The nvidia card in Ubuntu's solution is on all the time and uses the Intel card as a discrete sink. The rendering is always done by nvidia. The advantage to this is that game compatibility is not an issue. Also frame rates are far higher than Bumblebee with Optirun or primusrun. Negative effect is that with crammed laptops, cooling becomes an issue as the nvidia GPU dumps heat so when your CPU's are under load, heat dispersion becomes an issue as its unable to dump heat quickly. Hopefully in 13.10 with new 3.11 kernel this issue would be solved with Intel pstate and Intel thermal daemon utility. For now you will have to live with heat and battery consumption.

---

### Post by Reydil on 2013-09-29
> **Temüjin said:**
> It's an nvidia 745m, so you need to be using nvidia 319.xx driver. What version of Ubuntu are you using? If it's 13.04, add this PPA before installing bumblebee: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Already did that, seemed to have still stuck me with 304.  

> **Linuxisfast said:**
> The latest Ubuntu 12.04.3 installs nvidia 319 right out of the box along with nvidia-prime. This makes the nvidia GPU work well on Optimus machine implementing the driver's Optimus solution. Bear in mind this is different than typical Bumblebee discrete switch where nvidia us turned off and then turned on with a command. The nvidia card in Ubuntu's solution is on all the time and uses the Intel card as a discrete sink. The rendering is always done by nvidia. The advantage to this is that game compatibility is not an issue. Also frame rates are far higher than Bumblebee with Optirun or primusrun. Negative effect is that with crammed laptops, cooling becomes an issue as the nvidia GPU dumps heat so when your CPU's are under load, heat dispersion becomes an issue as its unable to dump heat quickly. Hopefully in 13.10 with new 3.11 kernel this issue would be solved with Intel pstate and Intel thermal daemon utility. For now you will have to live with heat and battery consumption.

I have Ubuntu 13.04, are those still installed by default? I haven't noticed any heat problems or anything and I haven't tried running any games. And my battery appears to run just fine (about 5 hours).

---

### Post by tim21 on 2013-09-29
> **Temüjin said:**
> ^Is your BIOS set to use Optimus or just the nvidia card by itself? If Optimus, then 'Additional Drivers' should not be prompting you to install the nvidia driver because it breaks the intel driver (as you've discovered). At the prompt, remove the nvidia driver:
```
sudo apt-get purge nvidia-319
sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core
```

I have no such BIOS settings.  I have had computer before which allow you to select GPU, but this is not one of them.   I find it strange.

Yesterday I installed this:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
Not sure if that was the correct move to make to get the nvidia GPU working.

---

### Post by tim21 on 2013-09-29
> **Linuxisfast said:**
> The latest Ubuntu 12.04.3 installs nvidia 319 right out of the box along with nvidia-prime. This makes the nvidia GPU work well on Optimus machine implementing the driver's Optimus solution. Bear in mind this is different than typical Bumblebee discrete switch where nvidia us turned off and then turned on with a command. The nvidia card in Ubuntu's solution is on all the time and uses the Intel card as a discrete sink. The rendering is always done by nvidia. The advantage to this is that game compatibility is not an issue. Also frame rates are far higher than Bumblebee with Optirun or primusrun. Negative effect is that with crammed laptops, cooling becomes an issue as the nvidia GPU dumps heat so when your CPU's are under load, heat dispersion becomes an issue as its unable to dump heat quickly. Hopefully in 13.10 with new 3.11 kernel this issue would be solved with Intel pstate and Intel thermal daemon utility. For now you will have to live with heat and battery consumption.

Why, then, does the additional drivers list contain the 319 driver as if it were not installed? I have 12.04.3

---

### Post by Linuxisfast on 2013-09-30
> **tim21 said:**
> Why, then, does the additional drivers list contain the 319 driver as if it were not installed? I have 12.04.3

It should have two entries, one with post-release and one standard, usually you will see a green button next to post release and thats normal.

---

### Post by Reydil on 2013-10-01
I've tested it out and so far have gotten pretty good performance in games, but I am using the default nouveau driver.  Is my only option for getting proprietary nvidia drivers working going to have to be downgrading to 12.04.3?

---

### Post by Linuxisfast on 2013-10-02
> **Reydil said:**
> I've tested it out and so far have gotten pretty good performance in games, but I am using the default nouveau driver.  Is my only option for getting proprietary nvidia drivers working going to have to be downgrading to 12.04.3?


If you wish for it to work without any issues.

---

### Post by Reydil on 2013-10-02
> **Linuxisfast said:**
> If you wish for it to work without any issues.
Alright, I'll try that and see if that works.  I wonder why this wasn't included default on latter versions of Ubuntu, and if it will decide to not work again when I eventually have to upgrade to 14.04LTS.

---

