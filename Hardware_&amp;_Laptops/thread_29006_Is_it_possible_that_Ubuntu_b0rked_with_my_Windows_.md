---
title: "Is it possible that Ubuntu b0rked with my Windows resolution????"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by simianMiscreant on 2005-04-22
**Hardware**: 15.4 inch 1920x1200 LCD laptop screen, 256MB ATI Radeon 9800 Mobility
**Software**: newest ATI drivers for my card (from DELL), newest VBIOS for my card (from DELL), Windows XP Professional, Ubuntu Linux 5.04 (and whatever the default kernel for it was on install - 2.6.10?), x.org using fglrx (OpenGL 3D acceleration enabled)

My Windows video options, after I enabled (and how!) x.org hardware acceleration with fglrx, have completely lost the capacity to display 1680x1050 and 1280x800. I run my desktop environments in Ubuntu and Windows at 1920x1200 because they look uber-sexy, but higher-demand games I used to run at 1280x800 or 1680x1050. Now, when I go to Display -> Options in Windows, these two resolutions are **totally gone ** (they're also gone in any third-party resolution app I try). I'm wondering whether x.org could have cross-partition implications - **Windows** (even after reinstalling video drivers and VBIOS) **seems to have completely 'forgotten' about these other resolutions**.  It doesn't make sense to me that x.org should mitigate screen resolutions in Windows, unless my Linux video configuration has made irreversible changes to my video hardware (I don't know if that's possible, but it **freaks me out**). This is by no means an emergency, as my screen still supports its full range of 4:3 resolutions - I can still run the intensive games at 1280x1024 (or whatever), but they look crappy and 'stretched.' This problem has me entirely stumped, and has also confused DELL tech support, my l33t friends, and people on other forums. Any help you all could offer would be **greatly ** appreciated, and I'm more than willing to supply any additional information you need.

P.S. I formatted my Windows partition to try and fix the problem, but to no avail. The problem persists!

---

### Post by Deusiah on 2005-04-22
Please edit your the title of your post!

That type of language is not tollerable and I am very surprised it has not been filtered.

---

### Post by simianMiscreant on 2005-04-22
Right, sorry...momentary judgment lapse  ;-)  . The language persists in your reply title though, so you might edit that.

---

### Post by simianMiscreant on 2005-04-22
somebody **please** help!

---

### Post by Deusiah on 2005-04-23
Yes lol, I fixed that thanks,

Linux does not change the Windows set up, my guess would be the BIOS update perhaps?

You should try and use another tool to set the resolution in windows. Many programs will use a list of available resolutions but some let you type in what you want such as Wizmo: [http://grc.com/wizmo/wizmo.htm](http://grc.com/wizmo/wizmo.htm)

Try and set your res with that and report what happened.

---

### Post by simianMiscreant on 2005-04-24
Anyone else have thoughts? Thanks.

---

### Post by simianMiscreant on 2005-04-26
:| helpless without help

---

### Post by nad on 2005-04-26
Have you tried reverting to your previous bios? How about pulling the battery out and holding the power button down for about thirty seconds to see if the video chip becomes uninitialized?

What happened with that other resolution setting app that was mentioned.

And if the word borked is considered low, foul, obscene, indecent or socially incorrect in any language, I will stop using it. Besides, words with the letter k in them just seem to be funny.

Opera Press Release: Opera releases "Bork" edition:

[http://www.opera.com/pressreleases/en/2003/02/14/index.dml](http://www.opera.com/pressreleases/en/2003/02/14/index.dml)

---

### Post by ouminan on 2005-04-26
What drivers have you used to enable your wide-screen resolutions?

Not sure if any particular drivers might work better for you, if you'll have to define your own resolutions using some utility like Powerstrip...

I just got a notebook with a 1920x1200 display and I'd hate if this happened to me!

WUXGA == Sexy!

---

### Post by Deusiah on 2005-04-28
[QUOTE=nad]And if the word borked is considered low, foul, obscene, indecent or socially incorrect in any language, I will stop using it. Besides, words with the letter k in them just seem to be funny.[/QUOTE]

It obvioulsy wasn't the word borked :roll:.

Have you tried asking this question on a Windows forum since it really has nothing to do with Linux?

---

### Post by nocturn on 2005-04-28
Ok, here is the deal.  You have a Windows problem, it is not related to your use of Ubuntu.  The only causes with a probability of more then 1E-1024 is the BIOS update or some fixes/patches/drivers you installed in Windows.

So, this question will be better asked on a windows forum.

---

