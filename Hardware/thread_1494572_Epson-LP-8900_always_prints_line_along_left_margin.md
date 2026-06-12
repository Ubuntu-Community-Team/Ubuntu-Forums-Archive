---
title: "Epson-LP-8900 always prints line along left margin"
date: 2010-05-27
forum: Hardware
---

### Post by NeverSage on 2010-05-27
Hello,

I've recently been having a problem while using Ubuntu 10.04 where my  Epson-LP-8900 printer will print a line along the left margin.  It is  perfectly one pixel wide which leads me to believe it's a software, not  physical, problem.  This always happens regardless of program and  format, .docs, .pdfs, etc.  Printing a test page yields the same  results.  This does not happen while printing from other OSs.  The  strange thing is that it was working fine under 10.04 for weeks and I  can't think of anything I did to change that. 

The printer is over a network, if that matters.  Also I'm running CUPS  1.4.3.  Any help would be very much appreciated!  Right now I use white  out on the line and then photocopy the page... obviously a big pain.

Thanks!

---

### Post by dino99 on 2010-05-27
try to remove/purge then reinstall the driver

---

### Post by ajgreeny on 2010-05-27
There have been several upgrades to a variety of cups packages over the lsat couple of weeks so perhaps that has a bearing on the problem.

As dino says, a purge and reinstall of cups or other print drivers may help.

---

### Post by NeverSage on 2010-06-01
Thanks guys,

Using Synaptic I did a complete uninstall of cups.  I reinstalled cups as well as foomatic-db which I found I need to have in order to be able to print at all.  I have to admit I don't completely understand but without foomatic my printer driver doesn't even show up when installing the printer.  

After this the line is still there though, sadly.  I don't know if this is an updated cups problem or an updated foomatic problem.  If there are any more suggestions I'm willing to give them a try!

---

### Post by NeverSage on 2010-06-02
Sorry, I just noticed something.  The line only occurs when there are graphics on the page.  PDFs always have it but word documents don't if they're just text.  I'm not sure what that means though...

---

### Post by NeverSage on 2010-06-08
I noticed something else very strange.  I opened up a word document  created in Microsoft word in OpenOffice3.2.  The document contained text  and images.  I printed and there was no line along the left side.  I  added an additional image (insert>picture>from file).  When I  printed that the line was there. I really can't figure out what would  cause that to happen.

---

### Post by NeverSage on 2010-06-22
I'm still hoping someone can help me.  I just upgraded to the newest  cups release, 1.4.3-1ubuntu1.2.  The line remains.  I had to buy more  white-out to keep up with all the lines I'm covering up :-/.

---

### Post by NeverSage on 2010-08-27
I reinstalled Ubuntu 10.04 and am still having this issue.  Anyone have any ideas?

---

### Post by NeverSage on 2010-09-14
First I should mention that I'm the only one who runs Linux in my office  and also the only one with this issue, so it's unlikely to be hardware  related.

My office has a different printer of the same make and model.  I tried  printing to that instead and still received the line down the left side.   This means it's unlikely to be a specific problem with the printer and  more with how CUPS or foomatic-db (though I'm still unclear as to what  that is exactly) interacts with this model.  If anyone has any  suggestions on how to fix this, or other resources I should explore,  please let me know.

---

### Post by NeverSage on 2010-09-21
Problem solved.  We got a new printer.  What I learned from this experience is don't use old, obscure ones.

---

