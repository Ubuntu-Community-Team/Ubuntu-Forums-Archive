---
title: "Workaround: notification und compiz problems with (older?) radeon cards in 9.10"
date: 2009-11-02
forum: Hardware
---

### Post by buellman on 2009-11-02
**Notice**: for me this workarround failed after the next reboot or so but you maybe try it anyway and leave a message if it helps. If it does not help anyone in the long term this thread should be deleted.
-------
Hi,

as I had problems with notifications and compiz in 9.10 and saw many ppl with the same problems (artifacts ...) I tried many modifications to my xorg.conf. What helped was the following modification to my xorg.conf:
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AGPMode"		"4"        # optional
	Option		"AGPSize"		"32"      # optional
	Option		"DRI"			"true"    # imprtant
	Option		"DRI2"			"false"  # important
EndSection

```
On launchpad I saw other modifications like disabling RenderAccel and so on... but as I like compiz I think this is a good way to go ;)

Greets. Grimsrud

BTW: I have an IBM X31 with a radeon 7000
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

---

### Post by zcacogp on 2009-11-30
Buellman, 

FANTASTIC! 

I've just tried this on my X31 (which I am typing this on), and it works with Compiz - which has failed to work since I upgraded to 9.10! 

I'm very happy! Many thanks. (If you were a pretty girl I'd kiss you on both cheeks, right now!) 


Oli.

---

### Post by buellman on 2009-12-01
@zcacogp

Are you sure that it does work for you? Because for me it did not in the long term :/
I had no time to correct this post or at least make a notice that it does not work for me after a reboot.

Would be cool if you could try it a bit more... if it also does not work for you after a reboot I think we can delete this post.

Greets. Buellman

Ps: sorry... I'm male ;-)

---

### Post by zcacogp on 2009-12-01
Buellman, 

You mean the fuzzy lines that appear along the top of the screen when you reboot? Ah yes ... I saw them when I rebooted (funnily enough!) 

It's not 100%. It's the best I have yet to manage, but it's not quite all the way there, is it? 

I'll carry on playing around, but without much hope (I am stabbing in the dark as I don't really understand what I am doing.) Let me know how you get on, and if anyone else has some good ideas then do post 'em up here ... thanks. 


Oli. 

P.S. I'm married, and I suspect that Mrs zcacogp would get a bit upset if she thought I was kissing strange pretty girls on both cheeks ... so it is probably a good thing you are male! :)

---

### Post by buellman on 2009-12-01
> **zcacogp said:**
> Buellman, 

You mean the fuzzy lines that appear along the top of the screen when you reboot? Ah yes ... I saw them when I rebooted (funnily enough!)

Yep... that was what I mean.

> **zcacogp said:**
> It's not 100%. It's the best I have yet to manage, but it's not quite all the way there, is it? 

I'll carry on playing around, but without much hope (I am stabbing in the dark as I don't really understand what I am doing.) Let me know how you get on, and if anyone else has some good ideas then do post 'em up here ... thanks.

Well. You can set the following in your xorg.conf:
```
Option "RenderAccel" "off"
```
That will work nearly perfect... only thing is: you can't use compiz because 3d acceleration would be turned off. Other than that there will be no problems with "fuzzy lines" and so on.
So you maybe would like to add the mentioned line to your xorg.conf and delete the "DRI" and the "DRI2" ones :-)

> **zcacogp said:**
> P.S. I'm married, and I suspect that Mrs zcacogp would get a bit upset if she thought I was kissing strange pretty girls on both cheeks ... so it is probably a good thing you are male! :)
HeHe... I think you are right. So no kisses for me but hopefully some for your wife after spending hours at your computer to fix stupid bugs :D

---

### Post by zcacogp on 2009-12-02
Buellman, 

Hmmm. Looks like you and I are very much suffering the same problems. Snag is that I like Compiz, and don't really want to turn it off! So the choice is, compiz with fuzzy lines, or no compiz but also no fuzzy lines. 

What I don't understand is why it works when you first turn it on, and then fails when you reboot. This suggests that it *can* work, but something happens when it reboots that spoils it. 

Surely we can't be the only people with this problem? There must be others? Should we / how do we report this as a bug? I am sure it is possible to solve, it's just that I don't know how. 

Out of interest, what do the DRI and DRI2 commands do? 


Oli.

---

### Post by buellman on 2009-12-02
> **zcacogp said:**
> [...]
Surely we can't be the only people with this problem? There must be others? Should we / how do we report this as a bug? I am sure it is possible to solve, it's just that I don't know how.

There are many bugreports on [Launchpad]("https://launchpad.net/") about this problem and we are far from being alone. I think one where most ppl reply to is this one: [bugreport]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/426582")
If you like you can add your voice in form of a comment there. I don't think that it is really necessary as the ppl behind the xserver-xorg-video-ati package allready know about the problem. It looks like there is not much that can be done at the moment. But you surely are free to add your comment :-)

> **zcacogp said:**
> Out of interest, what do the DRI and DRI2 commands do?

They tell the xserver that DRI should be used instead of DRI2. DRI2 should replace DRI in the future. But to me it looks like that the transition from DRI to DRI2 is not that easy and there is still some development necessary to get it to work.

I'm not sure but I think DRI2 is needed to get things like [KMS]("http://fedoraproject.org/wiki/Features/KernelModesetting") and other great future features to work.

Hope that helps a bit :)

Greets. Buellman

---

### Post by zcacogp on 2009-12-04
Buellman, 

Thanks. I've posted on the bug report you linked to, with a copy of my xorg.conf file. 

Having played around with it, the problem gets progressively worse the more you move between workspaces. You can mitigate this a little by turning off everything under "Desktop" in compiz, apart from "Desktop Wall" (which is needed to switch desktops), but it is still a problem. 

I have also found that when desktop effects are enabled I can't select things on the desktop. I am wondering whether this is relevant? 

Fingers crossed that those clever boys and girls in Canonical find the problem and fix it, and allow us to download the fix. For now, I am doing without compiz. (Ironically, I'm not a huge fan of the desktop cube, impressive as it looks. Compiz is much more useful for me for it's windows management capabilities.)

The other option would be to try playing around with the kernel that is used, as my suspicion is that an earlier kernel would solve this problem. Or bite the bullet and go back to 9.04 ... 


Oli.

---

### Post by tormod on 2009-12-04
[QUOTE=buellman]
```

	Option		"DRI"			"true"    # imprtant
	Option		"DRI2"			"false"  # important

```
[/QUOTE]
Why do you have those DRI options in there and why are they "important"?

EDIT: I saw the question and answer above, but what is the effect of using these options? Should be none, so why "important"?

---

