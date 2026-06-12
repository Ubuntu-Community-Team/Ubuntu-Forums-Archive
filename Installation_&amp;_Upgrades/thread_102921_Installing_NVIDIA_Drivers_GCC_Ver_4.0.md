---
title: "Installing NVIDIA Drivers GCC Ver 4.0"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by Ted_Smith on 2005-12-13
I really sorry if this is described elsewhere, but I've done a search of 'GCC 4.0' and I get hundred of returned hits but the titles don't help me. Excuse the bad explanation - but this is all new to me. 

I am trying to install the NVIDIA graphics driver on a standalone PC that is **not connected to Internet**. The reason I am doing that is because the only screen res I have as an option is 640 and 60Hz and it's on a 24" monitor! 

I have followed the HOWTO guide provided by tseliot (which worked at home but that PC was connected to Internet). Prior to running the actual installer, when I do the GCC=.. bit I was told the latest version was already in use. Anyway, I launch the installer and it asks me to download a new kernal interface. But because I have no connection I said no. So it tries to compile the kernal itself. But while running it tells me that the GCC compiler is different to the compiler that compiled the NVIDIA Kernal. It states that it was compiled with GCC 4.0 instead of 3.4 or something like that. So I went back to Terminal and told it to use GCC=3.4 instead of using 4.0. So I tried changing the 'CC=gcc-3.4'

But then the installer said 'gcc-version-check failed followed by "usr/src/nv/conftest.sh line 19: gcc 3.4 command not found". It says if I know what I'm doing to click No and it carries on for a bit then fails again Unable to Determine the Version of the Kernal Sources in /lib/modules/2.6.12.-9-386/build etc etc etc

In other words, it hasn't worked, it can't connect to net to fix itself. 

Any idea how I go about fixing this? I have a 24" Dell monitor with a 600x600 res. It looks daft! Using Ubuntu Breezy Badger 5.10

Thanks

Ted

(Ubuntu Breezy Badger 5.10)

---

### Post by Ted_Smith on 2005-12-13
Fixed it.

I ran the 

sudo dpkg-reconfigure xserver-xorg

command at the command prompt and set it up that way rather than relying on the auto features of the Ubuntu installer. It all seems to be fine now - 1600 x 1200 again! Bravo.

---

