---
title: "acpi on/off with wireless card"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by josie on 2005-09-15
I have ubuntu installed as a dual boot on a Dell Inspiron 8600 laptop with a Broadcom Dell Wireless 1350 card.

So far I've had flaky wireless access with ubuntu.  When I boot with acpi on, every once a while when I *moprobe ndiswrapper* my system will hang.  (I want to say more often when my laptop is unplugged).  With acpi on I can't seem to turn on/off my wireless card.

Everytime I boot with acpi=off and load apm *moprobe ndiswrapper* works like a charm.  I'm even able to press Fn+F2 to turn on/off my wireless card.  The only problem is I have no display on battery power and the laptop gets pretty hot while the fan runs almost constantly.

Any ideas to why it would behave this way?  Is there something wrong with the way my wireless card handles power in acpi?  Is there a way to change it?

Thanks in advance for any help!

---

### Post by mlomker on 2005-09-15
Have you checked that your system BIOS is the latest version?  ACPI is all about the BIOS talking with the operating system.

---

### Post by josie on 2005-09-15
I have an older version...maybe I'll give that a try!

Thanks

---

### Post by josie on 2005-09-16
Updated BIOS, still has a freezing problem.

I wouldn't need to reinstall anything would I?

I want to say that it happens only when my laptop is unplugged or...maybe...when my ethernet cord is unplugged???  I'm not sure...

Thanks for your help!  Any other ideas?

---

### Post by mlomker on 2005-09-16
Can you borrow or purchase a wireless card that has a native driver?  Some places have a 30-day return policy (hint, hint).

Seriously, though, Broadcom really bites.  They are one of the few wireless chip vendors that refuses to work with anyone wanting to make a linux driver.  I'd recommend a card with either a Prism or Atheros chipset.  Most of the Linksys cards are Atheros and will use the madwifi driver.

---

### Post by josie on 2005-09-17
Yeah I could borrow one from a buddy.

I seem to have found a temporary solution.  I installed rfswitch to add the Fn+F2 functionality to turn on/off my wireless card.  It seems like if I boot up with my wireless card off, and then modprobe ndiswrapper.  Everything works Ok.  And then I just turn on my wireless card.

---

### Post by mlomker on 2005-09-18
> I installed rfswitch to add the Fn+F2 functionality to turn on/off my wireless card. 

Hmm.  I wasn't aware that buttons like that would work with a PCMCIA card.  Unless I misunderstood your original post and you have an integrated card.

---

### Post by josie on 2005-09-21
Sorry, Yeah it's an integrated card.

---

