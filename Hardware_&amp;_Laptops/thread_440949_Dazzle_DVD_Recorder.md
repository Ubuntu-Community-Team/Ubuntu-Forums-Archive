---
title: "Dazzle DVD Recorder"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by technetium on 2007-05-12
Hi I've recently converted my laptop to linux. I'm on Edgy at present because Feisty doesn't support my  CD drive. Anyway, Does anyone know a way to get the Pinnicle Dazzle DVD Recorder working as its the only thing not working since I installed ubuntu? Thanks in advance...

---

### Post by technetium on 2007-06-21
DVC100 if that helps?:(

---

### Post by varm78 on 2007-07-18
Hi, just to tell you that I have the same problem.

---

### Post by technetium on 2007-07-19
Found some bits about running it on suse linux but that doesn't seem to help. It wont come up anywhere on google. :confused:

---

### Post by varm78 on 2007-07-25
Ok. I did some research and I found info about it, theres a how to, it's in french but have all the instructions to make it work.

Links:

[http://www.linuxtv.org/pipermail/linux-dvb/attachments/20070611/c63bc374/attachment.txt](http://www.linuxtv.org/pipermail/linux-dvb/attachments/20070611/c63bc374/attachment.txt)
[http://lea-linux.org/cached/index/Num%C3%A9riser_vos_anciennes_cassettes_VHS_sous_Linux.html](http://lea-linux.org/cached/index/Num%C3%A9riser_vos_anciennes_cassettes_VHS_sous_Linux.html)
[http://www.linuxquestions.org/questions/showthread.php?t=497596](http://www.linuxquestions.org/questions/showthread.php?t=497596)

Sorry for my English.

---

### Post by technetium on 2007-07-26
Thanks very much will try this out- french is not a problem. :)

---

### Post by eeried on 2007-12-09
The liunxquestions thread says dazzle will soon be supported by the kernel. is this the case now in Gutsy?

Do we still have to go through the Lea-Linux way? 

Would a Dazzle TV PCI card work easier?

---

### Post by fatguybp on 2008-03-19
Translate it with the google translator it works
[http://64.233.179.104/translate_c?hl=en&langpair=fr%7Cen&u=http://lea-linux.org/cached/index/Num%25C3%25A9riser_vos_anciennes_cassettes_VHS_sous_Linux.html](http://64.233.179.104/translate_c?hl=en&langpair=fr%7Cen&u=http://lea-linux.org/cached/index/Num%25C3%25A9riser_vos_anciennes_cassettes_VHS_sous_Linux.html)

But make sure you have the french one open too for the commands, (it translates those too and they wont work after translation)

---

### Post by bignickel on 2008-03-31
I just got one of these as well and got it to work.  Incidentally, if you find an AirLink 101 ATVUSB02 it does the same thing and works out of the box (at least for me).  Unfortunately I couldn't find another one of those so I got the Dazzle going.  The french instructions set it up for PAL, but if you're in North America you'll need to use NTSC.  In /usr/local/src/v4l-dvb-kernel/linux/drivers/media/video/em28xx/em28xx-cards.c search for the the Dazzle DVC 100 and change it to this:

```
	[EM2820_BOARD_PINNACLE_DVC_100] = {
		.name         = "Pinnacle Dazzle DVC 100",
		.vchannels    = 3,
		.norm         = V4L2_STD_NTSC,
		.has_tuner    = 0,
		.decoder      = EM28XX_SAA7113,
		.dev_modes      = EM28XX_VIDEO,
		.input          = {{
			.type     = EM28XX_VMUX_COMPOSITE1,
			.vmux     = SAA7115_COMPOSITE0,
			.amux     = 1,
		},{
			.type     = EM28XX_VMUX_SVIDEO,
			.vmux     = SAA7115_SVIDEO3,
			.amux     = 1,
		}},
		.tvnorms	= {{
				.name = "NTSC",
				.id = V4L2_STD_NTSC,
		},{
				.name = "PAL-BG",
				.id = V4L2_STD_PAL_BG,
			},{
				.name = "SECAM L",
				.id = V4L2_STD_SECAM_L,
			},{
				.name = "SECAM LC",
				.id = V4L2_STD_SECAM_LC,
			},{
				.name = "SECAM K1",
				.id = V4L2_STD_SECAM_K1,
		}},
	},

```

And it worked for me following the rest of the french instructions.  It would be nice for this to make it into the kernel.

---

### Post by eeried on 2008-04-01
> AirLink 101 ATVUSB02

This Airlink looks good but I don't seem to be able to find it in France. Does it really work out of the box on Gutsy?

---

### Post by bignickel on 2008-04-03
> **eeried said:**
> This Airlink looks good but I don't seem to be able to find it in France. Does it really work out of the box on Gutsy?

I borrowed an Airlink from a friend of mine, and it ran out of the box with no problems on Gutsy.  But i couldn't find one at a computer store near me (I didn't look too hard).

Now that I've mucked around with the v4l module to make it work with the Dazzle the Airlink doesn't work anymore.

---

