---
title: "What's working and what's not after upgrading to Hoary"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by wolrahnaes on 2005-04-09
I just upgraded my laptop from Warty to Hoary, since I was bored and had just noticed the Slashdot article.

It's working smoother than the last install, but that's partially because I had changed so many things that I just decided formatting and reinstalling was the better idea.

The important stuff is working, but I need help getting the rest going so I can have a completely enjoyable experience.  I'll list off what still isn't working, if it worked before in Warty, and any other relevant information.

_**ALPS Touchpad**_
**Current Status:** Semi-Functional
**Status in Warty:** Same
**Details:** The touchpad itself works fine, and properly switches on and off with the button, but the extra features like the scroll area do not work.  A minor nuisance, but very annoying at times.

_**ATI 3D Graphics**_
**Current Status:** Non-functional
**Status in Warty:** Worked fine
**Details:** Installed the xorg-fglrx package from Synaptic, rebooted, fglrxinfo still shows Mesa.  xorg.conf shows driver line of "ati".  Should be an easy fix, just not sure of the exact details.

_**Broadcom 802.11b/g**_
**Current Status:** Non-functional
**Status in Warty:** Semi-Functional
**Details:** I haven't yet installed ndiswrapper, so I don't expect this to work yet, but previously even with ndiswrapper I had to manually set the SSID of the target network, and I still could not log on to networks using LEAP (such as my school's)

_**Audio**_
**Current Status:** Barely Functional
**Status in Warty:** Same
**Details:** Startup sound plays at gdm, Intro plays while GNOME loads, from there it's a crapshoot.  Most sounds do not play, those that do are usually horribly distorted.  Only exception has been MP3 playback with Totem, works flawlessly.  VLC is doesn't output anything, though it claims it's playing.  XMMS just crashes and burns.

Volume Control shows two separate audio devices.  Analog Devices 1981B on OSS and ATI IXP150 on ALSA.  AD1981 appears to be the one that is playing, albeit badly.  IXP150 volume controls map correctly to the board (Master controls built-in speakers, Headphone controls headphone jack, and Mic works), whereas ADI1981 PCM1 controls master volume and PCM2 controls headphone relative to master.  No way to turn off the speakers and just use headphones, which makes this nearly unusable.  I would prefer to get the ATI IXP working and drop the ADI setup due to the volume situation.

_**Multimedia Keys**_
**Current Status:** Semi-functional
**Status in Warty:** Same
**Details:** My keyboard has alternate functions on Fn+<F3-F12>, of these only the display brightness control works.  The media player, sleep, lock workstation, web browser, and external monitor keys do not work, nor do the volume and mute buttons along the side of the case.

_**Flash Card Reader**_
**Current Status:** Non-functional
**Status in Warty:** Same
**Details:** I have a TI CardBus-based reader built in to the side of this laptop.  It reads SD, MMC, SM, MS, and MS Pro.  None function at all.

_**Extra Buttons on Mouse**_
**Current Status:** Non-functional
**Status in Warty:** Same
**Details:** Logitech MX510.  The primary 3, the wheel, and the scroll buttons all work fine.  The 3 other buttons (switch application, back, and forward in Windows) do not.  Back and forward are a must, as that has become a habit for me.

_**Second Monitor**_
**Current Status:** Not working
**Status in Warty:** N/A
**Details:** I didn't have it when I was using Hoary, but now I have a second monitor that I use to display live data from my server.  I would like to make it work in Linux as well.  Maybe this will fix itself as a side effect of getting fglrx working, I'm not sure.

_**HP LaserJet 4 Plus**_
**Current Status:** Semi-functional
**Status in Warty:** Worked fine
**Details:** This printer is a known good, it worked fine in Warty, as well as Mandrake and Fedora before it, works fine on my Windows box, and even works nicely from Mac OS 9 and X.  For some reason, Hoary insists on sending it A4 instead of US Letter, even though I have Letter selected everywhere.  When I click Print Test Page, soon after I get the familiar message on my screen "PC LOAD A4" meaning that my request to do letter was ignored.

_**HP PSC2175 Scanner**_
**Current Status:** Non-functional
**Status in Warty:** N/A
**Details:** Just got this, from what I read on linuxprinting.org it's perfectly supported.  Printing works fine with no configuration other than telling she system what printer I had and that it was on USB, but Xsane says no devices found.

Any help that anyone can offer on any of these issues would be greatly appreciated, but the sound, 3D, and mouse are the three highest priority right now.  I will post any config files if you need them to provide assistance.

Thanks
-Sean

---

### Post by dusu on 2005-04-09
Hi,

I'm not sure about this, but for what concerns xmms, did you make sure you use the proper audio output ? 
When using Gnome, you should set the preferences in xmms so as to use the ESD audio.
Another way is to use Alsa, but then you should modify the sound settings in Gnome, and tune them so that the sound server is not started when Gnome is launched.
This is what I decided to do, since I use Gnome, XFCE and Blackbox, and Gnome is the only one that uses ESD...

---

### Post by wolrahnaes on 2005-04-09
Well the sound issues seem to be GNOME related, since I installed the Kubuntu package, reloaded in to KDE, and everything works fine.  The ATI IXP is selected by default and I can independently control the volume levels of the internal speakers and headphones (though turning off the internal speakers when headphones are plugged in would be nice).

I also added a few printer problems that I had forgotten to put in the post originally.

---

### Post by zoso on 2005-04-10
> ATI 3D Graphics
Current Status: Non-functional
Status in Warty: Worked fine
Details: Installed the xorg-fglrx package from Synaptic, rebooted, fglrxinfo still shows Mesa. xorg.conf shows driver line of "ati". Should be an easy fix, just not sure of the exact details.

I followed the instruction found in [this thread](http://ubuntuforums.org/showthread.php?t=24557) to get 3D acceleration woking for ATI cards, but have not had any success. Running fglrxinfo still returns 'Mesa GLX'. I'm not sure what's going on here. Anyone have any insight?

Oh yeah, and it's nice to see that sound is working out of the box (for me at least) now. I tried with Warty and didn't have any luck. Now if we could just get 3D acceleration working I'd be a happy camper all around.

---

### Post by jonny on 2005-04-10
Try this [How To](http://ubuntuforums.org/showthread.php?p=125537#post125537) for the wireless card

---

### Post by RastaMahata on 2005-04-10
Interesting kind of post. I'll go with my experience from the upgrade.

Nvidia GeForce4 mx 440: Non functional
After the upgrade I just couldnt make it into X. I had to sudo dpkg-reconfigure xserver-xorg and switch to nvidia to create a clean xorg.conf file. Then I had to remove every nvidia* package from my system, then I had to install them again, do a nvidia-glx-config enable, and only after that change from nv to nvidia. Way to go for an easy setup. I just cant see my mom/syster/gf doing this.

Nforce2 ac97 sound: Semi functional
Yeah, way to go for a simple sound configuration. After setting everything to esd (thus getting audio delays in videos), I decided i couldnt work like this. So I had to google (a lot) to get decent alsa configuration. Setting everything to alsa fixed the delays, but I had to play one sound at a time, and disable the gnome sound server (esd). Then, in my google search, i was able to found a working .asounrc, place it in my home dir, and reboot gnome (besides installing some weird packages). Then i had to edit some file to let gaim use my new configuration (use alsa instead of software). And playing games is another story, configuring each one to use alsa (and they dont allow me to use dmix). Way to go.

Cd-burning (Samsung CDRW/DVD SM-308B): Just weird
Gnomebaker just crashed the first 5 times I tried to burn a cd. Even now, it pops up a message saying that it couldnt mount (or umount, i dont remember now) /media/cdrom0. In the 6 try, It burned my cd succesfully, but it still gave me the message. I dont know whats wrong. :(

Additional HardDrives (ntfs, vfat partitions):
Again, warty was able to show my hard drives in my Computer:/// folder, but hoary isnt. I have to "sudo /etc/init.d/dbus-1 restart" each time i get into X to be able to see my drives in Computer:/// and my places menu (but doing this takes away the names of the floppy and cdrom drive, turning into diskette1 and cdrom0). After a bit of configuring my /etc/fstab, I was able to show my harddrives in my Computer:// folder (by adding "auto,user,exec," before the umask), but they still dont show up on my places menu.

I hope that's all the trouble I will get. :(

---

### Post by TheRealEdwin on 2005-04-10
I did a similar post but not as detailed. [Link](http://ubuntuforums.org/showthread.php?t=25665)

---

### Post by wolrahnaes on 2005-04-11
Got wireless working, just as simple as it was on Warty.  Downloaded latest source release, compiled, installed driver from ounted NTFS partition, and modprobed.

I did notice something when testing it though...

When I unplug my wired LAN connection, I get the "!" icon on the GNOME panel, but everything continues trying to use that connection, and I have to manually ifdown it before anything tries to use wireless, then I have to ifup when I plug it back in.

---

