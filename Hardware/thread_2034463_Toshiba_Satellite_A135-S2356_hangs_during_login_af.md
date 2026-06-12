---
title: "Toshiba Satellite A135-S2356 hangs during login after install"
date: 2012-07-28
forum: Hardware
---

### Post by TrombaMarina on 2012-07-28
I have a Toshiba Satellite A135-S2356 and had to use both acpi=off and noapic in order to boot a Live CD thanks to this thread:
[http://ubuntuforums.org/showthread.php?t=1504267&highlight=Toshiba+Satellite+A135](http://ubuntuforums.org/showthread.php?t=1504267&highlight=Toshiba+Satellite+A135)
But when I installed Ubuntu 12.04 32-bit* it would hang about 5 seconds after booting to the graphical login screen.  Sometimes I could type my password fast enough to see it start building the desktop before it hangs and sometimes it hangs before I can type.  The mouse moves and keys work during those 5 seconds.  The same thing happens with Xubuntu.  I've installed a number of times now, with and without home folder encryption, updates from web, and restricted extras.  I didn't see anything useful in the logs.  My guess is that it has to do with the graphics card driver because I was able to log in at the command prompt as follows:

The following was successful:
 - Plug in network cable

 - Hold the shift key while booting to get boot menu

 - Select recovery option and edit boot options, put the word "Single" after "root=/dev/sda1 ro" and delete rest of line as described (sort of) here:
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

 - CTRL-ALT-F1 after booting to get command prompt

Then I tried to sort of follow this, but failed with "aticonfig: no supported adapters detected".  Also, there isn't any /etc/X11/xorg.conf any more (that's why I tried installing Xubuntu), so I really don't know what I'm doing:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

I don't see anything informative in any log files.  Any help would be appreciated.

Notes:
* The Atheros AR242x / AR542x Wireless Network Adapter in this laptop works out of the box with 32-bit Ubuntu 12.04, but might not have a driver at all for 64-bit (as of 2012-07-27). The rest of the system seems to work fine with 64-bit, but since it can't support more than 2GB memory, 32-bit is probably more appropriate anyway.

---

### Post by sid0972 on 2012-07-28
your system is a little old, and it scrapes the minimum requirement
to just be sure, try booting into graphic fail safe mode
(GRUB menu- recovery mode - graphic failsafe mode)

if it runs fine there, then its easy
in accord with this line
 "aticonfig: no supported adapters detected".
just install the drivers, since you have integrated ATI, and see what happens

---

### Post by TrombaMarina on 2012-07-28
Thanks for such a quick response!  When I boot to recovery mode (clean xubuntu 12.04 install) without forcing single-user mode, the system hangs before it even gets to the login screen (see attached).

I tried to manually install the ATI drivers, but when they still didn't work, I googled the error message and based on my reading, I tried to uninstall them.

---

### Post by sid0972 on 2012-07-28
have you installed the proprietary drivers?

dash-additional drivers- first install the recommended one
then the post release if you like

report back the results

---

### Post by TrombaMarina on 2012-07-28
Hmm...  I don't think this is a video problem any more.  I'm posting a picture of it hung, 5+ seconds after displaying the login screen.  Then a second shot of when I was able to hit CTRL-ALT-F1 to get to a command prompt login and it hung just the same before I could finish entering my name.

Why would the live CD work perfectly (with acpi=off and noapic) but the install not work?

Not sure if any of this is relevant, but Toshiba support pointed me here:
[http://linux.toshiba-dme.co.jp/linux/eng/pc/memo2/satA135.htm](http://linux.toshiba-dme.co.jp/linux/eng/pc/memo2/satA135.htm)

---

### Post by sid0972 on 2012-07-29
i had the same issue, LIVE CD rarely hung (but it did, although very rarely)
when installing on my HDD, it would hang almost every time, although sometimes i was able to install it

in my case it was bad motherboard, and i couldn't install windows either
can you try and see if you can install windows?

cause if you cannot, then its definitely a hardware issue,

---

### Post by TrombaMarina on 2012-07-29
Hmm...  At your suggestion I took out my new 128GB SSD drive and put the original conventional magnetic disk hard drive back in and Vista booted up just as well as it ever did.  I wonder if my drive is the issue, or the motherboard maybe can't handle it somehow?  Clearly it works long enough to boot to the login screen.  It also works if I spend several minutes messing around at the GRUB boot options.  No, I think it is something the OS tries to do just after it presents me with the login prompt.  Maybe it's initializing the network card?  That would explain my first attachment...

Sid0972: What does "dash-additional drivers" mean?  I have tried installing and uninstalling ubuntu-restricted-extras and as far as I can tell, Ubuntu installs the ATI driver by default, which I then tried to uninstall.

Interestingly, with Xubuntu without restricted extras, I can't seem to boot to a command prompt at all.

---

### Post by sid0972 on 2012-07-29
dash- additional drivers mean go to dash, type additional drivers
i think, since the issue is very common, 12.04 does support turbo technology, but improperly

---

### Post by TrombaMarina on 2012-07-29
Thanks for hanging in there with me.  So I looked it up and Dash is the new search box thingy in the upper-left corner of Unity?  How do I get to that if the system hangs before I can even log in?

---

### Post by sid0972 on 2012-07-29
yes, that is dash, and i dont have an answer for that question of your's
you say LIVE CD works fine?
then might be an HDD issue.
can you try and change some settings in the BIOS, just to be sure?
try disable/enable for some HDD settings!
i know this is far fetched but, just a thought

---

### Post by TrombaMarina on 2012-08-27
Thanks Sid and others.  There are no hard drive settings in the bios whatsoever.  Out of frustration, I gave it a rest for a few weeks, then started in again today.  I had the idea that the SSD was bigger than the original drive, so I could reformat the primary partition to be the same size or smaller.  Then it hung twice while booting up from the CD-ROM today.  Summary:

 - Consistent hang from installed Ubuntu 12.04 within about 10 seconds of booting.  Was able to work-around one time, booting to single-user text mode.

 - Occasional hang when booting from CD-ROM.  This may be due to not powering off the system long enough before trying again.  Don't know.

 - This laptop has a beautiful screen, but pretty much everything else is the pits.  The keyboard is a touch-typing nightmare for anyone who uses the Ctrl and Alt keys (me).

All in all, this has been an extremely frustrating experience.  The ultimate payoff - a slow, possibly unreliable laptop with an annoying keyboard, 2GB memory, and a battery recall - is not worth the effort and money I have already put into it.

I'm officially giving up.  Thank you everyone for your help.  I would have to suggest that others stay away from this make and model.  In prime condition with a working OS, it is probably worth $100 (eBay backs me up on this).  The most gratifying part of this whole project was that I learned a new word while searching for answers about this beast: Craptop.

---

### Post by sid0972 on 2012-08-28
i like that term: Craptop
i personally prefer desktops over laptops, but then, i am a gamer at heart, and i like big screens and powerful gpu's.

sorry to hear that the problem couldnt be solved,

---

