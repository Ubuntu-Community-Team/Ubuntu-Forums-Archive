---
title: "trackpad not working (9.10 karmic Koala on Asus 1008HA)"
date: 2010-02-09
forum: Hardware
---

### Post by gregnorc on 2010-02-09
So the issue is that there's something (software related) wrong with my 1008HA's trackpad. At some point I accidentally hit the switch on my 1008HA to turn it off.

No big deal right? It's one of those classic errors, you just hit the button again to turn it on. 

But when I hit the switch to turn it back on, instead of having the tackpad work again, I get the error "unable to enable touchpad ensure xorg.conf is configured properly".

So currently I need an external USB mouse to use anything GUI related.

I did a search for the error I was getting, which was as follows:
> unable to enable touchpad ensure xorg.conf is configured properly


Googling the above error turned up [this message board topic]("http://forum.eeebuntu.org/viewtopic.php?f=45&t=2986&start=0"), which pointed me to a [sample xorg.conf]("http://eeebuntu.org/wiki/index.php/Xorg") that was supposed to fix the issue. I updated my xorg and rebooted, but the issue persists.

I've had this issue for months... I briefly installed windows to check it was actually a software issue, and the trackpad worked when it was using that, so I know it's not a hardware issue. Instaling windows is not an acceptable solution for me however :) 

Having to carry a mouse everywhere is a HUGE pain, so if anyone has any suggestions I'd appreciate them. I am running Ubuntu 9.10 (Karnic Koala). Full from uname -a: Linux ruckus-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Below is a copy of the xorg file I had:

And here is the output from dmesg:
[http://pastebin.com/m2a1cd23](http://pastebin.com/m2a1cd23)

/var/log/Xorg.0.log:
[http://pastebin.com/m659cc57f](http://pastebin.com/m659cc57f)

I can post anything else needed, I'm just really interested in getting the trackpad working again (without resorting to going back to windows! :))

---

