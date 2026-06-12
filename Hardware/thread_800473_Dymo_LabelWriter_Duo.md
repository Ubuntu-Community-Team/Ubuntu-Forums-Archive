---
title: "Dymo LabelWriter Duo"
date: 2008-05-19
forum: Hardware
---

### Post by Keith_Beef on 2008-05-19
I'm trying to get this printer, also known as an LW400, to work fully. so far, I've got the label part working, but not the self-adhesive tape part.

Trying to get my Labelwriter 400 to work, I stumbled upon this page:
[http://forums.freestandards.org/read.php?33,120](http://forums.freestandards.org/read.php?33,120)

So I started the Cups admin web tool, and began adding a printer.

I give it a name, location and description, then get to choose a device...

Here are the options that I can choose from:

```
AppSocket/HP JetDirect 
Backend Error Handler 
DYMO LabelWriter DUO Label (DYMO LabelWriter DUO Label)
DYMO LabelWriter DUO Label USB #2 (DYMO LabelWriter DUO Label)
DYMO LabelWriter DUO Tape 128 (DYMO LabelWriter DUO Tape 128)
DYMO LabelWriter DUO Tape 128 USB #3 (DYMO LabelWriter DUO Tape 128)
EPSON Stylus Photo 890 (EPSON Stylus Photo 890)
EPSON Stylus Photo 890 USB #1 (EPSON Stylus Photo 890)
Gutenprint USB Printer #1 (EPSON USB Printer)
HP Fax (HPLIP) 
HP Printer (HPLIP) 
Internet Printing Protocol (http) 
Internet Printing Protocol (ipp) 
LPD/LPR Host or Printer 
LPT #1 
Print into PDF file (Generic PDF file generator)
SCSI Printer 
Windows Printer via SAMBA 
```

So I choose the first option:
```
DYMO LabelWriter DUO Label (DYMO LabelWriter DUO Label)
```

Now, I can choose a PPD, but the only one proposed is:
```
Dymo Label Printer, 1.3 (en,da,de,es,fi,fr,it,ja,ko,no,pt,pt_PT,sv,zh,zh_TW)
```

which is the file:
```
lsb/usr/cups-included/Dymo/dymo.ppd
```

In a terminal window, I look to see if there are any other PPD files:
```
$ locate dymo
/usr/lib/cups/filter/rastertodymo
/usr/share/ppd/cups-included/Dymo/dymo.ppd
```

Hmm... I'm not sure why I have a path starting simple lsb/. Maybe Cups adds a prefix to this, or substitutes /usr/share/ppd/ in place of lsb/usr/ in the path.

Whatever, I'll try the option; I can always come back and browse to the file I've found, if the first doesn't work.

I'm prompted for a login and password, so I give root.

Now I get some set-up options for print jobs. I leave the defaults of:
```
Media Size: Address - 1 1/8x3 1/2in
Resolution: 300dpi
Darkness: Normal
```

No banners, and policies are:
```
Error Policy: retry-job
Operation Policy: default
```

I get a message: "Printer DLW400_L has been configured successfully." Looks good.

So I try a test page, and I get a diddy little label, with rulers along the edges, and some tiny text.
The text doesn't quite line up inside the boxes, and doesn't quite fit on the paper, but otherwise it looks perfect!

Now to try in glabels!

I define a label size, make a simple address label and send the job to DLW400_L and it works!

Now for the tapes, that come out of the front of the printer...

I've rebooted since setting up the label printer, so I start up the Cups admin tool again, and look at which printers are available.

I see the print queue named DLW400_L that I set up earlier in the day, then I see another, named LabelWriter_DUO_Tape_128 that seems to have been added "automagically".

If I try to print a test page to this printer, however, I get an error message:
```
Unsupported format 'application/postscript'!
```

Hmm... maybe I should delete that queue. I'll see what happens when I add a queue for tapes.

Back to the Admin tab, and Add Printer.
I go through the same steps as for the label printing, but with a few changes.

Of course, this queue has a different name: DLW400_T.

For device, I choose the option:
```
DYMO LabelWriter DUO Tape 128 (DYMO LabelWriter DUO Tape 128)
```

When defining the label queue, I had the choice of these two:
```
DYMO LabelWriter DUO Label (DYMO LabelWriter DUO Label)
DYMO LabelWriter DUO Label USB #2 (DYMO LabelWriter DUO Label)
```

I chose the option without USB #2 in the string. So this time around, faced with these two options:
```
DYMO LabelWriter DUO Tape 128 (DYMO LabelWriter DUO Tape 128)
DYMO LabelWriter DUO Tape 128 USB #3 (DYMO LabelWriter DUO Tape 128)
```
I again choose the option without USB #3 in the string.I don't know what difference this makes...

Choosing the PPD, I get the same single propostion as before; namely:
```
Dymo Label Printer, 1.3 (en,da,de,es,fi,fr,it,ja,ko,no,pt,pt_PT,sv,zh,zh_TW)
```

This worked for labels, so I'll keep it.
Give the root password, and set some final parameters... or not.

For Media Size my choice is limited, and does not include the 1/2" D1 cassette...

Maybe I can tweak the media size later, so I'mm leave the parameters as default:
```
Media Size: Address - 1 1/8x3 1/2in
Resolution: 300dpi
Darkness: Normal
```

No banners, and policies are:
```
Error Policy: retry-job
Operation Policy: default
```

So, I finish adding this printer, then look at the list of printers available. I see my latest addition, and no "automagic" additions (i.e., other than "LabelWriter_DUO_Tape_128").

I try tweaking the media size for the new queue...
Modify printer doesn't have any settings for media size.
Set Printer Options just has the same list of media sizes as before.

Maybe I can just set a template in glabels to make sure I don't print over the edges of the tape...
So I make a template that's 12.7mm wide, and draw up a label, that I send to the DLW400_T print queue. And nothing happens.

Well, there's a job in the queue, processing, but nothing much is happening. After an hour, nothing comes out of the printer. Sending the job to "LabelWriter_DUO_Tape_128" gets no result, either.

Has anybody here had any success at getting the second part of this printer to work?

K.

---

### Post by Arooo on 2008-11-17
Hi Keith,
xcuse me for waking up this quite old topic but ...

... I just wondered if you ever found/obtained a solution to this problem ? I did folow exactly the same path, and had exactly the same problem, label part is okay, but can't figure out a way to get the tape part running, the queue still ending in "printer busy; next try by 5 s" (well ... in french on my machine ...)

Thx ;)

---

### Post by Keith_Beef on 2008-11-23
> **Arooo said:**
> Hi Keith,
xcuse me for waking up this quite old topic but ...
Pas de problème, Aroo. 

> **Arooo said:**
> ... I just wondered if you ever found/obtained a solution to this problem ? I did folow exactly the same path, and had exactly the same problem, label part is okay, but can't figure out a way to get the tape part running, the queue still ending in "printer busy; next try by 5 s" (well ... in french on my machine ...)

Thx ;)

No, I still cannot print onto tape... but since I upgraded to 8.10 (Intrepid Ibex) I have been busy
[LIST]
[*]fixing the problem of no sound (fixed tonight)
[*]trying to make a Streamzap controller to work with media applications
[*]trying to get bluetooth to bind to a GPS receiver.
[/LIST]

So I have not spent any time on the Label printer for several weeks.

I'll keep trying whenever I have time, and I'll come back to this thread to post anything that I learn.

K.

---

### Post by Arooo on 2008-11-25
> **Keith_Beef said:**
> Pas de problème, Aroo. 

;) 

> **Keith_Beef said:**
> No, I still cannot print onto tape... but since I upgraded to 8.10 (Intrepid Ibex) I have been busy
<...>
So I have not spent any time on the Label printer for several weeks.

I'll keep trying whenever I have time, and I'll come back to this thread to post anything that I learn.

K.


'kay :) thanks anyway, I also spent much of my time *not* trying anything that way. Be sure I'll post any clue I'll get.

---

### Post by HeinBehrens on 2010-06-15
[http://sites.dymo.com/Support/Pages/AllDriversUsers.aspx?Type=Drivers](http://sites.dymo.com/Support/Pages/AllDriversUsers.aspx?Type=Drivers)

downloaded the linux sdk.

Followed the instructions in the forum and it works for me under cups on ubuntu server amd64 10.04

with a dymowriter 400.

---

