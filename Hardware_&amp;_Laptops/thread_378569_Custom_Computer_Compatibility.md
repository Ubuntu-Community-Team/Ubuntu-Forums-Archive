---
title: "Custom Computer Compatibility"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by Puppy fam on 2007-03-07
Hi!

I'm looking at purchasing a custom-built computer from a local computer shop, but I've run into some Linux compatibility questions. I've done some research, but I would like some guidance before I go out and buy the thing. Here's what I'm looking at purchasing (items I'm concerned about are in red):
[LIST]
[*]Intel Core 2 Duo E6600 processor
[*]*[COLOR="Red"]Core 2 Duo  MSIP965 Neo-F Motherboard[/COLOR]*
[*]*[COLOR="Red"]256mb PCI-E Radeon X550 video card[/COLOR]*
[*]Two 160GB [COLOR="Red"]*Sata*[/COLOR] hard drives
[*]DVD drive
[*]1 GB of ram
[/LIST]

I've seen some things about the motherboard that have bothered me a little: [here]("http://www.ubuntuforums.org/showthread.php?t=233540&highlight=msi+motherboard+P965+Neo-F"). I've seen some incompatibility articles about some Radeon video cards in the same series as the one I'm interested in: [here]("http://www.leenooks.com/ATI+Radeon+x1600+PRO+PCIE+%28RV+530%29"). And I'm a little worried about Linux compatibly with Sata hard drives.

Can someone give me some guidance?

Thanks!

---

### Post by bobpur on 2007-03-08
Try this... Go to [www.distrowatch.com](www.distrowatch.com) and look for the sites that sell linux compatible computers. Look at their specs and go from there. Yeah, I know this is a low tech way of doing it, but it works.
There are other sites that feature linux computers and most post the specs.
As for what you list, you would be better off using a nvidia graphics card. they have better linux support than ATI does. I've used single SATA drives in linux, but for dualbooting (and my low level of expertise) I'd use PATA drives. I favor two PATA drives when dualbooting using two drives Linux on one and windows on the other. I've never dualbooted using a single or double SATA configuration. I use AMD processors for no real reason other than they offer more bang for the buck.(IMO)
                                                   Good Luck!

---

### Post by firedrow on 2007-03-08
I haven't run dual SATA HDD, but I have run single SATA without any problems.  I doubt a second HDD will pose any real threat.  As far as the mobo goes, the post you linked to seemed to have it resolved.  If it doesn't work on the first install, then read the post over and make the little changes here and there that they made.  The thing that seemed to help that board was changing the something to SATA+PATA mode instead of just SATA.  If you're buying it from a local shop, have them install Ubuntu as a test.  Most techs love testing things like that.  I can't say much about the ATI card.  I've always been an nVidia guy.  My roommate is looking to install Ubuntu with my help and he has an X850 so I will have some testing done.  My only suggestion on ATI is grab Automatix and Automatix:Bleeder and use the ATI drivers that it installs.  I've read the drivers for download aren't all that good.

---

