---
title: "White Screen after login after upgrade to 9.10"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by Java Geek on 2009-10-26
Hello everyone,
I just upgraded to 9.10 and was expecting a great new shiny OS to play with, but after logging in, I see my splash screen login bar turn to white and then the screen is just white and my mouse (which is able to move BTW). This is really bad because I cannot even log into failsafe mode and no recovery CD. I have sensitive data that can me ported to my windows 7 machine, but I would prefer not to. 

I have access to terminals TTY1-TTY6, so thanks and I really hope you can help me this time!

-- Stephen

---

### Post by blittle on 2009-10-26
> **Java Geek said:**
> Hello everyone,
I just upgraded to 9.10 and was expecting a great new shiny OS to play with, but after logging in, I see my splash screen login bar turn to white and then the screen is just white and my mouse (which is able to move BTW). This is really bad because I cannot even log into failsafe mode and no recovery CD. I have sensitive data that can me ported to my windows 7 machine, but I would prefer not to. 

I have access to terminals TTY1-TTY6, so thanks and I really hope you can help me this time!

-- Stephen
I have the same issue with my 1501 Inspiron Dell Laptop. Just upgraded form 8.04 to 8.10, was running on battery by accident. After I ran dpkg to unpack again, I was at least abble to get a a login splash page where before I could not. But naow after logging in, all I get is the white/beige screen, a movable mouse/arrow and that's it! I hope you have better luck getting help than myself. I feel like it has to do with the video setings, but not clear what config file to summon in term to fix or set video settings.

---

### Post by Java Geek on 2009-10-26
With sometimes a little bit of a beige swirl (SOMETIMES) but very faint. 

My card is ATI Radeon 9600, which I admit, is very old, but it works most of the time with Windows 7.

If no one knows, then is there a safe way to back up to 9.04?

---

### Post by blittle on 2009-10-26
> **Java Geek said:**
> With sometimes a little bit of a beige swirl (SOMETIMES) but very faint. 

My card is ATI Radeon 9600, which I admit, is very old, but it works most of the time with Windows 7.

If no one knows, then is there a safe way to back up to 9.04?

I have a ATI Radeon Xpress series. hmmm...

---

### Post by Java Geek on 2009-10-27
Bump?

---

### Post by Mark Phelps on 2009-10-27
All this thread hijacking isn't helping ...

To ALL: This is most likely to be a video driver problem, as this has happened a LOT to folks running ATI cards that had ATI drivers installed prior to the upgrade.

Go to a terminal, or to a console if you can't get a desktop, and enter "lspci" -- and look for entries for ATI cards.

If you DO have them, and your are not running one of the latest HD 3x/4x/5x cards, then the ATI driver is likely to be the problem.  In that case, use the info in the link below to remove the ATI driver and replace it with the open source driver:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

To those of you NOT running ATI cards, please don't hijack this thread but open a new one for your problem ...

---

### Post by jessiebrownjr on 2009-10-30
> **Mark Phelps said:**
> All this thread hijacking isn't helping ...

To those of you NOT running ATI cards, please don't hijack this thread but open a new one for your problem ...

Im having this same issue with a geforce 8400 GS. Exact same, so its not an ATI issue soley, so I don't think its thread hijacking in the least bit.

---

### Post by jessiebrownjr on 2009-10-30
ok, I found something that will probably work over time as the devs fix it

Reboot into the new kernel*** recovery mode***, do the prompt with networking
then do
```
apt-get upgrade
```

It will download any applicable upgrades via terminal.

After I did that, I thought it was the magic button. I booted into the desktop, but as soon as I tried to use a program the desktop crashed again. makes me think they are aware of it, but every day or so ill to upgrade this way as well

---

### Post by Java Geek on 2009-10-30
> **jessiebrownjr said:**
> ok, I found something that will probably work over time as the devs fix it

Reboot into the new kernel*** recovery mode***, do the prompt with networking
then do
```
apt-get upgrade
```

It will download any applicable upgrades via terminal.

After I did that, I thought it was the magic button. I booted into the desktop, but as soon as I tried to use a program the desktop crashed again. makes me think they are aware of it, but every day or so ill to upgrade this way as well

Thanks, I've done that via the command line, but I keep receiving 404 not found errors. However, the same site I am able to ping successfully. This is confusing!

---

### Post by blittle on 2009-10-31
This is what worked for me, but will skip the first attempt of the last step so as not to waste anybodies' time:

First, ran apt-get upgrade as jessiebrownjr suggests.

then the second step:

1. Select recovery mode from the boot menu.
2. Select login as root from the menu in recovery mode.
3. Type this at the prompt

    # sudo apt-get remove xorg-driver-fglrx
    # sudo dpkg-reconfigure -phigh xserver-xorg

4. Exit

    # exit

5. Now select Resume normal boot from the menu.

Method can be found here [http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html](http://blog.dipinkrishna.info/2009/06/blank-screen-after-boot-process-in.html)

Finally it worked!
It seems that I had to run apt-get upgrade due to original issue that I had an interrupted update to begin with or possibly 8.04/9,04 bug with video driver? Either way, I decided to do aclean upgrade to 9.10 since and I am happy so far!

---

### Post by Java Geek on 2009-10-31
I too just did a clean install, just so that I could have a clean new system to work with. So far I'm very happy, and I did look up that solution before I reinstalled and it looked like it would have worked great, but like I said, I just clean installed. Thanks all!

---

