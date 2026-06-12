---
title: "OfficeJet g85 poor image quality"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by binkybeane on 2006-07-08
Hi All,
My wife is, thankfully, running Linux now after years of being a Windows junky. I set her up with Ubunutu Dapper and so far she loves it. Her only really big complaint is that printing to our networked HP OfficeJet G85 doesn't work so well from photo applications (i.e. Gwenview, F-spot, Digikam, etc.).

System/Software Specs:

    * Ubuntu Dapper (latest patch level)
    * HPLIP 0.9.7 driver (Ubuntu base and suggested)
    * Digikam 0.8.2 RC1
    * Kipi plugins
    * Dell Latitude D600 - 1.6GHz - 512MB RAM
    * HP OfficeJet G85 with JetDirect


What happens (I'll talk about using Digikam for now) is that when she submits a print job, the CPU spikes and holds at or near 100% until the job is spooled. This process can take up to 10 minutes. Once the job is spooled the size of the file to be printed is massive, sometimes well over 100MB. Then to top it all off, after waiting 10 to 15 minutes, the image quality is poor - it has vertical streaks and is grainy.

This same laptop would print near photo quality images to the same printer whilst running Windows with little effort.

One thing that should be noted is that printing from other applications such as Firefox or OpenOffice is fast, but the image quality is roughly the same (grainy and streaked).

I've also tried using a postscript driver. This made the job print faster with not as much CPU saturation but the image quality was way worse.

So! Now my wife just wants to be able to simply print a picture without all of this hassle. She's considering moving back to Windows. If anyone here can help me fix this for my wife and keep her off of Windows I would be very happy (and so would she!).

Cheers,
CTD

---

### Post by unstatusthequo on 2006-08-27
I'm not sure where I read this... maybe expertsexchange, but I thought the JetDirect and OfficeJet g85 have issues... I know my OfficeJet g85 is pretty much a piece of crap unless directly attached to a Windows box. I have a Linksys PSUS1 (I think) print server, and there is a documented issue of those not working together. 

Then again, if it worked in your Windows environment, I don't know what to tell you, I just know that some people have had serious issues with the g85 and the JetDirect.

---

### Post by DoctorMO on 2006-08-27
The reason why the photos are spooling like that is being they are being converted into raster images, big ones by the sounds of it. (yes raster into postscript into raster again, nice) so your problem is:

1) Your printer driver is setting the wrong resolution and head alignment for your print outs (or it could be it's not setting it at all)
2) Your printer doesn't support postscript directly or has very bad support for post script (most good printers supoprt postscript level 3 nowadays).
3) you have a rather nasty printer manufacturer that wouldn't release specifications for that printer.
4) there have been no volenteers who own a G85 to snoop the windows driver in order to improve the quality of the gutten print driver.

Have you tried turboprint? they might have better quality (or not, I havn't checked)

---

