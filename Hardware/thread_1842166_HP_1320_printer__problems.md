---
title: "HP 1320 printer  problems"
date: 2011-09-10
forum: Hardware
---

### Post by HR70s on 2011-09-10
[U]Installed 11.04 last week every thing was working great . 3 days later I can't print from the internet
using firefox   Went and tried test on printer every thing ok. test page ok  What happens now is I will
 hit print the green light on my printer starts indicating ready to print but the print stays pendind or will
print after a minute or so or doesnt at all.
    If I copy and paste from the internet to Libbre office my printer spits it right out
:confused:
[/U]

---

### Post by foresthill on 2011-09-10
Printing is one of several major things f'ed up about 11.04. You'll have the same problem if you try to print any PDF files. One page might take literally a half hour to print.

I have an HP 1320 that I use daily, and can't afford these kind of headaches. So that's why I run 10.10, and will continue to do so until these problems are straightened out.

---

### Post by HR70s on 2011-09-11
Hey thanks, Not what I wanted to here but oh well . Life is like a box of chocolates

---

### Post by BigJules on 2011-09-11
Hey - I'm running a 1320 on 11.04 and its never missed a beat! So good I've made it default printer on the network.

I use the 'HP LaserJet 1320 series Postscript (recommended)' default driver and never a bit of grief. System is vanilla PC and Natty Unity (luv it), all updates done, FFox 6.0, can't see what the fuss is about...

---

### Post by foresthill on 2011-09-12
I'm sure that setup works fine for text files, but have you tried printing out any PDF files? How long do they take?

PDF's are all I ever print, so it's important that they not take 1/2 hour per page.

---

### Post by BigJules on 2011-09-13
Yes, pdf ok - slow, but this is because pdf is essentially like a graphic and requires much more memory in the 1320 itself than comes as standard. As I don't often print pdf's I can't be bothered to shell out for more. If you're doing a lot, suggest u get some from HP and fit it. Nothing to do with Ubuntu.

---

### Post by foresthill on 2011-09-13
In 10.10, using a certain program called XPDF, I can get PDF's to print in about 10 seconds on my HP 1320 Laserjet printer. 

The problem seems to be with the Image Viewer program that opens PDF's by default. It processes PDF files for printing extremely slow, no matter with version of Ubuntu I use. 

The workaround I have used in the past is to print PDF files with the program XPDF. The problem is that XPDF instantly crashes when I open it in 11.04, so I'm forced to use the Image Viewer program to print PDF files. Which takes 20 to 30 minutes to print a single page.

So that's why I have been forced to stick with 10.10 for now. YMMV.

---

### Post by BigJules on 2011-09-13
Can certainly confirm the xpdf segmentation fault crash in Natty. There must be other pdf print programs out there...? 

If it's a spool problem more printer memory should fix.

---

### Post by HR70s on 2011-09-15
I got 10.10 on a live flashdrive plugged it in and it runs good. As you have the same printer as I do I need to know where
to get the driver. With 11.04 it automatically configured  it for me. .

---

### Post by HR70s on 2011-09-15
Just an update on hp 1320 not printing in 11.04.
I went into system settings/ printing/ preferences  highlighted in the list HP 1320 then picked [recommended]
HP  laserjet -cups+gutenburg v5.2.6 simplified [ EN] 
The printer now prints anything PDF ,Text, doesn't matter and prints quick! 
oringinally the configuration was HP 1320 post script . which on the list was also recommended
    Hope this helps others.
  By the way I have a simple duel core Itell 3.0 GHZ
Duel boot off 500 harddrive with windows vista 2007 partitian split down the middle 250/250

---

### Post by foresthill on 2011-09-16
> Just an update on hp 1320 not printing in 11.04.
I went into system settings/ printing/ preferences highlighted in the list HP 1320 then picked [recommended]
HP laserjet -cups+gutenburg v5.2.6 simplified [ EN]
The printer now prints anything PDF ,Text, doesn't matter and prints quick!
oringinally the configuration was HP 1320 post script . which on the list was also recommended
Hope this helps others.
By the way I have a simple duel core Itell 3.0 GHZ
Duel boot off 500 harddrive with windows vista 2007 partitian split down the middle 250/250

Hey, this actually worked. Thanks HR70s. 

Now if I can get rid of that pesky black screen in 11.04 I might finally be able to migrate over.

---

### Post by HR70s on 2011-09-16
If you are talking about your desktop background ? Or print background?
                                                                                   HR

---

### Post by foresthill on 2011-09-16
Nope, I meant this:

[http://ubuntuforums.org/showthread.php?t=1741556](http://ubuntuforums.org/showthread.php?t=1741556)

Thanks again.

---

### Post by HR70s on 2011-09-18
I don't have an answer. But for me I use the remix it's a light weight program is plenty for me it's fast, does everything
I need with no grief . What I am saying is do you really need 11.04 . I have a Dell laptop. Most of what I do is text.
and browsing and Email { Thunderbird}  My PC as you know I use 11.04
                                                                                                    Good luck
                                                                                                    HR

---

