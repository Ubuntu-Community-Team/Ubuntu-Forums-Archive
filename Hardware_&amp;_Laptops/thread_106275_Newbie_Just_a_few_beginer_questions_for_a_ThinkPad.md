---
title: "Newbie: Just a few beginer questions for a ThinkPad 600"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by shapiror on 2005-12-20
hey guys.  i'm very new to linux, but i figure i'll give it a try.  i have a few questions first though.

1) i've heard a lotabout it being hard to get wifi pcmcia cards to work.  can someone explain to me how i would do this before i go and install ubuntu.  it's my only way to the internet.
2) does anyone have any experience with an ibm thinkpad 600 and ubuntu?  does all the harware automatically install and function correctly?
3) when a new version of ubuntu is released, do i have to doa fresh install?  or willit automatically update my version via the internet?

that's all for now.  thanks forhelping me get started with linux!  i've been waiting to do this for a long time now!

-randy

---

### Post by Lambert on 2005-12-20
[QUOTE=shapiror]
1) i've heard a lotabout it being hard to get wifi pcmcia cards to work.  can someone explain to me how i would do this before i go and install ubuntu.  it's my only way to the internet.[/QUOTE]
What make and model number (including revision #) do you have? This makes a huge difference on what's necessary.

> 2) does anyone have any experience with an ibm thinkpad 600 and ubuntu?  does all the harware automatically install and function correctly?
I briefly had ubuntu installed on a 600e before it went elsewhere and my initial view was everything worked. Each model can be a little different though so there may be some things you have to do. Try a livecd first as it will give you a snapshot of how it will function.

> 3) when a new version of ubuntu is released, do i have to doa fresh install?  or willit automatically update my version via the internet?

No you don't. all you have to do from a command line is sudo apt-get dist-upgrade after changing your source.list so it points to the repos of the new release. There's information about this when time comes. You will find opinions though where it's believed a clean install is still better.

---

### Post by Gurgeh on 2005-12-20
My Thinkpad 600 like ubuntu, few problems:

- I have a belkin wifi card (F5D7010) using the Broadcom chipset, supplied version of ndiswrapper doesn't seem to like (u'll get what I mean when u come to it)
- On board crystal soundcard is a right mare (but works lovely if u get it to work)

And those are the only two problems, everything else works like a dream.

Other than that the laptop really is perfect for it. I'll keep my eye on this post if u decide to go for ubuntu (which u should) I'll get u to where I am.

SIDENOTE: Even if u have the shitiest experience ever u will still enjoy urself. Having that reason to hammer away at ur keyboard for hours, seeing the results of ur labour and really appreciating what ur laptop can do are all part of the linux revolution but... ahem... Oh my god i'm turning into a geek!

---

### Post by shapiror on 2005-12-20
thanks for all the hep guys.  urgeh, i just wanted to say thanks.  it'sgood to know that you all are here to helpif i need it.  and for Lambert, i have a Proxim IEEE 802.11a/b/g ComboCard Model: 8481-WD.  please, i really need to get this card online or it will take a longtime to get windows 98 back on here up and running and back on the internet.  i also have one other question.  how do the function keys work on ubuntu?  do they work okay?

-randy

---

### Post by Gurgeh on 2005-12-22
Yup work fine, they are hardwired into the motherboard and would work even if you were running DOS. BTW I'm gonna wait for Xbuntu to come out before using my laptop properly. Although ubuntu works fine, it still feels a bit heavy sometimes... (nowhere near as heavy as XP tho)

PS: You can download a file called PS2.EXE from IBM and its like a command line driven extended BIOS tool. Allows you to configure pretty much anything. So get ur Win98 disk handy (to use for a boot disk) and whack it on a floppy boot into DOS and hack away.

---

### Post by omnibap on 2005-12-22
Hi, 

since my own TP 600e is running ubuntu breezy, I thought of adding my two cents to this thread

[QUOTE=shapiror]
1) i've heard a lotabout it being hard to get wifi pcmcia cards to work.  can someone explain to me how i would do this before i go and install ubuntu.  it's my only way to the internet.
[/QUOTE]

Some wifi chipsets have better support under linux than others, i have a cheapo card based on realtek rtl8180 chipset. I managed to get it running both with ndiswrapper and with the open source rtl8180 driver but both required some work like downloading stuff and compiling modules. Since you have proxim card native support might work right out of the box.

[QUOTE=shapiror]
2) does anyone have any experience with an ibm thinkpad 600 and ubuntu?  does all the harware automatically install and function correctly?
[/QUOTE]

Most of it works, but you might have to fiddle with stuff like sound and modem.

Sound works but I had to tweak alsa configuration to get it right. It's not that hard just search the forums for the terms "thinkpad", "600",  "alsa", "46xx" and "cs4236" and you'll find posts describing the right way to get it done.

I had the modem working on older linux distros like red hat 7.2 (which used kernel version 2.4) but never managed to get it working on ubuntu. IR is also a mistery, I also had IR working with red hat before but not now.

I also recommend during installation to add the parameters "acpi=off" and "pnpbios=off" to the installation prompt. These will save you some trouble setting up the audio.

Keep in mind that there are differences between the 600 and 600e. Actually, there might be differences even between two 600 with deiferent model numbers.

[QUOTE=shapiror]
3) when a new version of ubuntu is released, do i have to doa fresh install?  or willit automatically update my version via the internet?
[/QUOTE]

I only had the experience of upgrading hoary to breezy, but (as with Windows) I recommend a fresh install, especially if you messed with the default packages on your installation prior to the upgrade. I did an upgrade on a machine and things just didn run as smooth as a fresh install (which I was forced to do later on that machine)


regards,

Omnibap

---

### Post by bsj on 2006-01-01
I've recently come by a 600E as well. $25 :razz: 

Wifi has been horrifying, though. I've got three options: an airlink with an acx 111 chipset, a d-link dwl-g630, or a d-link dwl-122 usb. I would prefer to get one of the pcmcia cards working since the 600E only has one available usb port. Any suggestions as to which I should use? I have tried repeatedly to get the pcmcia cards working, but I haven't necessarily been trying things specific to the TP 600E. 

I've got the acpi=off...

WOOHOO!

I just check my /boot/grub/menu.lst file. This file had somehow been changed. My additions to the kernel line were gone, so acpi was being used on boot. I included the above, used houseofcraig's ./start_net script, and here I is! I'm using the airlink pcmcia card. 

Lesson learned. No acpi with the Thinkpad 600E!

---

### Post by Jackal82 on 2006-02-03
[QUOTE=bsj]
WOOHOO!

I just check my /boot/grub/menu.lst file. This file had somehow been changed. My additions to the kernel line were gone, so acpi was being used on boot. I included the above, used houseofcraig's ./start_net script, and here I is! I'm using the airlink pcmcia card. 

Lesson learned. No acpi with the Thinkpad 600E![/QUOTE]

Hi!

Maybe a stupid question but what is houseofcraig's ./start_net script?

---

### Post by Audiophiliac on 2006-04-04
Can't install my IBM 380z's sound card. It should use cs4232. BUt device can't be found on doing modprobe. How do I mess with irqs? i can't see where to change these in my Bios. I was also advised to disable the parallel port which is on irq=7. Can't find that either.

Any way I can do the acpi=off and pnpbios=off having already done the installation (Ubuntu 5.04).

At the moment I have pcmcia modem and lan working. I have no sound and pcmcia wifi. Wifi lights up on modprobe ndiswrapper. But still can't be detected.

---

