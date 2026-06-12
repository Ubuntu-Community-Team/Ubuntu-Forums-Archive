---
title: "dual screen crashes computer"
date: 2008-11-11
forum: General Help
---

### Post by holdie on 2008-11-11
I'm not really sure why this happened now, as I've been using my TV as a second monitor with an S-video cable for a while after upgrading to Ibex, but...

Recently, I tried to enable the TV as an extension to my laptop, when I did this, both screens began to flicker black for like 10 seconds, then a message popped up on my laptop saying that there was something wrong with the graphics and it had to run in low graphics mode...

When I restart the computer with S-video plugged in, the same thing happens...when I don't have S-video plugged in the computer boots up normally

I tried editing the settings for a second screen booting from just the laptop, but it didn't do any good.

Any ideas?

ps: using an ati radeon x300 with the ATI proprietary driver and compiz disabled

---

### Post by Neo_The_User on 2008-11-11
What version of Ubuntu are you using?

---

### Post by holdie on 2008-11-11
Ibex

---

### Post by Neo_The_User on 2008-11-11
Ever since 7.10, I've been building the drivers and installing the drivers for ati from the ati website. I hate the proprietary drivers. I just tried them and I got the same problem as you. If you want me to write you a guide on building and installing the ati drivers, I'll be happy to do that.

---

### Post by holdie on 2008-11-11
Interesting...I always thought the proprietary drivers were the same as those offered from the ATI website...is it a very difficult or dangerous process?  I've got a bit of experience configuring Xorg and such since I've been using ubuntu since edgy

---

### Post by Neo_The_User on 2008-11-12
Meh its not dangerous. It was for me the first time so I compiled the restricted modules from source in order to avoid the DKMS failed to do whatever whatever and I booted up in "Out of Range" all the time but you might not have to do all that. I'm using an older card anyway with 2 monitors so I had to go through a lot of trouble. Doing the following commands should be enough for you.

Open up terminal and follow this carefully all in your home folder. Do not cd to anything

```

sudo apt-get update

sudo apt-get install build-essential dh-make cdbs dkms libstdc++5 fakeroot debconf debhelper linux-headers-$(uname -r)

sudo apt-get install linux-restricted-modules

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run

sh ati-driver-installer-8-10-x86.x86_64.run --buildpkg Ubuntu/intrepid

sudo gedit /etc/default/linux-restricted-modules-common

```

All the way at the bottom of the linux-restricted-modules-common file, IN BETWEEN the quotes, type in fglrx. Yes. In disabled_modules.

```

sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb fglrx-modaliases_8.542-0ubuntu1_i386.deb

```

**_IF YOU GET AN ERROR ABOUT DKMS THEN POST THE EXACT ERROR HERE BEFORE DOING ANYTHING ELSE OR YOUR COMPUTER WILL START UP IN OUT OF RANGE!_**

Now you have the fglrx deb packages installed. Now to configure...

```

sudo aticonfig --initial -f

```

Make sure that it says somewhere in the xorg.conf Driver     "fglrx"

If it doesn't then do this command

```

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

```

---

