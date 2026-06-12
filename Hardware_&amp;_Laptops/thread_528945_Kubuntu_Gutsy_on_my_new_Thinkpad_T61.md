---
title: "Kubuntu Gutsy on my new Thinkpad T61"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by czheng on 2007-08-18
Hi all,

Have had my new Thinkpad T61 for about a week now, and things are going relatively well. There are wiki pages and such summarizing other people's experiences with this, but I thought I'd add my own two cents. This is not intended to be comprehensive, and just reflects what my biggest needs and concerns were. I started by trying Kubuntu Gutsy Tribe 4, then switched to openSUSE 10.3 beta, and then went back to Kubuntu.

INSTALL
In order to install, I had to go into the BIOS and change the SATA mode to compatibility in order to get rid of [this error]("http://ubuntuforums.org/showthread.php?t=469057").

RESOLUTION
(I have the WXGA+ 14.1" 1440x900) The resolution was detected out of the box when I first started up, which is a big relief. I used to have to use 855resolution on my old Feisty laptop. During the boot process, though, it doesn't seem to kick in until X is started. Before that, the booting screens are all in a lower res. **EDIT: Actually, the resolution doesn't work. The system *says* it's 1440x900, but comparing side-by-side with my girlfriend's 1280x800 laptop, the resolutions are identical.**

The system doesn't detect the actual hardware as well as openSUSE's 10.3 beta did. openSUSE, for instance, got all the names and drivers right (Lenovo laptop LCD, Intel 965, etc.) where Kubuntu uses generic 'intel' driver and 'custom' monitor. But there isn't much discernible difference as far as results. If any, it's that the screen and graphics are MUCH more crisp during the boot process on openSUSE.

FONTS
There seems to be a slight problem with font size. All of my fonts appear to be about 2 or 3pts larger than they are set to be. I've tried forcing DPI in Kcontrol, but to no avail. Probably [this bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/118745"). I also tried forcing the DPI in my xorg.conf as detailed [here]("http://www.kde-forum.org/artikel/16669/Plz-assist-how-to-set-a-screen-resolution-of-107-d.html"), but that didn't do anything either.

INTERNET
I have the Intel 4965 A/G/N card. Before any configuration, Kubuntu recognized both my wired and wireless devices. Connecting with either device works out-of-the-box. The only issue I've come across is this: using the wireless connection, I can connect to a wireless G network and access the internet with no problems. On my home network (a Belkin N1 router, or a wireless N network), I can connect to the network without issue, but the device stops receiving data almost immediately. Sometimes I can load a single page or two before it stops. 

I'm not sure what the problem is, and not sure how to test it further, but for now it doesn't work. I'm guessing it has something to do with the device trying to use its N mode instead of its G mode and freezing up. It's probably a iwlwifi driver problem and not an Ubuntu issue at all, but I did file a bug in launchpad.

Also, the little wireless LED doesn't light up at all.

WEBCAM
Built-in webcam is not detected, and I don't know how to get it installed or working.

SPECIAL KEYS
Volume keys don't work. Brightness adjusters (Fn+Home and Fn+End) don't work. The little thinkpad light (Fn+PgUp) works though. The front and back keys near the directional keys work fine too. Haven't tried any others. 

TOUCHPAD and that other little red thing
Both work out-of-the-box. Touchpad also has scrolling along right and bottom sides. Sometimes can be a bit too sensitive but I'm sure that's configurable.

SOUND
Didn't work at all until I did [this]("http://skinetwork.org/mediawiki/index.php/Fedora-T61#Sound"), except instead of editing /etc/modprobe.conf (which doesn't exist on my system), I added the relevant line to the end of /etc/modprobe.d/alsa-base.

So that's where I'm at right now. If there's any progress, I'll post it here. If anyone has suggestions for the few remaining issues, or questions about anything, I'd be happy to hear them.

---

