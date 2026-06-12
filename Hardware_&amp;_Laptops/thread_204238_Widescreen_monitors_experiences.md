---
title: "Widescreen monitors experiences"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by Jeroenverh on 2006-06-26
Hellu Ubuntu users,

I'm thinking to buy a new widescreen monitor. I would like to know what the experiences are from you. 

[LIST]
[*]Which monitors works out-of-the-box? 
[*]Which monitor can you recommend? 
[*]What kind of problems can you expect?
[*]How difficult is it to setup such a new monitor?
[*]Is "sudo dpkg-reconfigure xserver-xorg" enough to change the resolution?
[/LIST]

I hope that the collected information is useful for everyone.

regards, Jeroenverh

---

### Post by ajifans on 2006-06-26
I haven't a vast amount of experience with loads of monitors, but haven't had any problems with my acer widescreen monitor on several distributions.

Most widescreen monitors should work 'plug and play'.  Worked for my acer, and also worked for my dad who plugs his computer into his widescreen HD LCD - no configuration needed; worked first time.

I just needed to run 'sudo dpkg-reconfigure xserver-xorg' in order to be able select my preferred resolution (1400*900).

Can't speak for all monitors, but it's not something I'd really worry about.

---

### Post by TD-Linux on 2006-06-26
I haven't ever run installed Ubuntu on a computer with a widescreen display, but I've used the Live CD on a widescreen laptop (WSXGA+, 1680x1050). Everything went very smoothly, and the configuration utility picked the full native resolution of the screen with no problems. Everything ran fine, including the cool screensavers, games that change the resolution like Enigma, and some 3D OpenGL games I tried.

Note that fullscreen games/programs that don't run at your monitor's resolution, or don't support a widescreen resolution, will stretch to fit. It's not a very bad effect at all, and you only usually notice it when looking at a top-down map or something else grid-oriented.

I replaced a non-widescreen CRT with a non-widescreen LCD, switching from the VGA port to the DVI port, and didn't have to change a thing, on Kubuntu Breezy Badger 5.10.

---

### Post by mrazster on 2006-06-27
I've been using [*_THIS_*](http://us.acer.com/acereuro/page4.do?sp=page3&dau22.oid=13843&UserCtxParam=0&GroupCtxParam=0&dctx1=25&CountryISOCtxParam=US&LanguageISOCtxParam=en&crc=1005280033) monitor for a while under both Suse,Fedora and different flavours of Ubuntu. Only when using K,X,Ubuntu it works right out of the box. I haven't had to do any other configuration than brightness and contrast.

I'm running the montior along with an nvidia card...have never tried it on a ATI card under linux...but I can't se how this should be a problem.

So as to your question about wich problem you should run inte ..I have no answer because I've never had any with this one.

About changing resolution a *"sudo dpkg-reconfigure xserver-xorg"* should be enough..just as you pointed out.

Only downside I can think of is that it doesn't work well in other resolutions than the native 192x1200....so when running games(wich it does very well) it puts a lot of pressure on the gfx card.
And the contrast ratio is so damn high...so when surfing in to a webpage for instance with a white bakground it's like getting a "flashbang" in counter strike.  :mrgreen: 

Other than that...I'm in love with it. ;)

---

### Post by Jeroenverh on 2006-06-27
Thanks for all the reply.
I have a much better feeling now and it is much more save than I thought.

Jeroenverh

---

