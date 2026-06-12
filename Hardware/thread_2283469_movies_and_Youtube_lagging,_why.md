---
title: "movies and Youtube lagging, why?"
date: 2015-06-22
forum: Hardware
---

### Post by mlvmhn on 2015-06-22
When i watch HD vids and clips from Youtube on my laptop, you can see that my screen is lagging and flickering. Also when i watch 1080p bluray-rips the same thing occurs. 

I have recently installed Ubuntu 14.10 to it with all the basic settings only. The drivers that comes with the installation is the ones i use at the moment. 

The laptop is an HP 550 with 2 GB RAM and a 2 Ghz Intel processor: [http://www.notebookcheck.net/Review-HP-550-Notebook.15963.0.html](http://www.notebookcheck.net/Review-HP-550-Notebook.15963.0.html)

It is connected by VGA cable to my 42" LCD, and i use WiFi to Internet. 

What is the issue here?

---

### Post by kerry_s on 2015-06-22
your specs are not good enough for hd/1080p, at the most 720p local, 480p streaming.
your also running standard ubuntu, which would be heavy on 2gb ram, i doubt you even have enough ram left over for much of anything.

first you need to downgrade your desktop ui to something lighter, without fancy effects. xubuntu, ubuntu-mate, lubuntu would be the 1's you should try. 

i'm a ubuntu-mate 15.04 person myself, have similar specs as yours on my hp mini-210 netbook.

so install something lighter & after your install is finished, grab zram-config, that will help with your low ram issue.

---

### Post by mlvmhn on 2015-06-22
k, 720p works fine but not 1080p. 

what is the difference between Ubuntu and Lubuntu?

does VLC and Chromium work fine in Lubuntu?

---

### Post by kerry_s on 2015-06-22
yeah, your specs do not support 1080p

ubuntu uses unity, lubuntu uses lxde desktop. it's just a heavy vs light gui.

yes, same things will work. i'm not really a big lxde fan, it always feels like a bunch of stuff just slapped together to make the desktop.

ubuntu-mate has vlc as the standard vid player, you only need install chromium. i recommend version 15.04, cause that's when it got some good tweaks.
[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

---

### Post by mlvmhn on 2015-06-22
Or i just stick to 720p versions?

Where do i find Lubuntu btw?

Can i run a dual-boot?

---

### Post by kerry_s on 2015-06-22
yes, 720p is the best your going to get, there may be some 1080p you could swing if it has a low frame rate or maybe if you do a huge buffer, but if you want it to work for sure 720p or less. i mostly only do 480p local on mine & for youtube i have it set at 360p for streaming.

[http://lubuntu.net/](http://lubuntu.net/)

yes

---

### Post by mlvmhn on 2015-06-22
Ok, so changing to Lubuntu will not help me playing 1080p videos better?

---

### Post by kerry_s on 2015-06-22
> **mikael.hansson.967 said:**
> Ok, so changing to Lubuntu will not help me playing 1080p videos better?

yeap. your hardware is just not built for that. you have a dual core cpu, 2gb ram, intel graphics with shared memory, maybe google it, i been known to be wrong a many of times. :)

i'm just going off experience here, the old been there, done that thing. lol

---

### Post by coffeecat on 2015-06-22
@mikael.hansson.967, the link you gave doesn't give clear specifications for your machine. Please post the output of the following terminal commands:

```
lscpu
lspci | grep VGA
```

People frequently claim that modestly specified machines can't run Unity satisfactorily or play 1080 HD video. Oftentimes, this is simply wrong. I have a really cheap 'n' cheerful small Acer laptop with Intel Celeron 2-core N2830 @ 2.16 GHz, and integrated Intel graphics. It runs Unity just fine **and** can play 1080 HD videos without lagging when connected to a HD LCD. The main difference between my setup and yours is that you have 2GB RAM and I have 4GB RAM. I am a little sceptical that 2GB RAM is not enough to play full HD video, but that might be worth looking at if my cable suggestion below doesn't help. 

The other important difference is that I am using a HDMI cable whereas you are using VGA. I wonder if that may be important. Do you have an HDMI output on your laptop and can you connect via HDMI to your LCD?

---

### Post by mlvmhn on 2015-06-22
Ok, i just have VGA from my laptop but my LCD has HDMI. Playing 720p vids is no problem ,but as soon as i choose 1080p the video starts to lag and flicker. 

Someone told me to change from Ubuntu to Lubuntu. Would that help me with my low RAM issue?

What is the system requirements for Lubuntu?

---

### Post by weatherman2 on 2015-06-22
I would try installing Gnome Flashback instead of switching to Lubuntu, which is a radical change in desktop.  At least with Gnome Flashback, it's easy to switch desktops, back and forth to Unity if you want, without doing dual boot.  I use Gnome Flashback (Metacity) for most installs on older hardware and it works fine, even with only 2GB of RAM and a slower CPU.

I am not doing 1080p video, though.  I would expect you need beefier hardware for that.  If that HP really has an old Celeron M CPU, it is going to be pretty slow with any desktop you install.  I would personally consider upgrading to a Pentium M CPU, though I understand that's beyond the average person's ability to do in a laptop.

---

### Post by coffeecat on 2015-06-22
Changing from Ubuntu to Lubuntu will help **if** RAM is indeed the issue. 

You'll find some system requirements on the Lubuntu site here: [http://lubuntu.net/](http://lubuntu.net/)

If you want to avoid the hassle of a complete re-install, one option would be to install the Lubuntu desktop in Ubuntu and choose the LXDE desktop from the login screen. Whatever you choose, Lubuntu is a good derivative of Ubuntu and you may find you prefer it.

---

### Post by mlvmhn on 2015-06-22
> **coffeecat said:**
> Changing from Ubuntu to Lubuntu will help **if** RAM is indeed the issue. 

You'll find some system requirements on the Lubuntu site here: [http://lubuntu.net/](http://lubuntu.net/)

If you want to avoid the hassle of a complete re-install, one option would be to install the Lubuntu desktop in Ubuntu and choose the LXDE desktop from the login screen. Whatever you choose, Lubuntu is a good derivative of Ubuntu and you may find you prefer it.

Sounds like a good idea, how do i manage to do this?

---

### Post by coffeecat on 2015-06-22
If you want to have both Unity and the Lubuntu desktop (LXDE), you need to install the metapackage lubuntu-desktop which will drag in about 100-150 MB of dependencies. You can do this from the terminal with apt-get or with Synaptic if you have installed that, or with the Ubuntu Software Centre.

A couple of cautions if you do that. The bootup purple Ubuntu splash screen will be replaced with the Lubuntu blue one, and you will get the Lubuntu login screen. You can choose which desktop environment you want to log into by clicking on an icon near the top right. Also - if you install more than one desktop, you can sometimes get minor glitches in one desktop or the other.

---

### Post by mlvmhn on 2015-06-22
Ok, but i think i will stick to my present installation of Ubuntu 14.04 LTS.

---

