---
title: "Dell Tech Support Answer to ATI card"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by brim4brim on 2005-07-14
Hi,

To answer peoples first question, yes I was desperate when I contacted Dell's Tech Support.  ATI told me to contact the manufacturer of my laptop as they don't support their laptop cards with drivers (eh?).

Anyway they gave me a link to this saying it's a driver for Red Hat Linux but it's a .exe file and you need a Floppy Disc to create it.  It's also just a bios upgrade so I thought I'd ask here is it safe to install this for a duel boot Ubuntu system as at the bottom of Dell's email they say they take no responsability for the info in the email being inaccurate and don't support Linux installation so I just thought I'd check here.

[http://support.euro.dell.com/uk/en/filelib/index.aspx?sid=Latitude+D810&file=130946](http://support.euro.dell.com/uk/en/filelib/index.aspx?sid=Latitude+D810&file=130946)

This is for the D810 in case anyone wants to try it or look for similar for their cards on Dell's website but like I said I havn't tried it yet so it my not work!

---

### Post by Strife on 2005-07-14
BIOS updates very rarely actually screw things up. They mainly just say they can't claim responsibility that way if it's the one in a thousand chance that it DOES screw up, they're not liable. Just make sure to backup everything that you absolutely need in case of a catastrophic failure.

It should be okay, but consider yourself warned.

---

### Post by leezer3 on 2005-07-14
Hi there,
This is only a video BIOS update, and while it may speed up the card marginally, in Linux it will do close to b***** all!
Use synaptic to install the flgrx package (I expect you have probably done this), and then have a look at the ATI card tutorial in the tips & howto section- Basically you have to set up your X-Server to run on FGLRX rather than the generic driver that it's running on at the mo :P 
Mind you, I haven't managed to get this running yet either, so there's two of us with no decent laptop 3D support!

-Leezer-

---

### Post by brim4brim on 2005-07-15
[QUOTE=leezer3]Hi there,
This is only a video BIOS update, and while it may speed up the card marginally, in Linux it will do close to b***** all!
Use synaptic to install the flgrx package (I expect you have probably done this), and then have a look at the ATI card tutorial in the tips & howto section- Basically you have to set up your X-Server to run on FGLRX rather than the generic driver that it's running on at the mo :P 
Mind you, I haven't managed to get this running yet either, so there's two of us with no decent laptop 3D support!

-Leezer-[/QUOTE]

Yeah that's why I was posting this, after following the howto's and looking round on the web and doing pretty much everything I could think of, it wouldn't work so I contacted Dell and am hoping this works.

I've backed up my files and tomorrow I have to proof read and make some changes to a doc and then print it in XP (no printer don't work in Linux either yet), drop it into the college tomorrow and then go nuts and get Linux working before final year so I don't have to use windows for 4th year project hopefully, all going well.

---

