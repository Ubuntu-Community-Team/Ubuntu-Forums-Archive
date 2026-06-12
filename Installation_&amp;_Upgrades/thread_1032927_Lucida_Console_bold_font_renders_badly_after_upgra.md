---
title: "Lucida Console bold font renders badly after upgrade to intrepid"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by foresto on 2009-01-06
I use Lucida Console 9 (a Microsoft TrueType font) as my terminal font. It worked great in Hardy, but after upgrading to Intrepid, bold rendering looks awful, as if the bytecode hinter has gone haywire. This is puzzling because the other TrueType fonts I have tried look fine, as does non-bold Lucida Console. I am attaching screen shots to demonstrate the difference between hardy and intrepid.

My font settings:
  Anti-aliasing is disabled.
  Hinting is set to Full.
  Sub-pixel hinting is disabled.

(All these are set in the xfce User Interface Preferences. I normally use xfce, but the same problem is visible when I log in using gnome.)

Can anyone tell me how to fix it, or at least explain the change in behavior?

Bug filed here:  
[https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/314555](https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/314555)

(Bad) Intrepid screen shot:
[IMG]http://launchpadlibrarian.net/20991336/lucida-console-2-intrepid.png[/IMG]

(Good) Hardy screen shot:
[IMG]http://launchpadlibrarian.net/20991344/lucida-console-2-hardy.png[/IMG]

---

### Post by foresto on 2009-01-07
I just added screen shots.

I tried running dpkg-reconfigure fontconfig-config, which showed that the settings were already correct, and changing them didn't fix the problem.

---

### Post by foresto on 2009-01-13
The same problem exists with Andale Mono, which is another monospaced TrueType font, also from Microsoft.

---

### Post by juamez. on 2009-05-28
I see you filed this as a bug here [https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/314555](https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/314555)

There is a proposed solution mentioned in the bugtracker, did you try it yet? I just installed all fontconfig packages and dependencies from the jaunty repo on an intrepid installation. I'm sorry to say that Lucida Console in "bold" looks exactly as ugly as before.

I kind of hate it too, because Lucida Console is quite a readable font, especially at lower font sizes. I like it more than Monospace 8pt to use as a text editor font, because it is very clear to me and fits more lines in height on the screen.

Anyway, can you tell me what your status of this issue is? Maybe we can figure it out.

---

### Post by foresto on 2009-05-28
It looks like these fonts render correctly in a terminal window as of Jaunty, but they're still wrong everywhere else (including the font picker).

---

### Post by juamez. on 2009-05-28
I'm using Lucida Console at Full Hinting and Subpixels Smoothing, which makes Lucida Console at bold weight look very fuzzy. It looks like a font that does not support the current font hinting setting, just like when you use Freesans at full/medium hinting instead of slight - at which it looks like how it is intended.

My thought was that Lucida Console (Bold) might have another optimal hinting setting, but so far every possible variation in font settings proved to bring no improvement. That is very weird.

---

### Post by foresto on 2009-05-28
Lucida Console and the other MS Core Fonts include proper TrueType hints, intended for use with proper TrueType hinting, otherwise known as bytecode interpreter hinting.  Many linux distributions disable freetype's bytecode hinting due to fear of patent infringement.

[http://www.freetype.org/patents.html](http://www.freetype.org/patents.html)

In order to make up for the disabled hinting features, the community has been relying on various hacks (e.g. the freetype autohinter) to approximate proper hinting.  As a side-effect, many free fonts have been developed without hinting data at all, optimizing for the autohinter instead.  They generally don't look as good as properly hinted fonts when rendered with the bytecode hinter, but they look better than having no hinter at all.  Anti-aliasing helps hide the warts a bit.

However, some of us actually use properly hinted fonts (e.g. Lucida Console) on distributions with the bytecode hinter enabled (e.g. Ubuntu).  A few of us also disable anti-aliasing because it makes text look blurry.  The result is very clean, crisp text even at smallish point sizes.

Unless, of course, something erroneously disables the bytecode hinter, as seems to be happening here for certain fonts.  :(

---

### Post by juamez. on 2009-06-17
Any progress?

Are you aware of the faulty rendering of the embedded bitmap thingies inside the new MS Office 2007 fonts? There is a lot to be found on the internet. The way I fixed it was adding this to my ~/.fonts.conf:

```
 <match target="font" >
  <test compare="eq" name="family" qual="any" >
   <string>Calibri</string>
   <string>Cambria</string>
   <string>Candara</string>
   <string>Corbel</string>
   <string>Constantia</string>
   <string>Consolas</string>
  </test>
  <edit mode="assign" name="embeddedbitmap" >
   <bool>false</bool>
  </edit>
 </match>
```

This does not help for Lucida Console, though.

---

