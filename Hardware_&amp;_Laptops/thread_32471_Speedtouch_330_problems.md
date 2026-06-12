---
title: "Speedtouch 330 problems"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by AdamSebWolf on 2005-05-07
Hi,
    I'm in the middle of trying to set up my speedtouch 330 on ubuntu again. Previously I did this on warty and it took 4 tries with totally different HOWTO's to get it working.
   Once again on hoary, it's the same situation. I have used these HOWTO's so far:
[http://www.ubuntulinux.org/wiki/UKSpeedtouchDSLHowTo/view?searchterm=speedtouch](http://www.ubuntulinux.org/wiki/UKSpeedtouchDSLHowTo/view?searchterm=speedtouch)
[http://speedtouchconf.sourceforge.net/](http://speedtouchconf.sourceforge.net/)
[http://linux-usb.sourceforge.net/SpeedTouch/index.html](http://linux-usb.sourceforge.net/SpeedTouch/index.html)
   So far, each of these has refused to work.
   With speedtouchconf, I managed to get it to work the first time I ran it, and I set it to save its settings. The next time I rebooted it didn't dial up, and now when I try to run the speedtouchconf.sh, it flips out and starts reporting modem_run errors.
   
    Does anyone have any advice?

    The ubuntu install I did was totally normal, and I've not configured a thing since I installed apart from attempting the modem so surely I can't be alone in this? I don't see what can have gone wrong since the clean install to stop these HOWTO's from working (unless theres a PEBKAC error going on.)
   My pc is of pretty average hardware (AMD XP2000, 256Mb, USB1.1, well supported sound + gfx), and for me to have met such trouble setting the speedtouch up suggests that it can't be a one-off on my machine.

    Any help would be really appreciated!

---

### Post by rdfi on 2005-05-12
I've tried 6 different how-to's including the ones you mentioned, none worked, so you're not alone.

I'm serioulsy thinking about buying another modem...

---

### Post by AdamSebWolf on 2005-05-16
Well that's a relief!

I don't get it though, windows has no problem installing and using it, so it's not a modem problem - there's just something going on with linux. But it's worked fine before, so confusing!

---

### Post by Consumer on 2005-05-17
Hi,

I got my speedtouch 330 working with speedtouchconf after a little bit of tweaking. I'm not sure you're having the same problems as I did but it would be useful to see what error messages you got.

I found the answers to my problem on the speedtouchconf sourceforge site in the forums. For me it was simply a problem with the way it used my USB port. Also make double sure that you have the correct microcode for your model of the speedtouch 330. I made the mistake of downloading the wrong version and it wouldn't work at all.

Cheers

James

---

