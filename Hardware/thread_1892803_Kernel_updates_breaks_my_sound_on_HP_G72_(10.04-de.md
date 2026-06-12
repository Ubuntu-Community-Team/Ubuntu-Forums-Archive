---
title: "Kernel updates breaks my sound on HP G72 (10.04-desk-64)"
date: 2011-12-08
forum: Hardware
---

### Post by Dngrsone on 2011-12-08
As I mentioned in [this thread](http://ubuntuforums.org/showthread.php?p=11523913#post11523913), I fixed the sound on my G72 by updating the ALSA drivers in Ubuntu 10.04-desktop-AMD64.

My problem is, every time I update the OS with a new kernel version, the sound breaks again and I have to reinstall, which isn't so much a big deal as it is a big hassle.

So, is there any way to 'fix' this so I don't have to rebuild and reinstall the ALSA drivers again?

---

### Post by Dngrsone on 2011-12-14
Once again, I get to answer my own question... [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

I wrote a quick-and-dirty script based off the instructions in [here](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/):

```
#!/bin/bash

# Update ALSA drivers script

# Stop ALSA-Utils

sudo /sbin/alsa-utils stop

# Install necessary compiling tools

sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev

# Download new ALSA driver, libraries, and utilities

cd ~
rm -rf ~/alsa* ~/.pulse*
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2

# Create folder to compile in and install from

sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .

# Unpack files

sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*

# Compile and install Driver

cd alsa-driver*
sudo ./configure
sudo make
sudo make install

# Compile and install Libraries

cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

# Compile and install Utilities

cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

# Cleanup

rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*

echo You many now restart your computer to complete ALSA update.  Do not forget that the sound is muted by default.
```

---

### Post by brunoscunha on 2011-12-17
Great :D
Will this work on a 32 bits ubuntu with a core2duo?

---

### Post by Dngrsone on 2011-12-17
I don't see why not.

---

### Post by brunoscunha on 2011-12-17
Thanks. I'll try your fix after installing the latest kernel. Because the last time I did it, it broke the sound.

Thanks again

---

