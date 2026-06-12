---
title: "ATI X600 Mobile"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by brim4brim on 2005-07-11
Hi everyone,

I've installed the ATI drivers but it doesn't seem to be supported so I was wondering what the best driver for this in Ubuntu.  I have a generic one going but it's not supporting Open gl properly so is there a driver that will work better?  I know there probably isn't but I'm asking out of desperation

---

### Post by brim4brim on 2005-07-11
[QUOTE=brim4brim]Hi everyone,

I've installed the ATI drivers but it doesn't seem to be supported so I was wondering what the best driver for this in Ubuntu.  I have a generic one going but it's not supporting Open gl properly so is there a driver that will work better?  I know there probably isn't but I'm asking out of desperation[/QUOTE]
 So nobody knows anything about ATI drivers for the X600?

---

### Post by linuxfanatic1024 on 2005-07-12
[QUOTE=brim4brim]So nobody knows anything about ATI drivers for the X600?[/QUOTE]

Nope.  ](*,) 

But I had the same problem when I got my laptop with an ATI Mobility Radeon 7000--the drivers only started supporting 3D very recently, so I had VESA-only support for 6 months (SLOW VIDEO!!!) and then 2D-only support for 6 months. Your best bet is to wait...

--Dan "Crash" Brodzik

---

### Post by brim4brim on 2005-07-12
[QUOTE=linuxfanatic1024]Nope.  ](*,) 

But I had the same problem when I got my laptop with an ATI Mobility Radeon 7000--the drivers only started supporting 3D very recently, so I had VESA-only support for 6 months (SLOW VIDEO!!!) and then 2D-only support for 6 months. Your best bet is to wait...

--Dan "Crash" Brodzik[/QUOTE]
 No I contacted ATI and they said they aren't making any for laptops as that's the laptop makers arena so I sent an email to Dell (HA, yeah right or words to that effect!).

Anyway I've heard laptop users have been getting this to work with the X300 mobility so I figure it probably works with mine but I've tried the howto with no luck.  Any other X600 users out there or anyone know how to get it working.  I tried ATI's auto file creator and it kindly destroyed Ubuntu for me and when I tried to restore my backup copy of the file it still wouldn't work.  Anyway anyone got any advice/help/other sites to check that may have the answer?

---

### Post by brim4brim on 2005-07-14
[QUOTE=brim4brim]No I contacted ATI and they said they aren't making any for laptops as that's the laptop makers arena so I sent an email to Dell (HA, yeah right or words to that effect!).

Anyway I've heard laptop users have been getting this to work with the X300 mobility so I figure it probably works with mine but I've tried the howto with no luck.  Any other X600 users out there or anyone know how to get it working.  I tried ATI's auto file creator and it kindly destroyed Ubuntu for me and when I tried to restore my backup copy of the file it still wouldn't work.  Anyway anyone got any advice/help/other sites to check that may have the answer?[/QUOTE]
 I contacted Dell and in case anyone else wants something similar they say to TRY this Red Hat Driver they have:

[http://support.euro.dell.com/uk/en/filelib/index.aspx?sid=Latitude+D810&file=130946](http://support.euro.dell.com/uk/en/filelib/index.aspx?sid=Latitude+D810&file=130946)

for the D810 anyway so if anyone is wondering this is a bios upgrade and it's a .exe file that you use to create a floppy disc and then boot from it I think.

I havn't tried it yet as I have a document I need to print and I don't want it to take out my OS (just in case it does) as I can't afford to lose the files.

---

### Post by alxarch on 2005-08-21
same problem for me, it works only with ati as driver not fglrx and it can't even render the screensavers propably(sony has drivers only 4 win)

---

### Post by mlord on 2005-09-03
I have the ATI X300 (similar vintage), and just use the stock x.org "Radeon" driver.  Works well enough for me, but maybe you need something beyond that?

---

