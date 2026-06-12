---
title: "Video Card not recognized"
date: 2012-01-09
forum: Hardware
---

### Post by patriot56 on 2012-01-09
Can anyone tell me how to force Ubuntu to use my installed nVidia GeForce PCI card?
First let me say that there are no words in the human language to describe my hatred for this card!!!

That said, I don't have a choice at this time because I can't afford to purchase a new video card.
2 days before Christmas (2011) my 7 year old computer died.:(   So, now I'm stuck with an _OLD_ IBM computer.
Here's what I have to work with:

[LIST]
[*]**IBM Pentium 4 1.80 GHz.**
[*][B]1.5 Gig.'s RAM
[/B]
[*]**Integrated Brookdale-G graphic chip **(disabled in the BIOS)
[*]**nVidia GeForce4 MX 440 NV17 PCI card **(this is the card that I am trying to get installed)
[*]**Sound Blaster Live** sound card
[/LIST]
I've installed the drivers for this video card using Ubuntu's "Additional Drivers" applet and it recommended using the NVIDIA accelerated graphics driver (version 96) which I did.
When I open the System Info. app. it shows "Unknown" next to Graphics.:(

I have been working on this problem far to long now and really just want to get it resolved.  I can't believe that it is this difficult to get the appropriate drivers installed for a card that has been around for 10 years; especially for Linux.  If this was a M$ Windows computer, I could understand it.

If anyone has any suggestions I would be extremely grateful.

Thank you in advance.

---

### Post by MoreOrLess on 2012-01-09
That is a known/common bug in the system info app. Check glxinfo to verify correct driver installation:
```
sudo apt-get install mesa-utils
glxinfo
```

---

### Post by patriot56 on 2012-01-10
@MoreOrLess:KS
Thanks mate.  You just did what others couldn't.
I have been looking for a solution to this problem for almost 2 weeks now and no one has been able to even get close, but you, in a matter of minuets solved the problem and with one command.
I apologize if this sounds a little hero worship but I was prepared to throw the whole computer out the window.  LITERALLY!!! :(  You rock!

Thank you again.

---

