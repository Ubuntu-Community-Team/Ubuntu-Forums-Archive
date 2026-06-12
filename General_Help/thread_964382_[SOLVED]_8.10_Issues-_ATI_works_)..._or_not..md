---
title: "[SOLVED] 8.10 Issues- ATI works :)... or not."
date: 2008-10-30
forum: General Help
---

### Post by rwap on 2008-10-30
Hi,

First of all I would like to thank all of the people that have put work into 8.10, its beautiful! 

The LIVE cd worked flawlessly, even with my ATI X1950! I could turn on the extra effects and it all preformed wonderfully.

Before I go further, here are my specs.

AMD 64 X2 5000+
2GB Ram
320GB HD, 40GB to ubuntu.
realtek OB audio
ATI 512MB X1950 Crossfire enabled.
MSI motherboard(forgot what model)
Multi-boot, XP, Vista, Ubuntu 8.10 **X64 VERSION**.

ok,

I have used previous versions of ubuntu with failure, due to my X1950, I like others cant make drivers work for 3d support.  Much to my surprise, after installing 8.10, I had the "normal" visual effects, which is a improvement over past installs, I tried clicking "extra" and upon doing so, it searched for and found drivers for my card *WOW* much to my amazement, the effects worked wonderfully, that is until I updated 8.10, and it asked me to reboot.  Then it came back on the text login screen blinked 4 or 5 times and did nothing. :(  

So, digging way back in my history, I remembered that the xorg.conf file was in the /etc/X11 dir.  so I went there and overwrote it with the failsafe version. rebooted, and no go.. so with no browser, I just reinstalled 8.10, for the 3rd time.- the first time it hung on importing docs and settings at 80%-even though I didn't ask it to import them.)

So currently, I'm running 8.10 to post this, with "normal" effects, 

Is there a way to make the x1950 work to its fullest extent? although this is much better than it used to be.


also, this may require a new topic but, I have a Palm treo 680, I use it for a phone, contacts, calendar, and I use Splash money and ID for money management and ID storage, in windows, is there any way I can make these things work in ubuntu? I'm open to Linux replacements for splash money and ID.

I would love to break loose from the hold Microsoft has on me, but there are at least these reasons why I cant.

1. Non-sufficient support for my treo.- (Maybe)
2. No support for my Canon image class D660
3. Very limited support for windows apps. -Might have changed with the advent of WINE 1.0- Haven't tried in a while.
4. No ATI support for my GFX card- X1950

I'm sure there are more, but those are key.

I look forward to someones response.

---

### Post by rwap on 2008-10-30
I just seen this post... [http://ubuntuforums.org/showthread.php?t=964404](http://ubuntuforums.org/showthread.php?t=964404)

That's what happens to me, I figured it was the ATI drivers..

Maybe not? *HOPE*

I thought it was kinda weird that a new OS would have 6 updates already.

I'll try them again.

---

### Post by Yellow Pasque on 2008-10-30
Your post is somewhat confusing. Are you using the proprietary fglrx/Catalyst drivers or the open-source "radeon" driver?

---

### Post by rwap on 2008-10-30
sorry for the confusion,

I haven't downloaded anything, So I am using the FGLRX driver that ubuntu tries to load by default.

I just tried enabling the "extra" effects, again, in hopes it wouldnt crash, but it did, just as before it works until I reboot, Now im in Vista, so how do I turn off the FGLRX driver from the cmd prompt?

Thanks.

EDIT:

I just reinstalled 8.10- I think I'll give the ATI thing a rest until I get some concrete solutions. :) - Tired of reinstalling.

Edit 2: I just installed the updates they work fine so its definitely, ATI.

---

### Post by rwap on 2008-10-31
I got it!

Finally! after all this time! WOOT!

Thanks everyone!, This forum is priceless.

This is how I did it,

I found a post with this link in it..

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

then went to installing driver the ubuntu way.. followed to a T the directions, and it worked! I have access to ATI config program, and when I do fgrlxinfo, it says ati :guitar:  :popcorn: :):lolflag:

Not only does it work but I can play Delta force BHD in Wine! it works well except the ai gfx and the players hand does not render right, but it is very playable.

Thanks again!

For confirmation I have 2 ATI x1950 Crossfires, PCI-E cards (512MB).

---

### Post by Glaskows on 2008-11-01
Hey, I had the same problem (GA-MA78GM-S2H motherboard, 780g chipset).
"sudo aticonfig --initial -f" did the trick.

rwap: Thanks for pointing that guide up!

---

### Post by El_Perro_Perduto on 2008-11-01
Please help
I upgraded to 8.10 on my toshiba laptop and wanted to install drivers to work with my onboard ati graphix card.  According to lspci the video card is:
"01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]"


Downloaded the newest version of the ATI drivers for x64 processors and installed them according to the step by step in the wiki.  When I modify /etc/init.d/X11/xorg.conf to include fglrx as a driver in the device section, video hangs on reboot (e.g., it cycles a few time, the screen flickers and then hangs...I get nothing :() 

I am assuming that this is not uncommon. If anyone can suggest tweeks to xorg.conf or can show a correct config, I'd much appreciate it.

When I was using Ubuntu 8.04, I was able to get a step by step GUI driven installer from ATI, which detected everything automatically. Where do I find this?

---

