---
title: "Resolution Dell Inspirion 1300"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by dogman24 on 2006-08-01
Can anybody plan out a step by step solution to fixing the resolution on a Dell Inspirion 1300 laptop?

Dapper installs 1024x768 as standard, but my laptop monitor doesnt really like it, so it becomes stretched. The resolution for the monitor is meant to be 1280x800 (WXGA 16:10).

---

### Post by Jagot on 2006-08-01
I have exactly the same laptop.

You need to first enable the universe repo.  See either of these two links:

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then, from Terminal:

```
sudo aptitude update
sudo aptitude install 915resolution
```

The package automatically detects what the correct resolution should be, so all you need to do is restart the xserver - press ctrl+alt+backspace.

---

### Post by dogman24 on 2006-08-01
Thanks a lot, that worked!

Just remember:

To edit the sources.list, copy this into terminal

```
sudo gedit /etc/apt/sources.list
```

---

### Post by gholen on 2006-08-01
Will borrow this thread for some questions about the dell 1300, or in the US and Canada named as B130.

How are this laptop for you, does it work good?
Any tips?
Any fallback's that we owners of the dell 1300 / B130 should know about?

For me, this i a good laptop for Linux, and the only thing that is bad with it, is that the Broadcom WiFi card is a Broadcom card.
It does work under the kernel 2.6.17-2, but how many make their own kernels...?


Ambjörn AKA gholen

---

### Post by Jagot on 2006-08-01
The laptop is fine, though it could do with upping the RAM from the default config that came with it for me - 256MB - when I can be bothered I'll buy a 512MB stick.

There are various threads regarding setting up the wireless card - BCM4318 - a lot of people are using fwcutter and that kind of thing, but ndiswrapper works for me.  You need to have the Windows driver for the card - bcmwl5.inf.  Strangely the drivers supplied on Dell's web site did not work - I had to get mine from the Acer web site, but anyway - this is how I  get it working:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

As Dapper comes with partial drivers for Broadcom cards, the card is detected but does not work properly with the default set up, so, as you can see, the method I use involves blacklisting the drivers that come with Dapper so as that ndiswrapper can control it.

There isn't really anything else you need to know.  Everything else seems to work ok - even suspend-to-ram.

---

### Post by gholen on 2006-08-01
> There isn't really anything else you need to know. Everything else seems to work ok - even suspend-to-ram.

Have you got the suspend to disk working?
Thats my biggest problem now, but i have solved one specifik detail, the hotkeys!

Do this:
```
sudo apt-get update
sudo apt-get install hotkeys hotkeys-setup
```

then:

```
hotkeys -l inspiron8100 -d /path/to/cdrom
```

```
cd /etc
sudo nano hotkeys.conf
```

```

############################################################
# Global configuration for hotkeys                         #
############################################################

# These are the default values.
# A line starting with # is a comment.

### Specify the default keyboard  (without the .def extension) so you
### don't need to specify -t every time
Kbd=inspiron8100 <--add your keyboard model here
CDROM=/dev/hdb <-----here be cdrom 

# PrevTrack=xmms --rew
# Play=xmms --play-pause
# Stop=xmms --stop
# Pause=xmms --pause
# NextTrack=xmms --fwd
# Rewind=

# WebBrowser=mozilla
# Email=mozilla -mail
# Calculator=xcalc
# FileManager=gmc
# MyComputer=gmc
# MyDocuments=gmc
# Favorites=gnome-moz-remote --remote=openBookmarks
# Transfer=gtp
# Record=grecord
# Shell=xterm -rv
# ScreenSaver=xscreensaver-command -activate
# NewsReader=mozilla -news
# Communities=mozilla -remote 'openURL(http://slashdot.org)'
# Search=mozilla -remote 'openURL(http://google.com)'
# Idea=mozilla -remote 'openURL(http://sourceforge.net)'
# Shopping=mozilla -remote 'openURL(http://thinkgeek.com)'
# Go=mozilla -remote 'openURL(http://linux.com)'
# Print=lpr
# Rotate=

# osd_font=-arphic-ar pl kaitim big5-bold-i-normal--0-250-0-0-c-0-*-*
### For the color, you can either use the strings in /etc/X11/rgb.txt,
### or use the RGB syntax #RRGGBB, e.g. ##A086FF
# osd_color=LawnGreen
# osd_timeout=3
### osd_position is either 'top' or 'bottom'
# osd_position=bottom
# osd_offset=25
```

---

### Post by dolphinsonar on 2006-08-24
> **Jagot said:**
> I have exactly the same laptop.

You need to first enable the universe repo.  See either of these two links:

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then, from Terminal:

```
sudo aptitude update
sudo aptitude install 915resolution
```

The package automatically detects what the correct resolution should be, so all you need to do is restart the xserver - press ctrl+alt+backspace.

YES!  I have the Dell Inspiron B130 as well (AKA dell inspiron1300) and your solution worked perfectly!  Thanks!  

For anyone else with this problem, hang in there.  I used [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) to enable the "universe repository" then typed in the code as was instructed above.  At first I forgot to close the Synaptic Package Manager, and it didn't work because there was a conflict.  After closing it, the commands did the job right!

Learning the command line stuff is why I got into Linux, it is cool to be able to tiker with the inner workings of computers, muhahahaha!!

This is my first experience with Linux, and it is a great one.  Ubuntu is very user friendly and these forums are extremely helpful, the key is to not panic and calmly sift through the problem.  Thanks!

---

### Post by FingerPie on 2006-10-15
On my Dell 1300, I still get the following error... is it a problem?

""
Reading package lists... Done
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718
W: You may want to run apt-get update to correct these problems
""

i wrote a blank sources.list and re-ran aptitude update as suggested, but still get the error when i run it with the modified sources.list.

I got the same error when I activated the repositories from the system menu.

Do I have to worry?

-FP

---

### Post by michelefrost on 2006-11-17
don't worry, just solve it if you haven't yet in these months ;)

The repository you are using has a public key to insert in your local keyring to be recognized as trusted.

just add the key to keyring typing:

```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```

as shown on: [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/)

---

### Post by dakuran on 2007-07-17
would this method still work in feisty?

---

