---
title: "Tried to upgrade video card to Radeon 6870 on 10.04 system; now blackscreen at login."
date: 2010-12-30
forum: Hardware
---

### Post by kulturloseramerikaner on 2010-12-30
Well, not totally black. There is some incoherent white pixellation at the very top of the screen.

OK, this is what happened:
I swapped out the nvidia 8800 GTS card that's been in there for way too long for a Radeon 6870. It freaked out, as I expected, after booting up again, saying it couldn't find the old card and gave me an extremely basic-looking screen with low res and none of the effects. No biggie, I expected this.

I uninstalled all the nvidia components from my system in Synaptic, and gave another reboot. That's where the fun started.

After the reboot, I got a horrible looking screen; very low res, colors are completely off, as though I were looking at a negative. Quick search of the web lead me to ATI's driver download site here [[COLOR="Blue"](ATI Driver)[/COLOR]]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English") and after a bit more digging I found the destructions on getting this running here [[COLOR="Blue"]Maverick Installation Guide[/COLOR].]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide") I ran through the procedure to remove old drivers, just to make sure, and then tried this install. Another forum pointed me back to the same guide, but because I was getting the "hardware not detected" issue suggested I manually edit my xorg.conf to force the fglrx driver. And now I get the (mostly) black screen...

First, please help me get back to where I can at least see what I'm typing, and if you have any pointers on getting this thing running, I'd appreciate them.

Thank you.

BTW I'm not sure if this'll make a difference, but I have both Gnome and KDE installed but I'm using Gnome as the default.

---

### Post by pi/roman on 2010-12-30
I hope you have a live cd handy for any version of linux. You can boot up from the cd and mount your hard drive then just go in and edit your xorg.conf again.

---

### Post by dandnsmith on 2010-12-31
If you have a liveCD handy, then you've nothing to lose by booting it in trial mode.
If that seems to work OK for graphics (perhaps not the best that could be got, but initially acceptable), then clear out any xorg config file you've built up, and let the software sort things out.

Providing you've not 'hard wired' your old config in too many places it should configure on the fly, and provide a good basis for starting any improvements.

Worth a try?

---

### Post by kulturloseramerikaner on 2011-01-02
I could say something, but I won't... I'll take the hit. Good call on the LiveCD. Too obvious, I overlooked it completely.

I've gotten things back to where they were, with the horrible negative image that at least lets me see what I'm doing, and am currently trying to figure out why I'm getting the "No supported adapters detected" error when I try to configure a new xorg.conf.

---

### Post by kulturloseramerikaner on 2011-01-02
We're making progress; I ran through the tutorial on the installation guide and got the "No supported adapters detected" issue again. I again modified my xorg.conf file as in my first post, and am now coming to you from my Ubuntu desktop with all features enabled - Compiz work great, colors are accurate, and I'm getting the full 1920 x 1080 res out of the monitor. Problem is, now I have a watermark in the lower right that reads "AMD Unsupported hardware." I'll keep working on that, and will report back if I find anything, else any help is appreciated.

Thank you.

---

### Post by dandnsmith on 2011-01-03
Good to see you've made progress - that watermark is curious.
I see that it is mentioned in the tutorial you referenced, and a possible workaround to use if the update suggested doesn't work.

I guess you're using the catalyst drivers and fglrx?

Should your sig be updated to 10.04 now?

---

