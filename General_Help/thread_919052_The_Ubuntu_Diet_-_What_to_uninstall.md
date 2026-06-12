---
title: "The Ubuntu Diet - What to uninstall"
date: 2008-09-13
forum: General Help
---

### Post by Erdr1ck on 2008-09-13
So I'm working from an EEE PC with a tiny 4 gb SSD, and I need a bit more space to work in.  I'd move to Xubuntu, but A) I like Gnome, and B) I'm not that comfortable with Linux in general yet.  I've already uninstalled the games and a few apps I won't be using, but I was hoping you guys would have some tips for me.

---

### Post by Erdr1ck on 2008-09-13
Also related question: I've got my home directory and such on the slightly slower 16gb SD card, where speed doesn't matter.  Is there a way to move some programs or system files over as well, while leaving the main chunk of the OS on the internal 4gb drive?

---

### Post by WRDN on 2008-09-13
Rather than only removing applications, you could replace them with lighter alternatives. For example, you could replace Open Office Writer with Abiword, and ALL media players with VLC.

---

### Post by Erdr1ck on 2008-09-13
That was the first thing I did, and though it helped it didn't free up as much space as I need.  Any other suggestions?

---

### Post by TenPlus1 on 2008-09-13
Purge things like compiz, tracker, wallpaper/sound/pointer/theme/icon sets, and as mentioned before search for lightweight alternatives to what you do need, there's plenty out there...

---

### Post by hyper_ch on 2008-09-13
why not use the alternate cd to make a base (cli) install and then only install the stuff you need?

---

### Post by Erdr1ck on 2008-09-13
That's what has been recommended to me by my power-user Debian happy friends.  However, this is only my second Linux box ever, so I'm not confident enough that I'll know what I need/don't need.  So I find it easier and less stressful to start with a full install and work my way down.

---

### Post by solarwind on 2008-09-13
Use Arch Linux. You'll be surprised at how easy it is to install (even though it's a do it yourself distro) and you'll get to know your system very well.

[http://www.archlinux.org/](http://www.archlinux.org/)

---

### Post by sebbouckaert on 2008-09-13
I also use Ubuntu on my Asus eee 900. After a first install I had the same problem as you have, not enough diskspace. 

I tried to use the alternate installer, but since I have to boot Ubuntu from an USB stick (I don't have an external CD drive) this didn't work since this alternate installer kept asking for a valid CD device and driver.

However, I found a workaround. Takes a bit more time, but worked for me. 

First, I did a full install (used Ubuntu Eee, instead of standard 8.04). 

Then I removed Gnome by removing all packages as listed on Psychocats's guide [found here]("http://www.psychocats.net/ubuntu/purexfce"), I rebooted, logged in to an xterm session and there I did:

```
sudo apt-get install gnome-core
```

rebooted again, and voila, I had a basic Gnome desktop from where I could install custom apps. After I installed the stuff I need I also did a

```
apt-get clean
``` to remove the apt cache.

Now, even with Open Office and a bunch of other apps installed, I have 1.2 GB free on my 4 GB drive, and also a faster booting system (52 secs counting from Asus splash to working Gnome desktop. Standard install did it in 1 min. 10 secs)

---

### Post by bodhi.zazen on 2008-09-13
As hyper_ch indicated it is far easier to install a minimal system and add in only what is needed. Either way, you need to poke under the hood to learn what you can remove and what packages you need / want.

---

### Post by hyper_ch on 2008-09-14
well, first, you need the base system, then you probabl want x-server, a login manager, and a basic gui (I think gnome-core will do that).

Use apt-get only as aptitude will also installl recommended packages.

Then add the additional repos and start adding the stuff you want. The dependencies will be added automatically.

e.g. you could then run

```

# IMs
sudo apt-get -y install skype amsn

# Burn Programs
sudo apt-get -y install gnomebaker brasero

# IRSSI / OpenSSH
sudo apt-get -y install irssi openssh-server

# Browsers
sudo apt-get -y install firefox kazehakase opera flashplugin-nonfree

# Codecs & players
sudo apt-get -y install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer vlc

# Midnight Commander
sudo apt-get -y install mc

# UNRAR
sudo apt-get -y install unrar

# GParted
sudo apt-get -y install gparted

# OpenOffice
sudo apt-get -y install openoffice.org openoffice.org-gtk

# Numlock & fonts
sudo apt-get -y install numlockx msttcorefonts

```

the "-y" switch will install them automatically... and this is just an example...

It is not required to make categories but you can then use it for later on and more simple modfiy it. You coudld then put it into a bash script (adding #!/bin/bash as first line, remove the "sudo" and then just run that bash script with sudo....)

---

### Post by bornagainpenguin on 2008-10-09
> **Erdr1ck said:**
> So I'm working from an EEE PC with a tiny 4 gb SSD, and I need a bit more space to work in.  I'd move to Xubuntu, but A) I like Gnome, and B) I'm not that comfortable with Linux in general yet.  I've already uninstalled the games and a few apps I won't be using, but I was hoping you guys would have some tips for me.

I think you'll find this thread to be very helpful:
[http://ubuntuforums.org/showthread.php?t=820804](http://ubuntuforums.org/showthread.php?t=820804)

--bornagainpenguin

---

### Post by mikjp on 2008-10-10
You most probably don't need CUPS.

---

