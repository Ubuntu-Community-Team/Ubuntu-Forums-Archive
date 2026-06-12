---
title: "installing Brother DCP-7040 under Ubuntu 12.04"
date: 2013-06-13
forum: Hardware
---

### Post by gleedadswell on 2013-06-13
Hi everyone,

I've installed this printer under a variety of other Ubuntu versions, but it went somewhat differently this time so I thought I'd post on it in case others encounter the same issues.  I've previously posted on it here:

 [http://ubuntuforums.org/showthread.php?t=1124867&page=2](http://ubuntuforums.org/showthread.php?t=1124867&page=2)

That time I used the "Brother DCP-7020 Foomatic/hl1250" driver which comes in the brother-lpr-drivers-laser package that is available from the repository.  Note that I did not use the drivers from the Brother site.  I've had little luck with them in the past.

This time (same computer, same printer, but running 12.04 now) that driver produced the common problem of little black rectangles on the descenders from letters from "p" and "g" when printing from a wordprocessor.  Interestingly there were also problems with descenders from letters in a .png file, which surprised me.  The economy printing setting was off.

I switched to the "Brother DCP7020 for CUPS" driver and the problem went away immediately.  Cheers![COLOR=#000000]
[/COLOR]

---

### Post by gleedadswell on 2013-06-17
OK, I **thought** that everything was working but then when I printed from LibreOffice and from a pdf viewer I found that the margins were messed up.  The print area was shifted down on the page.

I tried following 

[http://ubuntuforums.org/showthread.php?t=1450999](http://ubuntuforums.org/showthread.php?t=1450999)

but no luck (but note that it is a 3 year old post).  After trying a number of things I decided to try directly modifying the .ppd file.  This was one of those useful learning experiences which (after the initial frustration) reminded me of why I love linux so much.  I've had a problem like this under Windows and there was simply nothing I could do to fix it.  Here the solution involved getting my hands dirty, but it was doable.  Here's what I did:

In a terminal I did

```
sudo -i
```

Then I used locate to find where the .ppd files were.  The Brother ones turned out to be in /usr/share/ppd/Brother.  So I went there and did

```
cp DCP_7020.ppd DCP_7020_mine.ppd
gedit DCP_7020_mine.ppd
```

Somewhat down the page was 

```

*DefaultImageableArea: A4
*ImageableArea Letter/Letter: "18 12 594 780"

...
...
*DefaultPaperDimension: A4
*PaperDimension Letter/Letter: "612 792"
...

```

No idea why the defaults are A4 (is Brother a European company?).  Anyway I changed all the defaults to Letter, but that didn't fix everything.  I then fiddled with the  *ImageableArea Letter/Letter and *PaperDimension Letter/Letter settings.  Apparently 612X792 is what the paper dimensions *should* be for Letter.  But I had to change both the paper dimension and image area to get good results.  The image area is in the format

```

*ImageableArea Letter/Letter: "llx lly urx ury"

```

That is, it gives x and y coordinates for the lower left and upper right corner of the image area.  So I changed the values, saved the ppd and then reinstalled the printer using the new ppd (I just used the Printers item from the System Settings).  Then I printed a test page.  I repeated this loop until the whole outer box in the test page was visible.  In the end, for this printer what worked for me was

```
*DefaultImageableArea: Letter
*ImageableArea Letter/Letter: "20 60 575 790"
...
*DefaultPaperDimension: Letter
*PaperDimension Letter/Letter: "612 842"

```

I have no idea why I needed the paper dimension to be "wrong" for Letter, but this works.  I expect results may vary.  But this sort of problem seems to plague Brother printers so hopefully this general procedure will be useful to other people.

Cheers!

---

### Post by user_of_gnomes on 2013-06-17
> No idea why the defaults are A4 (is Brother a European company?).


Brother Industries is actually a Japanese company. The Japanese have their own unit measurements but they do use A-formats for paper.

---

