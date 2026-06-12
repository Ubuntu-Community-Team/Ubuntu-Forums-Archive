---
title: "ATI Mobility Radeon HD 2600 Graphics Card Linux Compatibility"
date: 2008-10-22
forum: Hardware
---

### Post by stephenj2008 on 2008-10-22
Hi,

I am interested in buying an Acer Travelmate 7720G laptop, which has an ATI Mobility Radeon HD 2600 graphics card.

I currently run both Ubuntu and PCLinuxOS and I took a live CD of PCLOS 2009 Beta 1 to a computer store and was allowed to try it out on the computer.  All seemed to work well, in terms of resolution.  I didn't try other features such as 3D (Compiz, etc.).  I have read on the net, however that some people have experienced difficulties with this ATI graphics card (resolution, refresh rate, etc).  Am I correct in believing that, though there appeared to be no problems in live CD mode,  this may not be the case after Ubuntu is installed, and problems such as those experienced by others, may surface?  If so, how does this happen?

The ATI Mobility Radeon HD 2600 card appears to be included in many laptops, currently.  Indeed, it seems that most of the laptops that I have interested me, contain this card &#8211; so I am wondering if anyone here has any knowledge of, or experience with this card (and how it works with Linux).  There have been a few mentions of it on the net (including references to drivers, both within repositories and located at the ATI site) but these have just resulted in confusing me even more (more knowledge of such matters, being very scant).  

Linux compatibility sites I have found don't make mention of laptops with this card.

I did find a site where this was discussed.  ([http://forum.notebookreview.com/showthread.php?t=222933]("http://forum.notebookreview.com/showthread.php?t=222933")).  One person wrote:

[I][http:////ati.amd.com/support/drivers/l...ux-radeon.html]("http:////ati.amd.com/support/drivers/l...ux-radeon.html")
[/I]
*This driver will simply work if you have, for whatever the distro, all headers installed. the installer will in fact build the driver, and the most recent installers have almost flawless package maintenance.*

But, the OP replied:

[I]The Mobility Radeon HD 2600 is not supported by the driver there. I guess it will come sometime in the future. AMD really needs to get on this, it's getting ridiculous.

*[https://a248.e.akamai.net/f/674/9206...ux.html#172394]("https://a248.e.akamai.net/f/674/9206...ux.html#172394")*

The response was:

[I]poor documentation - the driver does, indeed, work...
chip is chip -

on asus g2k series, debian, 2.6.23 kernel, fglrx 8.45.5 builds, loads, runs 3d[/I]

Unfortunately, this does not lessen my confusion as there is reference to procedures/terms with which I am not familiar  (e.g. headers, chip is chip) and again, there appears to be no resolution of the problem.

I have posted a request, similar as this one, on the PCLOS forum, but nobody has replied to it.  Perhaps Ubuntu, with its much larger user base and forum will be able to provide me with some assistance.

Any advice will be appreciated, greatly.  Thanks.

---

### Post by teaker1s on 2008-10-25
I have a hd2600 in a hp slim pc, at first I had issues with restricted driver first white screen(compriz) and freezing on screen saver- months ago.
latest update compriz/beryl work great and I've no nasty issues.


I personally prefer nvidia, but I must say the quality and reliability of the hd2600 is faultless so far

---

### Post by stephenj2008 on 2008-10-26
Thanks for your help teaker1s.

Is the graphics card an HD 2600 or a Mobility HD 2600?  I don't know if the HD 2600 is ever found in laptops - I've only seen laptops with the Mobility HD 2600 advertised.

I'd be greatful if you would tell me from where you got the driver - did you get it from the repositories?  What was the title/description of the driver?

Thanks again for you assistance.

---

### Post by teaker1s on 2008-10-26
I'm away from home, so I can't check-but my ati is hd2600 and not the mobility version. 
Hardy heron if you install restricted drivers under the restricted drivers tab. Installs latest ati restricted and catalyst control centre.

If you make sure you have latest kernel and then install restricted drivers it plays nice.
hope this helps

---

### Post by stephenj2008 on 2008-10-26
Hi again, teaker1s,

From what I have read on the net, it appears that there is a driver for the HD 2600 but not the Mobility HD 2600 (though, someone has disputed this as I outlined in my original post).

This is quite frustrating ... as I mentioned, many laptops currently come with the Mobility HD 2600.

I appreciate you help.

---

### Post by teaker1s on 2008-10-26
[http://www.cyberarmy.net/library/article/1777]("http://www.cyberarmy.net/library/article/1777")
ubuntu with fluxbox instead of gnome and ati hd2600 mobility, if restricted drivers don't work

---

