---
title: "Alternative to Lenovo W510?"
date: 2010-05-11
forum: Hardware
---

### Post by jackiemcghee on 2010-05-11
I've recently been messed around trying to get a Lenovo W510 (supply problems, vendor being incredibly unhelpful etc.) so I cancelled my order.

Previously, I was a Linux on Macbook Pro user and have no idea about non-Apple hardware. I'm adamant, however, that I won't be giving Apple any more of my money. So I was wondering if anyone could help me out with an alternative to the W510.

I need a machine of that calibre and one that won't give me a laundry list of headaches when it comes to getting Linux up and running on it.

Basic needs are: powerful processor, discrete VRAM of around 1GB, very high resolution screen, nice keyboard, 7200rpm disk, plenty of RAM.

I was going to have a peek at the Dell site but I remember them having serious build quality problems (especially around the screen) when I last checked them out about 9 years ago. If this is no longer an issue, I'd be grateful to hear about it.

ETA: I checked out the Dell 4500, and that is the kind of thing I am interested in.

---

### Post by ltmon on 2010-05-12
I've got the W510, and I have it because I couldn't find an alternative I liked :) I wasn't willing to go to a 17-incher however, which will give you more flexibility.

If you don't order the FHD screen you will have better luck, as they are the problem part for supply issues. I'm using the HD+, which arrived in about a week.

Possibly the G series gaming laptops from Asus, such as the G51JX-X1? It seems to have mostly compatible hardware, and a couple of reports of playing nice with Ubuntu.

---

### Post by mesaphlin on 2010-07-14
> **ltmon said:**
> I've got the W510, and I have it because I couldn't find an alternative I liked :)

The Ubuntu works with the specific model flawlessly? Because I wanna purchase one for myself too for only Ubuntu...

:)

---

### Post by ltmon on 2010-07-14
> **mesaphlin said:**
> The Ubuntu works with the specific model flawlessly? Because I wanna purchase one for myself too for only Ubuntu...

:)

Nearly flawlessly, but only with a little extra configuration.

The main things you need to do are:
- Update the W510 BIOS to the absolute latest version
- Install the most recent stable nvidia driver available (I use the Ubuntu X-Swat updates PPA version)
- Make a couple of manual changes to xorg.conf to enable the brightness control to work properly
- Unload the USB3 (xhci) module upon suspend and reload it upon resume, as the W510 freezes otherwise

This page should outline most of it:

[http://www.thinkwiki.org/wiki/Category:W510](http://www.thinkwiki.org/wiki/Category:W510)

The last problem I had was a really ugly boot screen once I had updated to the latest nvidia drivers. This can be fixed by a slightly complicated process described here: 

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

Otherwise, it's pretty much flawless.

---

### Post by mesaphlin on 2010-07-14
> **ltmon said:**
> 

The main things you need to do are:
- Update the W510 BIOS to the absolute latest version
Should I do it after Ubuntu installation on the harddrive or while it is in windoze mode?
> **ltmon said:**
> - Install the most recent stable nvidia driver available (I use the Ubuntu X-Swat updates PPA version)
I guess I can handle that...
> **ltmon said:**
> - Make a couple of manual changes to xorg.conf to enable the brightness control to work properly
Could you write it down please if I may ask? I don't want to be a headache for you but I might really need it after I purchase the Thinkpad...
> **ltmon said:**
> - Unload the USB3 (xhci) module upon suspend and reload it upon resume, as the W510 freezes otherwise


This page should outline most of it:

[http://www.thinkwiki.org/wiki/Category:W510](http://www.thinkwiki.org/wiki/Category:W510)

The last problem I had was a really ugly boot screen once I had updated to the latest nvidia drivers. This can be fixed by a slightly complicated process described here: 

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)



The pages you mentioned do not incline the specific problems you had with the Thinkpad. Could you also tell me how could I unload the USB3 (xhci) module upon suspend and reload it upon resume?

I hope I am not becoming a headache which I really don't want to bust your balls about it but I really need your help and I will definitely get the ThinkPad W510 really soon...

Thank you so much if you could help me!!!...

Please take care so much!!!

Yigit

---

### Post by ltmon on 2010-07-14
Update the BIOS whenever you want. I used the bootable ISO from Lenovo, and there's also a Windows exe to do the same thing (I think).

The Thinkwiki site is all about the W510... but not well organised, so here's the most relevant bits:

> To enable brightness control in X, append 'Option "RegistryDwords" "EnableBrightnessControl=1"' to the Device-Section of xorg.conf, orginal source: [http://www.nvnews.net/vbulletin/showthread.php?p=2204839#post2204839](http://www.nvnews.net/vbulletin/showthread.php?p=2204839#post2204839).

> All Versions: System cannot suspend unless SUSPEND_MODULES="xhci" is added to /etc/pm/config.d/unload_modules (may need to create this file)

Let me know if you don't fully understand either of these.

Some of the other information is out of date, especially if you've applied the BIOS updates, so don't worry too much about the rest unless you encounter a specific problem.

The second page linked is not specific to the W510, but I followed the steps exactly and it worked for me. Note, you don't have to do this -- it just prevents an ugly looking screen while you boot up.

---

### Post by mesaphlin on 2010-07-14
Thank you so much...

I hope I will solve the problems when I install the Ubuntu on it. If I cannot I know that you will help me. 

Thank you so much again...

Please take care of yourself!!!...

Yigit

:)

:guitar:

---

### Post by kapetanski on 2010-09-10
Have you tried to connect an external screen?

---

### Post by ltmon on 2010-09-10
> **kapetanski said:**
> Have you tried to connect an external screen?

Yes. I use a displayport-to-dvi adapter, and have had no problems in this regard.

Ensure you have

Option      "TwinView" "true"

As part of your xorg.conf "device" section.

---

### Post by kapetanski on 2010-09-10
That's great! Thank you for the quick response.

Anyone tried the turbo mode in ubuntu? I've read something about the system clock going too fast when this is enabled.

cheers

---

### Post by ltmon on 2010-09-10
TBH I haven't tried, I wasn't even properly aware of it, so doing some reading now.

Obviously it's quite fast without the turbo mode, but I'll see if I can enable this later today and see what happens.

---

