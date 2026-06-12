---
title: "Firefox fonts stink"
date: 2008-07-18
forum: General Help
---

### Post by Footer on 2008-07-18
Check out the attached images of Firefox 3.0 and Konqueror 3.5.9.  Konq. is nice and smooth but FF is almost unreadable (especially the bold text).  I have not done any tweaking with anti-aliasing or anything else at the browser level.  I'd prefer to use FF but if I can't get the fonts to look like Konqueror, I guess I'll switch.

Any suggestions?

Thanks!

---

### Post by coffeecat on 2008-07-18
Yes, that is pretty bad. I'll tell you what I do. Install msttcorefonts and then in Firefox Edit > Preferences > Content, click the Advanced button for Fonts and Colours, choose Verdana for Sans Serif and Sans Serif for Proportional. OK that and restart Firefox.

You can then tweak anti-aliasing if you want. This next a matter of personal preference, but I prefer autohinting to be on (this is different from anti-aliasing). It improves font rendering in all apps as well as the desktop generally. If you want try try it, in a terminal:

```
sudo dpkg-reconfigure fontconfig-config
```Choose autohinter in the first and the defaults in the second. Restart the X-server. If you don't like autohinting, just run the command again and choose Native.

---

### Post by Footer on 2008-07-18
Thank you for the prompt response!  I have the newest version of msttcorefonts installed.  My browser advanced font settings were:

[INDENT]Proportional --> Serif
Sans-serif --> sans-serif[/INDENT]

Trying to compare 'apples to apples', I looked at the Konqueror settings which were basically the same.  I tried the settings you suggested but it didn't make any difference.

Then I tried the autohinter which definitely helped (see attached) but I don't really want my entire desktop affected ...

The funny thing is, most other web pages look fine.  Maybe it's just the Linux Journal site?  I guess maybe for now, I'll just look at Linux Journal in Konqueror.  :)

Thanks!

---

### Post by coffeecat on 2008-07-18
> **Footer said:**
> Maybe it's just the Linux Journal site?

That's a thought. Perhaps the Linux Journal site is specifying a font that handles badly in FF. I'm a bit hazy about HTML and CSS and all that stuff (that is the understatement of the century :lol: ) but I think those font settings in FF only affect web-pages where the font isn't specified. You'd have to inspect the page source coding to see what font Linux Journal is specifying, if any. But don't ask me where! :wink:

> **Footer said:**
> Maybe it's just the Linux Journal site?

For a long time Linux had a reputation for grotty font-rendering. Perhaps Linux Journal is simply respecting tradition. :neutral:

---

### Post by coffeecat on 2008-07-18
I forgot to look at your screenshot before posting. That's still bad even with autohinting. Out of interest, here's my screenshot of the same website. I'm using Ubuntu/Gnome and it seems much better. What do you think?

---

### Post by Footer on 2008-07-18
I think I agree, yours look 1000X better.  :)  Very smooth.  So you have autohinting enabled?  I've never been a big fan of the anti-aliasing stuff and prefer to leave it disabled.  To me, even though it's smooth and sweet looking, I prefer a bit 'crisper' fonts.  In other words, the autohinting/anti-aliasing stuff tends to look a bit fuzzy to me (maybe it's my aging eyes).

As for Gnome, well, I've been using KDE for years and really don't plan to change.  And you make an interesting point about Linux Journal, maybe they are respecting tradition!  Seriously, most other sites look just fine in FF3.0 so maybe I shouldn't complain and just leave well enough alone.

But I do agree with you, I've been using Linux since the late 90s, and desktop Linux daily for more than 3 years now (Kubuntu specifically).  I've lived through the crappy fonts and tweaked for hours.  It's just sort of sad that there are still these issues lurking.  It is my hope that this does not happen to someone first trying out Linux and throwing in the towel because the fonts just plain stink.  :(

So anyway, I'll get off my soap box and go lay by my dish now.  Thanks for your responses.  I'd love to banter on about Flash as well but that's for another day, another thread.

:)

---

### Post by coffeecat on 2008-07-18
> **Footer said:**
> I've lived through the crappy fonts and tweaked for hours.  It's just sort of sad that there are still these issues lurking.  It is my hope that this does not happen to someone first trying out Linux and throwing in the towel because the fonts just plain stink.  :(

Well - you've been using Linux a lot longer than me. I could be wrong - you may know better than me - but I think a lot of the technology to get better font rendering is software-patented. Bits by Apple and bits by M$ iirc. That's why it's difficult to get really good font-rendering as default in Linux. I believe autohinting uses some of these patents but as I live in the UK I can switch it on without any fear of patent lawyers knocking on my door in the early hours.

But that might not stop the FSF people objecting. Imagine - Richard Stallman calling at 3.00 am. Scary! :(

---

### Post by Footer on 2008-07-18
You are correct, M$FT and Apple are probably the biggest reasons we have these font issues.  And unfortunately, it's still mostly a M$FT, closed source world we live in ... but thankfully, it's changing slowly but surely.  :)

Flash is another thing that is really suffering.  Too bad nearly every web site now uses it but on the Linux side, we are at Adobe's mercy and they don't seem too keen on opening it up though at least they're releasing versions specific to Linux now ...

Oh well, we just have to continue to plug along as best we can.  I'm amazed at how far Linux has come just in the past few years and truly hope it continues to gain popularity.

---

