---
title: "How I can install silverlight"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by chanfle on 2009-08-12
How i can view the sites with application silverlight, i installed the moonlight but not working on many sites with silverlight.
any tip?
thanks

---

### Post by 3rdalbum on 2009-08-12
Microsoft doesn't make Silverlight for anything except Windows and Mac OS X/Intel.

---

### Post by Sub101 on 2009-08-12
You might want to try the moonlight beta, which supports silverlight 2.0.

[http://go-mono.com/moonlight-preview/](http://go-mono.com/moonlight-preview/)

---

### Post by directhex on 2009-08-12
> **Sub101 said:**
> You might want to try the moonlight beta, which supports silverlight 2.0.

[http://go-mono.com/moonlight-preview/](http://go-mono.com/moonlight-preview/)

But be sure to remove ML 1.0 first!

---

### Post by chanfle on 2009-08-12
done...i install the new version
thanks

---

### Post by kolbiel on 2009-08-13
god damn silverlight! i cannot get this site working:

[http://www.itv.com/ITVPlayer/?intcmp=NAV_ITVPLAYE2](http://www.itv.com/ITVPlayer/?intcmp=NAV_ITVPLAYE2)

installed moonlight 1.0, tried moonlight 2.0 as well - none works.

---

### Post by directhex on 2009-08-13
> **kolbiel said:**
> god damn silverlight! i cannot get this site working:

[http://www.itv.com/ITVPlayer/?intcmp=NAV_ITVPLAYE2](http://www.itv.com/ITVPlayer/?intcmp=NAV_ITVPLAYE2)

installed moonlight 1.0, tried moonlight 2.0 as well - none works.

[http://www2.apebox.org/wordpress/rants/156/](http://www2.apebox.org/wordpress/rants/156/)

i.e. "soon"

---

### Post by directhex on 2009-08-18
> **kolbiel said:**
> god damn silverlight! i cannot get this site working:

[http://www.itv.com/ITVPlayer/?intcmp=NAV_ITVPLAYE2](http://www.itv.com/ITVPlayer/?intcmp=NAV_ITVPLAYE2)

installed moonlight 1.0, tried moonlight 2.0 as well - none works.

Moonlight Beta 1.1 released, fixes ITV Player: [http://go-mono.com/moonlight-beta/](http://go-mono.com/moonlight-beta/)

---

### Post by kolbiel on 2009-08-23
just checked Moonlight 2.0 Beta 1 - itv still DOES NOT work...

---

### Post by howefield on 2009-08-23
> **kolbiel said:**
> ....itv still DOES NOT work...

It does, obviously not for you, but it does work.

Keep at it.

---

### Post by directhex on 2009-08-23
> **kolbiel said:**
> just checked Moonlight 2.0 Beta 1 - itv still DOES NOT work...

Nicely done on ignoring the message directly above yours saying beta 1.1 is needed

---

### Post by kolbiel on 2009-08-24
sorry mate, obviously got overexcited... 

@ howefield: are you saying it works for you?

how's that then? do i need to wait for next beta, or there's something wrong with my firefox?

---

### Post by howefield on 2009-08-24
> **kolbiel said:**
> ...@ howefield: are you saying it works for you?

how's that then? do i need to wait for next beta, or there's something wrong with my firefox?

Yes, it works fine.

Had just installed a fresh system and forgotten to put this in, your post reminded me. No issues. I am using 64 bit, but wouldn't expect that to cause any issues either way.

[http://www.go-mono.com/moonlight-beta/Default.aspx](http://www.go-mono.com/moonlight-beta/Default.aspx)

---

### Post by kolbiel on 2009-08-27
moonlight 2 beta 2 released. itv still doesn't work for me though.... is it just me?

---

### Post by directhex on 2009-08-27
> **kolbiel said:**
> moonlight 2 beta 2 released. itv still doesn't work for me though.... is it just me?

Yes, it is.

[http://www.itv.com/ITVPlayer/Video/default.html?ViewType=5&Filter=46958](http://www.itv.com/ITVPlayer/Video/default.html?ViewType=5&Filter=46958) does nothing at all?

---

### Post by kolbiel on 2009-08-27
nothing mate....

[IMG]http://i27.tinypic.com/20ud6if.png[/IMG]

that's all there is....

---

### Post by directhex on 2009-08-27
> **kolbiel said:**
> nothing mate....

[IMG]http://i27.tinypic.com/20ud6if.png[/IMG]

that's all there is....

This may sound odd, but...

Do you have Picasa installed? Show me about:plugins

---

### Post by inobe on 2009-08-27
adblock and swf could aslo be responsible

---

### Post by kolbiel on 2009-08-28
don't use picasa.... switched adblock and flashblock off, didn't help....

about: plugins:
[IMG]http://i29.tinypic.com/2emzoxv.png[/IMG]
[IMG]http://i32.tinypic.com/1264riw.png[/IMG]

there's also quick time plugin and vlc one as well, and that's it.....

---

### Post by directhex on 2009-08-28
> **kolbiel said:**
> don't use picasa.... switched adblock and flashblock off, didn't help....

about: plugins:
[IMG]http://i29.tinypic.com/2emzoxv.png[/IMG]
[IMG]http://i32.tinypic.com/1264riw.png[/IMG]

there's also quick time plugin and vlc one as well, and that's it.....

Yeah, look at the list - the application/x-silverlight-2 MIME type has been claimed by libvlcplugin.so, so that's the lib being used to try and load Silverlight sites. Which obviously doesn't work.

File a bug.

---

### Post by directhex on 2009-08-28
> **directhex said:**
> Yeah, look at the list - the application/x-silverlight-2 MIME type has been claimed by libvlcplugin.so, so that's the lib being used to try and load Silverlight sites. Which obviously doesn't work.

File a bug.

Also, you need to uninstall the packaged version of moonlight or the XPI will crash your browser

---

### Post by kolbiel on 2009-08-28
didn't get all you wrote mate, but think i know what you ment. will try to file the bug.... sounds exciting....

---

### Post by webchimp on 2009-08-30
> **directhex said:**
> Moonlight Beta 1.1 released, fixes ITV Player: [http://go-mono.com/moonlight-beta/](http://go-mono.com/moonlight-beta/)


This worked for me after it prompted me to download the mwdia player codec  pack

---

### Post by kolbiel on 2009-09-07
ok, go on and call me names now - couldn't get to sending out the bug report.....

beta 3 is up - itv player still not working for me.

---

### Post by directhex on 2009-09-07
> **kolbiel said:**
> ok, go on and call me names now - couldn't get to sending out the bug report.....

beta 3 is up - itv player still not working for me.

Did you uninstall the VLC plugin yet, since it's the VLC plugin that's breaking it?

Moonlight is FINE, it's intentional (or inadvertent) breakage in the VLC plugin. The VLC plugin is claiming to your browser that it can open Silverlight content, and your browser is using the VLC plugin (not Moonlight) on ITV.com. Since VLC can't load Silverlight content, nothing is being displayed.

Moonlight has been fine for ITV since Beta 1.1. You have a VLC plugin problem.

---

### Post by kolbiel on 2009-09-07
directhex, you're my guru! absolutely right. removed the vlc plugin, installed moonlight beta3, then some codec pack and itv works like charm...

thanks, mate.

---

