---
title: "Printing and printers printable area"
date: 2013-12-10
forum: Hardware
---

### Post by roofusthedoofus1 on 2013-12-10
Hello there everyone,

What i'm trying to do is simple and maybe there's a simple answer that i've overlooked, if i have i apologise.

I'm using Xubuntu 13.10.

Anyway - i'm trying to print out ASCII art using the full area of a page.  After tangling for days with the absolutely woeful Abiword i realised the problem has something to do with the printers i use, Canon IP4300 and IP5200, they leave three thin blank borders on the top, right and left and one thick border at the bottom.  you can see text has been cut off.  After not getting anywhere with Abiword, i tried to work on it as a PDF, but again to no avail...

I've messed with the printers themselves, changing things like 

-expand (to use maximum page area), 
-borderless (chose both yes and no), 
-changed the margins in job options to 0, 
-even something like media-bottom-margin in job options (i have no idea, but help is thin on the ground)

I have absolutely no idea what i'm doing wrong, but the printer refuses to print anywhere its decided margins are, despite there being none when i click on the printers properties.  

Any ideas?  i'd reall really appreciate some help....

---

### Post by tgalati4 on 2013-12-10
Some printers have a hard limit of 1/2" all around.  Others can print to "bleed" or right to the edge.  Others can bleed to one or two edges but leave 1/4" edge, which requires special paper with a tear-off strip, or you have to trim the paper.  How large are your minimum margins for your printers?

---

### Post by roofusthedoofus1 on 2013-12-18
Hi and thanks for your reply!

I'm fairly sure both the Canon ip5200 and ip4300 support borderless printing or full bleed as they say.  I've set the minimum margins on the printers to zero so everything should be setup up correctly.  It still doesn't work however.  The pages print out with 1/8" approx all round.  

I'm stumped...

---

### Post by tgalati4 on 2013-12-18
What paper size are you using?  A quick web search shows some conflicting information--the IP5200 can only print full bleed on letter size not legal size and that the printer enlarges the image slightly to achieve full bleed which causes some of the designed image to be cut off.  This is a problem with page layout and graphic design, but less of a problem with photographs.

What specific printer driver are you using in linux?  A work-around is to design your ASCII art to be slightly smaller and use a paper trimmer.  Sometimes you have to throw in the towel.

---

### Post by roofusthedoofus1 on 2013-12-18
Aha...

im using A4 (8.3 x 11.7) which should be okay then by width at least (since letter is 8.5 x 11).  

Interesting what you said about the printer enlarging the image a little resulting in the image being chopped slightly.  the printouts i'm getting have characters chopped all around 1/8", which makes me think its the driver (since it's not the word processor and the printer should be at least able to print full bleed width).  the drivers im using are from the gutenprint package, Canon PIXMA iP5200 - CUPS+Gutenprint v5.2.9 specifically.  

and you're right, sometimes you have to throw in the towel, it's just nagging me now as it would mean the process of printing out A4 sheets and putting them together to form large images would be sped up a lot...

anyway thanks a bunch for looking into it for me...

---

### Post by coldraven on 2013-12-18
I was trying to print the attached scale which fits easily within any margins on A4 but it kept printing smaller than it should. 
Obviously it should measure 10cm on the page. 
After much swearing I found the option in the printer driver settings "Shrink page if necessary to fit borders" and changed it to "Crop, preserve dimensions".
It then printed the scale exactly 10cm x 10cm.
This was using Epson Stylus Photo R300 - CUPS+Gutenprint v5.2.8-pre1 which should also be able to print borderless.
Does that help?

Edit: The original scale in svg format can be found here:
[http://openclipart.org/detail/97897/photomacrographic-scale-10x10cm-by-msevilla00](http://openclipart.org/detail/97897/photomacrographic-scale-10x10cm-by-msevilla00)

---

### Post by tgalati4 on 2013-12-18
If you are trying to paste several sheets together to make a large image, I have had good luck with *posterazor*.  

It's difficult to get perfect registration with printers.  There are a lot of variables involved.  All you can do is experiment and find a technique that works for you.  You will have to spend some time with all of the printer's settings and experiment.  As *coldraven* has pointed out, a simple setting such as "Crop, preserve dimensions" can make all of the difference.

Sometimes you can make some adjustments through the printer's front panel; they will interact with the linux printer driver in different ways.

A Haiku:

Registration off?
Experiment with settings.
Focus?  "Big Picture".

---

### Post by roofusthedoofus1 on 2013-12-19
well i gave it a shot with windows and it worked... i'll give all those  other suggestions a go in ubuntu and mess around and see what i can up  with.  Posterazor looks interesting i'll definitely give that one a  shot.

thanks a million to you both for your suggestions, i understand more now than i did at the start.  

excellent haiku! it'd make a great tattoo altogether

---

### Post by aikishugyo on 2013-12-22
Regarding borderless printing, this expands the image from what it naturally would be by some percentage so that it spills over the border---you will always lose some of the edges.
Now, for the Canon driver:
5.2.9 is much better than 5.2.8pre-1 (which after all is a pre-release for testing on MacOSX systems), so I won't speculate on what might be broken.
However, since I wrote the code for the borderless printing, I can tell you that it expands to the same overflow as the default Windows borderless. In the Windows driver, one can actually adjust this overflow to lose less or more of the photo (thereby wasting less or more ink, adjusting for paper feeding misalignments, etc.), but in the gutenprint driver this option does not currently exist.
Then, the printer firmware does not support borderless for all media types, and not all "resolutions" (a resolution is a particular inkset at a particular resolution intended for a particular media type).
In short, all photo media support borderless, plain media only supports borderless at a low resolution with a resolution mode made up of photo inks (no K, only k) which I think is not part of 5.2.8pre-1.
Other media, like envelope, T-shirt, HiRes paper, and FineArt paper do not support borderless at all in the firmware.
Currently, in 5.2.9, borderless support is complete for photo media and non-support for non-supported media is guaranteed (default mode for that media will be used) but borderless with plain mode (a kind of draft printing) is not properly supported (i.e., the mode either does not exist, or else if it does then there is no support for it being chosen automatically when borderless is selected).

---

### Post by tgalati4 on 2013-12-23
Excellent answer.  Thanks for  sharing.  If a printer could talk, then this is what it would say.

---

