---
title: "esata not supported?"
date: 2011-01-30
forum: Hardware
---

### Post by davidmaxwaterman on 2011-01-30
I can't seem to get my esata drive working on my Lenovo w510 running kubuntu 10.10.

Are there any tricks to getting it working?

Max.

---

### Post by cascade9 on 2011-01-31
eSATA should work fine. 

Maybe you've got some nasty marvel controller for the eSATA ports. I dont think it should, the intel chipsets have more than enough SATA ports to use one as eSATA. The lenovo x510 specs page doesnt help me at all. :( Intel controllers normal play nice with eSATA however......

Have you checked in your BIOS to see is eSATA is enabled?

---

### Post by davidmaxwaterman on 2011-01-31
> **cascade9 said:**
> eSATA should work fine. 

Maybe you've got some nasty marvel controller for the eSATA ports. I dont think it should, the intel chipsets have more than enough SATA ports to use one as eSATA. The lenovo x510 specs page doesnt help me at all. :( Intel controllers normal play nice with eSATA however......


lspci doesn't show anything for 'sata' apart from the intel one...I guess that comment should show it, if it was there, right?

> 
Have you checked in your BIOS to see is eSATA is enabled?

I just checked and it is enabled.

I just noticed it is a 'combo' port - ie it doubles as a USB port. I wonder if that is somehow the problem...

Also, somewhere I read it is an E-SATAp with an extra 'p'...

Any clues there?

Max.

Max.

---

### Post by eddier on 2011-01-31
ESATAp means the port will supply power to the device plugged in,much as a usb device.

[http://en.wikipedia.org/wiki/ESATAp]("http://en.wikipedia.org/wiki/ESATAp")

eddie

---

### Post by davidmaxwaterman on 2011-02-02
> **cascade9 said:**
> eSATA should work fine.

It does. I tried another e-sata drive I had around and that worked fine. Then I tried the original again and it worked.

I think the drive may need to be power cycled in order to switch from its usb port to its e-sata port, but I'm not sure. Anyway, it works :)

---

### Post by cascade9 on 2011-02-02
Odd, but hey, it works. :)

---

