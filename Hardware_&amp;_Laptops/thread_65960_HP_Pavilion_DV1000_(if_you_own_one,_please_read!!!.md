---
title: "HP Pavilion DV1000 (if you own one, please read!!!)"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2005-09-15
Hello,

     First of all how does Hoary run on this thing. Is there anything special that needs to be done besides noapic as a kernel option?

Second, I have a whole bunch of questions about the NEW dv1000's (they come with the intel 915 chipset and Intel Graphic Media Accelerater integrated video ... it seems most of the specs/reviews on the internet are for the older one with the 855 chipset... I wonder why HP put in a newer chipset and didn't change the model number, DV2000 anyone?):

- Is the hard drive ATA-6, ATA-7, or SATA?
- Is the memory DDR333 or DDR400 and is a 200-pin DDR400 SODIMM backwards compatible with DDR333 (I'm buying a 1GB stick aftermarket because its a LOT cheaper than what HP charges)?

I ask these questions here because HP doesn't know. They told me to bet on it being SATA because that is what the *majority* of their laptops are. I don't know about you but I'm not betting on spending $2600 to get two of these just to find out my bet was wrong  :roll:  Secondly, the customer service rep just couldn't tell me what the memory was and the technical support guy wanted a model number or he couldn't help me... hence I have to gamble on this too to find out.

So if you own one, please help me out.. thanks :)

---

### Post by vtec on 2005-09-15
Well.... I can help you a little. I have the compaq v2000. It is the same as the dv1000 except it doesn't have the quickplay dvd stuff. It is based on the 855 chipset. Mine is based on the 2200 chipset for wireless and has BT. I havn't used the BT yet but every thing else works out of the box except for the memory card reader. My understanding is it does not have linux drivers yet. Battery life is great (scales cpu with out issue), and it can suspend to ram and disk without issue. the v2000 has ddr333 ram. This may have been stepped up in the HP line to ddr400 but i'm not sure. Overall i'm very happy with this laptop.

---

### Post by audax321 on 2005-09-16
Well, not too many replies. Thanks vtec. I ended up ordering both of them because I heard such good things about them running Ubuntu and because they have some good offers on it right now ($50 rebate, free printer, free BrightView upgrade, and free extra battery - I got two 12 cells on one and two 6 cells on the other since I heard the 12 cell raises the laptop up a little I'll just use it as a backup).

Anyway, I read about it and it should have the Intel 915GM chipset which I believe includes the following:

- Intel Media Graphics Accelerator 900
- SATA
- DDR 333/400
- 533 MHz Front-Side Bus

Since the chipset can vary a little from manufacturer to manufacturer, I'll post what I get sent when they arrive if anyone else needs info on this. It looks like a really nice machine and should be more portable than my Inspiron 9300 which is going to get donated to my sister :) - it was my first laptop purchase and I didn't realize how HUGE a 17" screen is, good thing my sister is in the market for a desktop replacement right now...

Now I only wish that Linux had something like Microsoft OneNote so I could ditch Windows completely and switch over to OpenOffice.org 2.0.  Does something like this exist???

---

### Post by audax321 on 2005-10-02
Okay, I've been using the DV1000 for a few days now and it works perfectly under Breezy. The hard drive is not SATA and the memory is DDR333. I think the only thing that HP changed was to add the new chipset. Everything else is the same. This has to be one of the best laptops I've used and would definitely recommend it if anyone is looking to buy one anytime soon. :)

One thing I really like is that the remote controls buttons register as standard button codes in xev. That means I don't have to run any utility to get the remote control buttons working except for xbindkeys.

---

### Post by RastaMahata on 2005-10-02
[QUOTE=audax321]One thing I really like is that the remote controls buttons register as standard button codes in xev. That means I don't have to run any utility to get the remote control buttons working except for xbindkeys.[/QUOTE]
Hi. I have a dv1325la (I think it qualifies to be a dv1000). I'm looking forward to install ubuntu on this laptop, but I'll wait until breezy gets an official release.
What do you mean about the xbindkeys?
Is 3d acceleration working out of the box?
Does acpi work ok?
Is there anything I should be afraid of?:(

---

### Post by audax321 on 2005-10-02
ACPI doesn't seem to be working. If the laptop goes into suspend it won't come back out very cleanly and usually ends up rebooting or shutting down. I don't really care about this since I never use suspend anyway. 3D acceleration should working as well (but I haven't tried it yet).  The only thing I'm confused about is that the laptop has the Intel GMA900 video card but it gets detected as i810 by xorg.  Maybe xorg doesn't support the GMA900 yet or this is the correct driver... not sure...

Anyway, everything was setup and working properly... the wireless card (2200 b/g) worked out of the box. I haven't tried bluetooth though because I don't have any bluetooth devices but it seems to be detected. The only thing you have to setup are the media button on the laptop and the remote. For example, the laptop and remote both have a button with a musical note on them. If you open up a console and type 'xev' and then push either of these buttons, both come up with a keycode of 188. To use these you can install xbindkeys (available in the breezy universe and multiverse...also available for hoary in the repos). To configure xbindkeys just make a .xbindkeysrc file in your home folder and add the following:

```

"amarok"
  m:0x10 + c:188

```

This will launch amarok whenever the key is pressed. (BTW, I'm using Kubuntu Breezy, since I started liking KDE again :) ... watch me change back to Gnome in like six months and then back to KDE, then back to Gnome....). In Gnome, you would probably change "amarok" to "rhythmbox".

You can also map these keys to other keys, but requires you to install xvkbd (also available in the repos). For example,

```

"xvkbd -xsendevent -text "\[Control]\[c]"" 
  m:0x10 + c:188

```

would send Cntrl+C (copy) to whatever window is active when I press the musical note button. Of course this would be kind of retarded because it makes a music button copy, but it illustrates the point. :)

---

### Post by numberexhaust on 2005-10-03
Also looking into getting this laptop.  I've narrowed my choices down to this and a Thinkpad t43p.  Does the quickplay cd/dvd stuff interfere with any of the bootloader's operations or anything like that?  I've heard that some mainstream computers come with recovery partitions or w/e (I have an HP desktop like that) and it interfered with installing ubuntu.  Is this true?

Also, does the wireless work out of the box?  I know it has the Intel Pro Wireless 2200, and I'm pretty sure that will, but just to be sure ;-) 

Many thanks

---

### Post by audax321 on 2005-10-04
Yup, the wireless worked out of the box. Also, the quickplay partition does not interfere with the Linux bootloader. As far as I can tell, it doesn't even support the filesystem so it just ignores it. Just have to make sure you don't overwrite the partition when you install Linux... but the system came with all the backup CDs in case you do anyway.

---

### Post by numberexhaust on 2005-10-04
All right, two more *last* questions before I jump into buying this computer.  First off, I know it has no dedicated graphics memory.  I'm not really planning to use this machine for any hardcore gaming, but have you found this a problem at all so far?

Secondly, the case is made of all plastic, which I'm not a fan of.  When you pick up the notebook with one hand, does it creak at all under its own weight?  In my opinion, notebooks that do this aren't very good.

---

### Post by audax321 on 2005-10-09
Well, I have a 1.5GB of memory in it so I haven't had a problem. Although it probably won't run Composite in xorg or anything like that. It also is not a gaming laptop.

As far as creaking goes, yes it does creak a little. But, I don't think it is going to break or anything. Try searching google for reviews on the laptop, it normally scores pretty high. And I've always heard that in terms of build quality it goes:

Apple/IBM > HP > Dell

But Apple and IBM obviously cost a lot more than an HP or a Dell.

---

### Post by RastaMahata on 2005-10-09
Ok... New question. Has anyone tried breezy lately?
-Wireless and mute leds dont seem to work
-Switching to an external monitor WITHOUT a monitor plugged in throws garbage in the laptop lcd monitor (To fix the screen, switch to a virtual terminal (ctrl+alt+F[1-6]), and switch back to tty7 (ctrl+alt+f7)).
-Switching to an external monitor WITH a monitor plugged in actually works well, but as the laptop has a widescreen, the external monitor gets a crappy resolution (which as far as I know, is unfixable).
-Memory card reader and firewire dont work...
-TV out (s-video) doesnt work...
-Graphic card is recognized as i810 (being 900)

If There's a way to fix these things, or you know who should I send these bugs to, please tell me :(

---

### Post by audax321 on 2005-10-09
I'm using Kubuntu Breezy:

-Wireless and mute leds dont seem to work

Mute LED doesn't work for me, but wireless works fine. The wireless config    is really messed up though and I think it might be a breezy problem. I had to help a few people with it in the chat forums as well. I actually had to edit /etc/network/interfaces manually to get it to work. I'll post mine below if you want to take a look at it.

-Graphic card is recognized as i810 (being 900)

I noticed this too. Reading on Google though it appears that the updated i810 driver includes support for the 900. They just didn't change the driver name??? But, I'm also noticing bad performance under KDE sometimes if I make the selection square on the desktop and then rapidly resize it. When I boot into WinXP, it works fine. So maybe this driver isn't correct?

No idea on the other issues since I haven't used them. Here is my /etc/network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# ETH1 (wireless) Configuration
# Make sure that the wireless key doesn't have an s: in front of it.
iface eth1 inet dhcp
wireless-essid ####
wireless-key #####

# ETH0 (wired) Configuration - disabled since I always use wireless
# iface eth0 inet dhcp

# Automatically activate ETH1
auto eth1

# Automatically activate ETH0 - disabled since I always use wireless
# auto eth0

```

---

### Post by apu95 on 2005-10-15
Yaaaay, some other people who have a similar laptop. I have the DV4000...I think the difference is the size of the screen, I'm not sure. With the previous version of Ubuntu, I had to manually updated the drivers for the wireless, because they didn't work. I installed Breezy today and they work outta the box (although I updated them anyway to the latest version). I know that the TV out, firewire and card readers don't work. I'm not very interested in getting the firewire and tv out working, since I'll be using it to program mostly. I wouldn't mind getting the card reader working, since I could pass my pictures from my digicam directly into Ubuntu whenever I need it instead of having to boot into windows all the time.

My gfx card is also recognized as the 800 instead of the 915, but apparently it doesn't matter. I downloaded TuxRacer and it runs awesome and fluidly :).

The trackpad works halfway only. I had to manually enable drag and dropping (found it in another thread in this forum), and I've yet to discover how to enable the vertical scroll section on the right side of the trackpad.

As for the multimedia buttons, I know that the Vol Up/Down/Mute work, and even a little window appears showing the level of the volume.

---

### Post by 4ebees on 2005-10-21
[QUOTE=apu95]Yaaaay, some other people who have a similar laptop. I have the DV4000...[/QUOTE]

Hey apu95, I have a DV4000 (well, dv4121ap)... good to see someone else has one.

The downside is I'm running Fed Core 4 on it - only because Ubuntu, for some strange and sad reason :( , doesn't support my graphic tablet and FC does (otherwise it would have been a Ubuntu machine).

That said, I'm trying to find out if the multi-media card will work. So if I find out how, I'll post here and PM you. Bluetooth is something else I'm working on (I can *see* my Motorola E1000, but have no idea how to access the files etc).

Just thought I'd let you know **you're not alone**!! :)

(For those curious as to why I'm reading the Ubuntu Forum: I have Ubuntu on two desktops :))

---

### Post by Bharath on 2006-09-04
Hi,

Check out [http://memoranda.sourceforge.net/](http://memoranda.sourceforge.net/) for Onenote replacement. Memoranda has more than 50% of the functionalities of OneNote.

Bharath

---

