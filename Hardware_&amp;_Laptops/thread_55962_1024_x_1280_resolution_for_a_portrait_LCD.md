---
title: "1024 x 1280 resolution for a portrait LCD?"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by qewl on 2005-08-10
Hi, I want to get the Samsung 193P. How can I get Ubuntu to display 1024 x 1280 portrait resolution? Any other info would also be appreciated. Thanks.

---

### Post by qewl on 2005-08-11
*bump*

Sorry, I don't mean to be redundant, but I would really appreciate if anyone could supply any info. Thanks  :)

---

### Post by WhiteZ on 2006-01-18
Browsing through the articles in here, no one has gotten it working, back to fedora then :(

---

### Post by Mr. Picklesworth on 2006-11-01
I'm bumping this, too...

Seems that there are a million threads about getting into Portrait mode, but no responses to any of them :(

It seems that playing with XOrg.conf and restarting the X server works, but it's a lot of trouble. Is there some way to change it on the fly?

Thanks in advance!

Edit:

Google gave me this:
[http://ask.slashdot.org/article.pl?sid=00/06/27/0248218](http://ask.slashdot.org/article.pl?sid=00/06/27/0248218)

The usual solution of changing XOrg.conf... it's a tad ugly, and not on the fly as one would hope, but it works for some people!

---

### Post by Mr. Picklesworth on 2006-11-01
Okay:
Firstly, Rotate does not work for me because I have an awful embedded video card. ( :( ). This may be the last straw to me replacing this awful computer and running Ubuntu on the hardware it deserves... next up is somehow moving all my data across computers.

However, it seems that after adding Rotate to xorg.conf, something wonderful happens!
A Rotate option appears in the Screen Resolution preferences :)

---

### Post by Graybeard on 2006-11-02
> **Mr. Picklesworth said:**
> Okay:
....However, it seems that after adding Rotate to xorg.conf, something wonderful happens!
A Rotate option appears in the Screen Resolution preferences :)

Picklesworth,

That will be great if it works on my system and I'm game to try but I'm a newbie and intimidated by xorg.conf. Can you post the section and subsection where "Rotate" should appear and how it should appear? Having looked at xorg.conf, I doubt that one can simply stick the word "Rotate" in just anyplace. A sample entry and where it should go would be great.

bob

Later:  With more impatience than caution I edited xorg.conf as follows:
Where it reads:

Section "Device"
Identifier  "NVDIA etc. etc."
Driver  "nv"
BusID  "PCI:1:0:0"

I added the line:

Option  "Rotate"

Rebooting, I still had landscape orientation and there were no new options in System>Preferences>Screen Resolution.

So I went back and added "CCW" after "Rotate"

Rebooting, I had PORTRAIT format. That's the upside.
On the downside, resolution reverted to maximum instead of the lower resolution that is easier for these old eyes to read, System>Preferences>Screen Resolution no longer allows me to change the resolution, and no new option appears for rotation. So at this point I have to choose between a resolution that is easier for me to read and the screen orientation that I prefer. And to make the choice I have to edit xorg.conf and reboot instead of making choices from System>Preferences on the fly. It's a tough choice.

bob

---

