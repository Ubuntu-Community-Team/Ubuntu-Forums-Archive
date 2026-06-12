---
title: "SONY Vaio VGN-N31S and Ubuntu 7.04 Fiesty Fawn all works (plus issues encountered)"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by JeffDaviesAtAber on 2007-09-05
SONY Vaio VGN-N31S and Ubuntu 7.04 Fiesty Fawn all works (plus issues encountered)
====================================================
Ubuntu 7.04 is amazing. The best OS I've ever used. Vista on the same Core Duo still has a sluggishness that's there even after I've turned off all effects and reverted to XP interface.
(yes I have 1 gig of RAM).
By comparison, Ubuntu with Beryl is drop dead gorgeous and lightening fast. All credit to the Ubuntu team.
I'm sharing my experiences in an attempt to feed back to the community.

Dual boot install went smoothly and uneventfully, partitions took a while to resize, but they did resize, and everything works fine afterwards.

What works out of the box is (I didn't have to select anything beyond keyboard type as far as I remember):
1. Sound, 3d Graphics, the large screen, Core Duo processor, WiFi card, Ethernet.
I think I've tried USB and the the DVD, but I can't remember (I have no need to use these).

2. What didn't work was Security on Wifi: I just had to modify a file to put my WiFi key in a slightly different place.
I used to have an unsecured WiFi, but my service provider gave me a new hub (BT HomeHub).
Because the WiFi driver is an AtheOS WiFi driver, it seems like the system puts the Key in the wrong place (ath0), so just amend the config file, and put it in the right place (wifi0)  (I copied and pasted, so in mine it's in both places - doesn't seem to matter): 
SEE BOTTOM OF POST FOR FULL CONTENTS OF FILE

Change it and reboot. You don't need to reboot, but it's so fast you might as well.

3. Another thing that doesn't work is hibernate, but boot is so fast, this is a bit pointless in any case. Beryl is great. OpenArena (QuakeIII OpenGL) runs really well on this hardware.

I also turned off mouse gestures (because I hate them), by setting MaxTapTime in the
/etc/X11/xorg.conf file as below:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
 	Option 		"MaxTapTime"		"0"
EndSection

(see the MaxTapTime line above)

Change it and reboot. You don't need to reboot, but it's so fast you might as well.
--------------------------------------------------------------------------------------------------
[/etc/network]
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid BTHomeHub-73CD
wireless-key e76c72f07e


auto wlan0
iface wlan0 inet dhcp
wireless-essid BTHomeHub-73CD
wireless-key e76c72f07e

:)
--------------------------------------------------------------------------------

---

### Post by victor9098 on 2007-09-06
Hi JeffDaviesAtAber,

That was a great post. I have just picked up the exact same laptop, just about to install Ubuntu. I do not plan to dual-boot so will just be letting ubuntu do a standard install.

Everything should work without any tweaks then? I intend to use WiFi "hotspots" when in university, should I make the changes you mentioned or is this not an issue in my case? Please make sure you update, will be very interesting to hear how different users on the same hardware get on.

Best regards.

---

### Post by JeffDaviesAtAber on 2007-09-06
If the wifi is encrypted, I think you just have to edit that file. There is a proper windowy way to do this, but it seems to get messed up because the Ubuntu driver for this Wifi is from another operating system called AtheOS, with a plugin compatability layer, and I think the window code is expecting a slightly different interface name (wifi0 not ath0 ...  or something like that).

Anyway, if you get any issues, post here, but also email me at jeffd AT aberinstruments.com.
I'll come back to this site, and post responses on this site (and email you to tell them when they're done).

---

### Post by victor9098 on 2007-09-06
Guess I will not know what the situation is with the networks security for another week or so. Will keep your post to hand though. If there are any issues will just change the name of that file above.

I am going through the update process at the moment so will be a while before this is finished. Then to get the look and feel how I like it. Probably be a while before I start tripping over any problems, but yes, everything seems to work straight out of the box!

Just a shame they have to ruin the look of the laptop with that nasty "windows vista" sticker!

Look forward to further updates.

---

### Post by wieman01 on 2007-09-07
While we talk about network security, don't use WEP. It is not secure and can be compromised in less than 30 minutes (see signature).

Apart from this, Ubuntu on Sony laptops is a pleasant experience, I can confirm that.

---

### Post by victor9098 on 2007-09-10
Quick Update,

I have replaced Beryl with Compiz-Fusion, using the guides here in the forums. Works perfect, looks amazing. I am guessing Gutsy will have a 'stable' release as standard and just update this when the time comes.

Issues with Hibernation...The Sony will not wake up! Yes, simply turning the machine off takes seconds as does boot up so that is not really a major problem.

Have yet to try out WiFi, so no update there.

Silly question, when I got my first Vaio I remember there being an update for the BIOS every now and then from Sony. Is that something I need to worry about or is it not an issue with Ubuntu? Excuse my ignorance, I do not even understand fully what the BIOS does, I just remember having to update...but that was under win-doh's! 

Everything else seems perfect! No issues. Would really recommend this laptop for anyone wanting a worry free Ubuntu installation.

---

### Post by wieman01 on 2007-09-11
> **victor9098 said:**
> Quick Update,

I have replaced Beryl with Compiz-Fusion, using the guides here in the forums. Works perfect, looks amazing. I am guessing Gutsy will have a 'stable' release as standard and just update this when the time comes.

Issues with Hibernation...The Sony will not wake up! Yes, simply turning the machine off takes seconds as does boot up so that is not really a major problem.

Have yet to try out WiFi, so no update there.

Silly question, when I got my first Vaio I remember there being an update for the BIOS every now and then from Sony. Is that something I need to worry about or is it not an issue with Ubuntu? Excuse my ignorance, I do not even understand fully what the BIOS does, I just remember having to update...but that was under win-doh's! 

Everything else seems perfect! No issues. Would really recommend this laptop for anyone wanting a worry free Ubuntu installation.
I have never had to update the BIOS with Ubuntu. Guess you don't have to worry about that.

---

### Post by victor9098 on 2007-09-16
Hello Again,

Quick question, probably a simple answer but I am not figuring  it out.

When I plug in my headphones I still get sound from the speakers...which kinda defeats the purpose. This never happened on my previous machine and I am not aware of any software changes so maybe there is a box I am not ticking somewhere?

Any help would be great, thank you.

---

