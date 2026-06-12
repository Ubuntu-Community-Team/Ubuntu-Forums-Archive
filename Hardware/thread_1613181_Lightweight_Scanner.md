---
title: "Lightweight Scanner"
date: 2010-11-04
forum: Hardware
---

### Post by gavinjb on 2010-11-04
Hi,

I am looking for a basic scanner for use with Linux and was wondering if anyone could reconmend any, I was looking at the Canon LIDe 100 but from reading various posts it looks like the possability of getting this to run on Linux is next to nill.

All I am looking for is a small light flatbed scanner with colour scanning and connects through usb (would be nice if it powered as well!), and has a resoultion of around 2400x4800dpi or better, can anyone reconmned anything?

Thanks,


Gavin,

---

### Post by IcarusR on 2010-11-04
To find if a scanner is supported by SANE check this listing ....

[http://www.sane-project.org/sane-mfgs.html]("http://www.sane-project.org/sane-mfgs.html")

Maybe a question of finding a suitable scanner & then checking the above link for compatibility.

Personally I stick with Epson, but they are not small.

---

### Post by bwana on 2010-11-30
I'm also on the hunt for a small flatbed scanner. It's for a small office and the Canon LIDe 110 fits my requirements perfectly, main ones being:
- small / portable
- USB powered (the office is in southern africa and we have blackouts quite often. we use laptops with xlarge batteries instead of UPS).
- simple to operate (pushing a button on the scanner to scan and email is perfect)
- has to work well with Linux (we currently run Ubuntu 10.10)
- high rez not needed - we're mostly scanning text documents or architectural drawings.
As I said, the Canon LIDe 110 looked to be perfect but the non-existent Linux support unfortunately makes it a non-starter.

gavinjb, did you find anything useful during the 3 weeks since your post ?

Has anyone seen anything like what I'm looking for ? 

Any advice and/or suggestions would be welcome!

>> Having looked around a bit, I think that the Epson Perfection V33 seems like a good option for us ( [http://www.epson.co.uk/Store/Scanners/Epson-Perfection-V33](http://www.epson.co.uk/Store/Scanners/Epson-Perfection-V33) ).

Did anyone try it out ?

---

### Post by gavinjb on 2010-12-07
Hi,

I am still currently looking at Scanners, in particular I am looking at some of the lightweight HP Scanners which seem to be compatible, but not sure if they are USB powered.

---

### Post by IcarusR on 2010-12-07
Canon LIDe 100 looks to be supported & completely working under 'Development (git) Version'  sane-backends-1.0.22git

[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON]("http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON")

Epson Perfection V33 is mains powered & supported by iscan from avasys

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do")

---

### Post by gavinjb on 2011-02-26
I have just had a look on the SANE website and it now looks like the Canon LIDE 110 & 210 scanners are supported, can anyone tell me if I will need to install anything extra (apart from scanning software) to use these scanners or should the latest kernel give me support

```

Model                Status     Backend
CanoScan LiDE 100    Complete 	genesys (1.0-62)
CanoScan LiDE 110    Complete 	genesys (1.0-62)
CanoScan LiDE 200    Complete 	genesys (1.0-62)
CanoScan LiDE 210    Complete 	genesys (1.0-62)

```

[http://www.sane-project.org/sane-mfgs.html#Z-CANON]("http://www.sane-project.org/sane-mfgs.html#Z-CANON")

Thanks,



Gavin,

---

### Post by fjgaude on 2011-02-26
I like the Epson V33, 4800 optical resolution, 8.5 x 11 scanning. Nice GUI under Linux.

---

### Post by gavinjb on 2011-02-26
> **fjgaude said:**
> I like the Epson V33, 4800 optical resolution, 8.5 x 11 scanning. Nice GUI under Linux.

Looks and sounds like a good scanner, just a couple of questions.

1. You mentioned a nice GUI does this mean that Epson supply Linux Software for there scanners or is it the Scanning Software you are using

2. Is it Mains of USB Powered, as preferable I am after a lightweight USB poswered scanner (I have to many power connectors as it is around my desk!)

Thanks,


Gavin,

---

### Post by fjgaude on 2011-02-26
You have to download three **deb** files and then click each one of the icons in your download folder. Then click on ImageScan! for Linux you will find in your Applications/Graphics menu. The GUI shows permitting all the options for scanning.

Study this link:

[http://ubuntuforums.org/showthread.php?t=1447789&highlight=epson+scanner](http://ubuntuforums.org/showthread.php?t=1447789&highlight=epson+scanner)

You have to use the adapter that plugs into the 110VAC wall socket.

Gosh, it sometimes hard to have good cake but still eat it, eh?

---

### Post by gavinjb on 2011-02-27
Hi,

Thanks for the help, looks like you have answered my scanner question :)

I was hoping for a Scanner that was USB powered, but I can't have everything (Yes it looks like the CanoScan 110 & 210 are now supported, but they dont scan from what I can see at their full resolution in Linux, so the Epson looks a better deal).

When you mentioned some scanning software I thought for a minute you were referring to the Proprietary VueScan software that you can buy for this scanner on all 3 OS's!

Thanks,



Gavin,

---

### Post by whome on 2011-04-14
I have a Canon LiDE 210 scanner. It works perfectly with Ubuntu 10.10.

Sane have to be updated. Info here
[http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick](http://www.bottomlesspit.org/2010/12/23/canon-lide-210-scanner-support-on-ubuntu-1010-maverick)

I use Simple Scan as software. Simple as the name indicates, I like it that way.

---

