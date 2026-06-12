---
title: "How really good is AMD fusion (E-450)?"
date: 2012-06-10
forum: Hardware
---

### Post by tuxerman on 2012-06-10
Alright, I am banking on the huge community of helpful souls out here to finally help me decide. 

How good is the AMD E-450 APU at everyday performance, and as a portable primary laptop? I am getting a rather nice deal here from an online shopping site (flipkart.com), and the notebook (although it's more of a cross between a netbook and an ultrabook) is the 13.3" Asus U32U. 
[Website]("http://www.asus.com/Notebooks/Superior_Mobility/U32U/#specifications")

AMD E450 APU
AMD 6320 GPU as part of the processor
2GB RAM (Am going in for an upgrade anyway)
Regular 2.5" HDD

An impressive 9-10 hours of battery life and the light weight (no optical drive) and rather neat looks too, is what is drawing me towards buying this. I am leaving home for a software engineering job, and will be away from my desktop for most part of the year. This is going to be my primary computer for a while now.

I can get a regular (but heavier and bulkier and less lasting in terms of battery) 2ndGen-i3 based laptop for a little above this price, and hence I'm wondering if the E450 would be enough for most of my needs.

Moderate to heavy web browsing, movie-watching, coding, tinkering, casual photoshop (and relatively [heavier?] stuff like some processing  in MATLAB, development on Visual Studio, etc when the office wants it) - has anyone had any issues with these with an AMD E450?

The portability and battery life are really enticing as far as the Asus notebook is concerned. However I'm wondering if the occasional audio-video encoding, experiments with MATLAB, teaching myself computer-science and algorithms, tinkering with the kernel, etc would bring it down to its knees. 

I'd be really glad if anyone could throw some light on this.

PS: Plan to build up the OS from a base xubuntu install.

---

### Post by Redblade20XX on 2012-06-10
Get something with a little more power. I do some coding and Matlab on my e-450 but there is "noticeable" lag. Most likely you'll have to have an AC power connection to get any performance for any real processing which defeats the mobility aspect.

-Red

---

### Post by moteprime on 2012-06-11
I have an Ideapad s205 with a E-450 in it (4Gb ram).
For everyday use, browsing, mail and so on it performs well, it's not lightning fast but it covers my needs nicely. 
I have an homebuild PC from august 07 with a AMD Athlon64 X2 5000+, 3Gb RAM, Asus M2N-SLI/Deluxe and a Geforce 8400GS. The two machines performs about the same. They both have Ubuntu 12.04.

---

### Post by tuxerman on 2012-06-11
How about the i3 ULV? The HP DM1 series 11.6 incher offers both AMD E450 as well as 2nd generation Core i3 (ULV) 2367M.

If the latter were significantly better than the AMD fusion platform in terms of processing power, it would be an awesome buy.

---

### Post by Redblade20XX on 2012-06-11
> **tuxerman said:**
> How about the i3 ULV? The HP DM1 series 11.6 incher offers both AMD E450 as well as 2nd generation Core i3 (ULV) 2367M.

If the latter were significantly better than the AMD fusion platform in terms of processing power, it would be an awesome buy.

I would avoid buying an HP for linux use. They use encrypted signed BIOs to lock people out of advance settings in which some are needed for linux usability. Look at Asus or MSI.

-Red

---

### Post by tuxerman on 2012-06-11
> **Redblade20XX said:**
> I would avoid buying an HP for linux use. They use encrypted signed BIOs to lock people out of advance settings in which some are needed for linux usability. Look at Asus or MSI.

-Red

Could you elaborate on that please?

---

### Post by Redblade20XX on 2012-06-11
HP manufactures a family of there computers with a general motherboard (cost saving strategy). As you should know, different models in the same family have different hardware. In order to control the selling of the family, they use encrypted signed RSA BIOS (from what I've seen, I'm a BIOS modder) to unlock certain features for different models in the family.

I've had a dm1 and the model came with only stock hdd while another high end model had ssd. I've recently bought an ssd to put into my dm1 but the controller for disks on the mother board was set to IDE (bad for ssd) instead of ahci (good for ssd). I couldn't change this in the BIOs because there was no advance menu. Upon looking into the BIOs there was an advance menu but future BIOs updates locked that feature thus making me unable to use the sdd more efficiently. Couldn't mod the BIOS to unlock the menu and change the setting because it was encrypted and RSA signed and would semi-brick. :(

-Red

---

### Post by tuxerman on 2012-06-12
I see. Thanks a lot for the info. Do RAM upgrades offend the BIOS?

---

### Post by ubik89 on 2012-06-19
Somebody can play 1080p HD videos with amd fusion e-450 and radeon hd 6320?

---

### Post by DrEameR86 on 2012-06-19
Using VLC, both stable and nighlty are able to play 1080p but not as smooth as I would like to. Without GPU acceleration it's impossible of course. With it, it stills eats around 80% of the CPU, wich I consider quite weird. You get a playable video although a bit choppy in fast scenes (actually I don't think you ever get full framerate). 

VLC, ATI Catalyst stable, Ubuntu 12.04.

I could not make it work with mplayer2 or totem.

---

### Post by upnix on 2012-06-21
I have an E-350 inside a Lenovo Thinkpad x120e.

I think it's a fantastic little machine. I have it hooked up to a 22" monitor at 1920x1080 using an HDMI cable. I can do full screen 1080p in VLC 2.0 no problem. Battery life is around 6.5 hours on the 6-cell battery.

I use it for general web browsing, DVD transcoding and ... just general kicking around I guess.

One complaint I'd make is that it doesn't do any hardware encryption. So copying from my encrypted hard drive to an encrypted USB drive is slow. Firefox GUI is a little slow too, but with Chrome things feel as fast as my 2.something GHz Core 2.

In general though, it's "slow" in the right way. Video and UI are speedy, it's things like opening LibreOffice, or video encoding that's slow. If I were to move to an SSD drive, I think things would be better still.

Using Ubuntu 12.04 with Unity and Catalyst drivers.

---

