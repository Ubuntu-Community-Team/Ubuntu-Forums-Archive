---
title: "S3 Unichrome Pro on Ubuntu 7.10"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by svenerikjensen on 2007-10-23
Ok, I've been sitting for 10 hours straight now to get this working, I give up. If nobody can help me I'll have to go back to Vista and hang-ups 15  times a day, and I really don't want that. I've browsed the web for 4 hours looking for a sollution, with no luck. Nothing works, not the unichrome project, not via drivers, nothing. Or, as I'm a complete linux nubber, I'm doing something very wrong. After I install drivers, what am I supposed to do? The xorg.conf shows the via driver, but I have no idea if it has to show unichrome or what not.

So, anybody able to help me on this. I can honestly say that I have my doubts that I'll ever get above 1024x768 on this computer.

Link to computer specs: [http://www.afterdawn.com/hardware/product_details.cfm/3043/fujitsu_siemens_amilo_la_1703-14b](http://www.afterdawn.com/hardware/product_details.cfm/3043/fujitsu_siemens_amilo_la_1703-14b)

xorg.conf has all the correct resolutions and stuff, but it won't let me choose the correct resolution, even after choosing a 1280x800 screen. :S

Please help.

---

### Post by rashaba on 2007-10-24
Ubuntu doesn't support that chipset. Try VESA with a 1280x800 resolution instead. I managed to run 7.04 with quite good results on a Amilo 3515 with usable results. Forget the Unichrome drivers. Performance should be okay if not better than with the VIA drivers.

To set the up VESA with the desired resolution use this command:
[INDENT]sudo dpkg-reconfigure -phigh xserver-xorg[/INDENT]

It also works on 7.10 but since this release has so many issues with these cheap Fujitsu laptops I would strongly advise against installing it on these models.

---

### Post by Nightdrive on 2007-10-24
I feel your pain!

I have a Jetway Micro-ITX board with Unichrome graphics, connected to a 1366x768 LCD TV

It appears that the really useful looking 'System' - 'Administration' - 'Screens and Graphics' utility in 7.10 is about as much use as the proverbial chocolate fireguard. Despite have options for S3 Unichrome, it keeps reverting back to VESA without having the good grace to say why.
The also useful looking monitor resolution settings, which even include a 1360x768 setting for my Samsung LCD TV - just don't work - resulting in one of those strangely interlaced screens where you get 4 copies of everything on screen.

All in all, it ;looks like a premature release for this feature.

Although I haven't got around to it yet on 7.10, I did manage to get Unichrome working on 7.04 by following this guide:

[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")
(I never succeeded with the 3D driver though)

I seem to remember having some fun and games getting the right modelines in xorg.conf, to get my desired resolution. There are various modeline generators around, but some didn't work. I seem to remember having to read the frequencies from my TV manual to get the right data in there. I didn't make any notes on this, but I did save my xorg.conf file for future use.
It may even be that once the driver is installed the 'Screens and Graphics' utility may work for resolution.

If not, other useful links:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")

[http://ubuntuforums.org/showthread.php?t=203905&page=2]("http://ubuntuforums.org/showthread.php?t=203905&page=2")

I hopething in here is useful.

Greg Woods

---

### Post by ton145 on 2007-10-25
I have the same problem.
My motherboard is Asus P5VD2-MX-SE with P4M890 chipset. I've tried every 'solutions' that ever exists in this planet, but it always revert back to Generic Vesa driver.

---

### Post by Officer Dibble on 2007-10-25
Unless its a laptop, in all honesty I have only ever used the integrated graphics card as a back-up and bought a proper card such as an Nvidia.

---

### Post by stinger30au on 2007-10-25
i use this little trick in 7.04 and it does the trick

If your monitor is giving you a hard time and not showing the right resolutions this little trick may fix it
sudo nano /etc/X11/xorg.conf
scroll down using the arrow keys till you find this section
Section "Monitor"
at the bottom of this section add these two lines

HorizSync 30-110
VertRefresh 50-70

now quit and save and restart. with a bit of luck, should be all good!

---

### Post by svenerikjensen on 2007-10-25
I actually got it to work, even if the chipset isn't supported. :) Only trouble is I've tried so much I have no idea what finally made the change. All I know is vesa driver doesn't work with anything else than 1024x768. I downloaded the Ubuntu VIA driver from [www.viaarena.com](www.viaarena.com), installed this. I edited the xorg.conf so that driver said "via" instead of "vesa". And in the screen selection unders "System/Screens and Graphics" I marked up for widescreen, and chose the 1280x800 lcd panel. After that I was able to choose 1280x800 resolution. Make sure there's alot of resolution options in your xorg.conf file. Shouldn't be much trouble if you use that auto-config feature that I don't remember what's called. :D Anyways, shouldn't be too hard to find.

Sry for my bad instructions, but I've been using Linux for about a week. :D

---

### Post by forestgril on 2008-03-15
YES - IT WORKS! (ubuntu 7.10, via unichrome, amilo pro 2055, 1280/800)

You have to download the drivers from

[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=163](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=163)

and follow the instructions in the attached files.

Watch out only for the name of the file to open in terminal. In the instructions it is written:

# sh VIA_Ubuntu710_Unichrome_GFX_v40072d.run

In fact You should check the exact real name of the file and write in terminal (when I opened it worked):

sudo sh VIA_U710_UniChrome-GFX-v40072d.run

Then read the rest and follow. You can also do, what was written in the previous post.

If there are any unexperienced users (NOOBS), who want more info, just reply to this post or private message to me, and I will give STEP-BY-STEP instructions.

---

