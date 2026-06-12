---
title: "using Thinkpad &quot;tablet&quot; with *-buntu"
date: 2010-02-10
forum: Hardware
---

### Post by SaintDanBert on 2010-02-10
Do you use a Thinkpad Tablet -- either the X61-tablet or the X200-tablet
-- or even one of the older but similar Thinkpad laptops with *-buntu?

What are you having trouble getting to work?

What do you have working? Will you share what you did in detail?

Are you happy with GNOME support for "tablet"? with KDE? other?

Have you found web links that solved some or all of your Thinkpad or tablet issues? Which links?

Here is a list of "features" that I want to address -- either they don't work at all, or I want better working. 
[list]
[*] Configure what happens when each of the "special keys" or "extra buttons" get pressed or released or held.
[*] Manually switch between "laptop mode" (landscape w/ keyboard & mouse) and "tablet mode" (portrait w/ stylus input & navigation)
[*] Detect orientation change between "laptop mode" and "tablet mode"
[*] Use external display from both laptop and tablet mode
[*] Use 3D-effects from both laptop and tablet mode
[*] Take full advantage of installed video card features
[*] View DVD-media or streaming video as both laptop and tablet
[*] Use the stylus as a mouse everywhere
[*] Use the stylus to create and capture "digital ink"
[*] Use the stylus to create and capture character data
[*] SLEEP or suspend-to-ram (power on but mostly idle) and resume
[*] HIBERNATE or suspend-to-disk (power off) and resume
[*] authenticate with fingerprint reader
[*] *Thinkpad* Undock and Dock the UltraBase docking station.
[*] *Thinkpad* Undock and Dock the docking station DVD or HDD.
[/list]
Some of these are Thinkpad specific. Others are "tablet pc" specific. Because I'm not sure of the solutions, I'll leave any designation until we discover what is going on. If I'm sure, I'll say so. Some of these require supporting applications in addition to more basic features.

Cheers,
~~~ 0;-Dan

_______________________________________
_**NOTES**_
[indent][i]
1. I know that there are other "tablet pc" devices in addition to the Thinkpad(tm) family. If you have something to add I'd like to hear from you, too, but please avoid hardware specific details unless you have Thinkpad details.
[/i][/indent]
[indent][i]
2. I know there is this whole ThinkWiki world for Thinkpad folks, but it has a close orbit around Washington state ... specifically, Redmond.
[/i][/indent]
[indent][i]
3. My original post will contain a list. I will update that list with what works for me as a separate posting.
[/i][/indent]
[indent][i]
4. I have asked the Ubuntu Forum folks about creation of a distinct sub-forum for "Tablet PC" details and issues. Please visit [http://ubuntuforums.org/showthread.php?t=1403615](http://ubuntuforums.org/showthread.php?t=1403615) to comment on this idea.
[/i][/indent]

---

### Post by Favux on 2010-02-11
Hi Dan,

> Manually switch between "laptop mode" (landscape w/ keyboard & mouse) and "tablet mode" (portrait w/ stylus input & navigation)
See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").
> Detect orientation change between "laptop mode" and "tablet mode"
Needs a switch in the hinge or somewhere that triggers an acpi event or an acpi extension like wmi event.
> Use the stylus as a mouse everywhere
I don't know what that means.
> Use the stylus to create and capture "digital ink"
Xournal is probably the best.  If you like Java you could try Jarnal.
> Use the stylus to create and capture character data
CellWriter.
> HIBERNATE or suspend-to-disk (power off) and resume
How big is your swap and RAM?  Make sure the swap is a least the size of RAM.  Sometimes 1.5 to 2x RAM is needed.
> authenticate with fingerprint reader
See:  [http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)  And the Thinkwiki site is probably better for you:  [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader)

Speaking of the Thinkwiki site I seem to remember a lot of your requests being addressed there.  Maybe not for your model or for Karmic?

I apologize if this is something you've already looked at and is too simplistic.

---

### Post by srilyk on 2010-02-21
There's also another program called cellwriter that allows tablet text input.

---

