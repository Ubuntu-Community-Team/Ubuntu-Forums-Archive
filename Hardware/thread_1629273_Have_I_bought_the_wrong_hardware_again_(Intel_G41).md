---
title: "Have I bought the wrong hardware again? (Intel G41)"
date: 2010-11-23
forum: Hardware
---

### Post by heyho on 2010-11-23
Trying to overcome the limitations of VGA on my Myth tv setup, I replaced my video card with a dedicated 8400gs, which had a disagreement with my Mobo (would not even POST!), so instead of running the risk of ATI compatibility problems, I went for a new Motherboard with onboard Intel G41 chipset (Gigabyte GA-G41M-ES2H G41), with DVI and HDMI connections.

The good news is that the display is detected properly, and now defaults to the correct resolution of 1920x1080.

1st problem, install exits to a live session due to "unexpected errors", but strangely, pretty much the entire desktop environment (and the mythtv frontend) when they do startup are almost entirely green!  This also happens with mint 9 (even greener than usual!)  The green seems to occur just after the 1st splash screen, so I guess it's when the drivers are loaded.  It's almost as if the green is now where black should be.

When I use the VGA connection, the colours are fine.  I (foolishly) thought that I would be safe with Intel, as a few searches before I purchased this board threw up little in the way of problems.  I realise that I've been a little vague, but I'm not too sure where to go from here.  It would be encouraging to hear if anybody else is using the G41 chipset with the digital connection.

It seems that I am destined never to get this box up and running properly!

---

### Post by heyho on 2010-11-24
Well, I'm half way there.

Plugged the box into a different display(another LCD TV), and voila!  Colours back to normal.

Unfortunately, I don't have another digital source to plug into the problem tv, so I'm still not sure if it's the display at fault, or the way it's being detected.

Is there anything in the "handshake" between graphics chip and the display which could cause this problem?

---

### Post by dandnsmith on 2010-11-24
It could be a connector problem.

Did you try the same cable?
Have you since tried plugging the original display back?

I'd always try different cables.

---

### Post by heyho on 2010-11-24
Hi Derek.

Yes, back on the original display now, and still giving the same problems.  The cable is a brand new DVI>HDMI lead, which has also been used on my daughter's acer revo with no problems (on a different display).  I will try another cable shortly though, just to rule it out.

I am still convinced it is software related, because the 1st splash screen on the live CD (640x480) is the correct colour, I think I'm right in thinking that this is displayed using vesa.

---

### Post by heyho on 2010-11-24
Well, I've just booted from a puppy live cd, and all is well - all colours displayed correctly.  That rules out the lead and the display in my book.

I'm still thinking that this is a problem during the EDID handshake, but I don't know enough about how this works.


Hmmm...

---

### Post by dandnsmith on 2010-11-25
It certainly sounds as if you've eliminated the cable.
I don't know anything about the DVI>HDMI routing to comment (like any pitfalls in transferring between formats).

I've fallen foul of the EDID thing myself, without realising it for a couple of years, when trying to use a VGA connection switched between PCs - but that only resulted in a Least Common Denominator (can't use LCD here) display, with no colour oddities.

I'm not sure about vesa for the initial display, I would have expected it to be bog-standard VGA, especially using 640x480.

I don't see how the colour shift could arise (but have you tried googling for EDID problems with your example display?).

I know that not all the distros do the monitor properties setup the same way, but haven't had occasion to check Puppy to see if it stores an X config file - I know Ubuntu doesn't nowadays, but can be persuaded to create one (which might help sort things out).

---

### Post by heyho on 2010-11-25
Well, as far as I understand, DVI is the same as HDMI, but carries no audio, so there is not really any conversion going on at all, but I will try a plain HDMI cable when I have one.

I also plan to test the box on my Father's full HDTV at the weekend, as my other television is only 1360x720.

As for the xorg.conf, yes, that is my hope at the moment.  I will boot puppy again later this evening and have a look at the file it creates, and maybe use it as a starting point.

I've done plenty of googling, and keep finding this thread!  Thanks for your input Derek, hopefully I'll get this sorted and report back on this thread.

---

### Post by heyho on 2010-12-05
A small update, but still no success.:(

I have so far tried the following:

PC -> TV via DVI/HDMI cable, everything green.(10.04)

PC -> TV via HDMI cable, everything green.(10.04)

PC -> Different TV via DVI/HDMI cable, everything fine.(10.04)

PC -> TV via DVI/HDMI cable, everything fine. (puppy/mepis)

HDMI upscaling media player -> TV via HDMI cable, everything fine.

I am still convinced that this issue arises when the video drivers are loaded, quite possibly at the point when the graphics chip and the television "handshake".  Why it should only happen on this particular tv I don't understand, but as stated, other HDMI devices seem to work fine on the same tv.

I suppose I could start by trying to find out if any alternative drivers are available, or perhaps by trying to read out the edid from the television.

Help.[-o<

---

### Post by heyho on 2010-12-07
Update - I threw the TV out of the window, should I now mark the thread as "solved"?

---

