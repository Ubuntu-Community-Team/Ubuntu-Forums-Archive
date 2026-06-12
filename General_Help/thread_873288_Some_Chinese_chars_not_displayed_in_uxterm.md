---
title: "Some Chinese chars not displayed in uxterm"
date: 2008-07-28
forum: General Help
---

### Post by John Chambers on 2008-07-28
I installed Chinese and Japanese fonts, and tried using vim with a few files that contain Chinese text.  The weird thing is that most of the Chinese characters display correctly, and around 1/3 of them don't. Even some very common chars, such as ni3 (you) show as an empty rectangle.

Some other tools, such as firefox and gnome-text-editor display all the Chinese text correctly.  I tried xterm and uxterm, and they both failed for the same characters.

I searched these forums, and did a bit of googling, but didn't find anything that helped.  Anyone know about this problem?  Is it documented somewhere?

---

### Post by John Chambers on 2008-07-29
I just discovered an even more bizarre behavior in (u)xterm with Chinese and Arabic text.  I have a test file that contains both languages and English.  When I use CTL+right button to get the Unicode Fonts menu, and change the size to anything less than Large, I see the same behavior, with some Chinese and all Arabic chars shown as rectangles.  But when I set the size to Large, all the Chinese characters appear correctly, though the Arabic is still little rectangles.

The fun part is when I set the size to Huge.  Then all the Chinese chars show as little rectangles, but the Arabic appears as Arabic characters.  However, they are all the isolated form - and they're drawn left-to-right!

So Arabic text is only rendered at a Huge size, and is drawn totally incorrectly (but with recognizable glyphs).  Chinese is rendered correctly only at Large size, is partly correct at some small sizes, and is entirely unrendered at Huge and Medium sizes.

Since Chinese is rendered correctly at one font size, it looks like uxterm has the ability to draw Chinese chars correctly, but there's something screwy going on that has to do with font size.  It's weird that Chinese isn't rendered at all at the Huge size.

Anyone know where I might go from here?  Is anyone successfully using Chinese in uxterm on Ubuntu Hardy?

And what's with the left-to-right Arabic?

---

### Post by hansdown on 2008-07-29
Hi John Chambers. I don't know if this helps, but...  I have found that GNU Unifont works pretty well for X, and for apps that
need TTF, Cyberbit is adequate enough.
(Cyberbit is not included in Debian, as far as licensing goes.)

I too have noticed that xterm/uxterm are missing some Chinese
characters; the fix for this is to Ctrl-Right-Click within the xterm
window to bring up the fonts menu. (Change it to "large")

I cannot speak for the rest of X, unfortunately, but on the console side
I can launch to jfbterm -q -c other,GB2312,iconv,UTF-8 to view Chinese text.
I use system-wide UTF-8 for everything since it "just works" with
Japanese and Korean.

If you need to input Chinese in the console, zhcon would work. If I'm
not mistaken, both of these apps utilize GNU Unifont, and so can X apps.

If you copy and paste your post topic you can see some interesting stuff.

---

### Post by lanruisen on 2009-01-20
[http://www.debian.org.tw/index.php/scim](http://www.debian.org.tw/index.php/scim)

[http://ubuntuforums.org/showthread.php?t=528382](http://ubuntuforums.org/showthread.php?t=528382)

These two threads got my Chinese working very well

---

