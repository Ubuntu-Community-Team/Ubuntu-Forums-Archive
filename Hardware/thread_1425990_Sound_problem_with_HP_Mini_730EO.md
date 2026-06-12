---
title: "Sound problem with HP Mini 730EO"
date: 2010-03-09
forum: Hardware
---

### Post by Jupeli on 2010-03-09
I have the HP Compaq Mini 730EO laptop onto which I installed Ubuntu 9.10 Karmic. Everything was working fine except for the speakers. I had sound from earphones, though.

I found this: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/64930](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/64930)

I tried to follow these steps from that link: 
> Step 1: Open Terminal from "Applications->Accessories->
Terminal"

Step 2: Run the following commands (copy/paste each command into the Terminal and then hit <enter>)

sudo aptitude update
sudo aptitude install wget build-essential ncurses-dev libncurses5-dev gettext linux-headers-$(uname -r)

# go to your home directory (which is what cd ~ does, so ~ is actually <your homedirectory>)

cd ~
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.19.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.19.tar.bz2)
tar xjf alsa-driver-1.0.19.tar.bz2
tar xjf alsa-lib-1.0.19.tar.bz2
tar xjf alsa-utils-1.0.19.tar.bz2

cd ~/alsa-driver-1.0.19
./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
make
sudo make install

cd ~/alsa-lib-1.0.19
./configure
make
sudo make install

cd ~/alsa-utils-1.0.19
./configure
make
sudo make install

# modify alsa-base file:

sudo gedit /etc/modprobe.d/alsa-base

and change the model options to the following:

options snd-hda-intel model=ref

Reboot your pc and then retest audio (play mp3 file, for example)
At this step ```
make
``` (the first one) I had errors
and now the earphones also stopped working.

Within the massive wall of text returned by the command "make", this seems to be the problem.
```
/home/lauri/alsa-driver-1.0.19/acore/info.c: In function &#8216;snd_info_entry_prepare&#8217;:
/home/lauri/alsa-driver-1.0.19/acore/info.c:161: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/home/lauri/alsa-driver-1.0.19/acore/info.c: In function &#8216;snd_info_register&#8217;:
/home/lauri/alsa-driver-1.0.19/acore/info.c:1020: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;

```


Any ideas?

---

### Post by Jupeli on 2010-03-09
I followed these instructions: [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)
and now the earphones are working again and so are the speakers.

---

