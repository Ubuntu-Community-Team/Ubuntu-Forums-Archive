---
title: "Desktop Effects kills Terminal ability..."
date: 2008-09-28
forum: General Help
---

### Post by yoozrname on 2008-09-28
Hi, I just installed Hardy Heron 8.04 this weekend after being somewhat disillusioned with Fedora 9. I am very impressed so far by how smooth everything has gone as well as all the excellent documentation available compared to Fedora. I have been doing a lot of reading postings in the last couple of days about trying to get my video set up the way I want.

However I am at the point of being overwhelmed and have come to find roughly where my problem lies.

Machine is: HP P4 2.6Ghz HT, 1.5GB RAM, Geforce4 4200TI 64MB Card (VGA/DVI/S-Video out),
Vista on drive0, Ubuntu on drive1, 19" Sony CRT monitor,
32" Sony CRT TV set on S-Video out.

So here's the situation.

I got Twinview working so far so good with nVidia's binary driver (regular xgl), by saving the new xorg.conf file while running nvidia-settings through the terminal. Then restarted X. So, when I go to enable Visual Effects from None to either of the other two, I notice that when I open a terminal, all I get is a white window with no cursor or title bar. Also I notice that I am unable to drag any window without having to hit the Alt key.
I would think my nvidia card would have some capability to handle things.
When I set the Visual Effects back to None, my terminal window appears normal and am able to drag again. The same situation arises when I revert back to single display and nvidia-settings rewrites the xorg.conf file again. As soon as I go to "None" everything works fine.
When I first finished the install of Ubuntu, I noticed that by default the Visual Effects button was at "On" and my windows and terminal worked fine also. And from the point when I first saved the new xorg.conf file, that's when things went awry.
Is this a bug in the driver or is there something else I'm not considering?

Other than that, so far I am blown away with Ubuntu. Vista said my card was too old to run certain things and I wasn't about to dish out more money for a new one after spending what I did on Vista.

This is what I love about Linux, is that it sets itself up with the hardware you got instead of forcing you to spend your hard earned dollars on new hardware.

Thanks in advance for any help.

---

