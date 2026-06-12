---
title: "Boot Issues: Video Card or CPU?"
date: 2009-07-18
forum: Hardware
---

### Post by BJ_Covert_Action on 2009-07-18
Howdy Everyone,

First off I need to comment that I am pretty sure this is not an ubuntu issue so much as a general computer/techie question. Nonetheless these forums seem to be filled with folk much more techno-literate than I am so I am hoping I can garner some input/help here.

The other day I turned on my computer as I normally do only to find that it froze up prior to loading my operating system selection menu (grub is the program used for that if I remember right). Right now, my computer is running Ubuntu 8.04 as its primary OS on its primary HD and Windows XP as a back up on the secondary HD. 

Prior to loading either operating system, my typical Boot Screen Sequence failed to load properly. Normally, an ad screen for my 'Core Cell Extreme' chip loads followed by two other loading screens where I can typically log into my BIOS or edit my boot sequence from. Instead of showing any of these screens, my screen went black the first time I booted and never changed. I rebooted only to be met, the second time, with three different screens of pretty pretty pixelated color art. That is, pixels and rectangles of all shapes and sizes went apeshit and flashed every color my computer understands. It kind of looked like a defragging screen from hell.

It made it, upon the second reboot, to the ubuntu loading screen (bypassed my OS selection menu) but that, too, was FUBARed graphically. By the time it got to the Ubuntu login screen things seemed to have gone fine. I logged in and all seems to be running smoothly. When I do a reboot from the logout button in Gnome, the computer boots just fine. However, whenever I turn it off for long periods of time and reboot it, it greets me with the same rainbow sherbet mess of a graphic I described above.

Since this is all occurring pre-OS, I am pretty positive it is a hardware issue. I think it could be my graphics card going to crap: Radeon 9800 Pro 128 MB, or maybe something wrong with my processor or chipset? AMD 64b Athlon 3200. I am running the processor on the K8 Neo MSI motherboard, and have 1 GB of RAM. I really have never seen anything like this before, but have been using this box with various tweaks and upgrades (mostly to the RAM) since mid 2004. 

Does anyone know if the hardware I mentioned tends to degrade after about 5 years? Has anyone ever seen something like this happen before? Is there anything I can do to troubleshoot the issue from my OS, since I can't get into my BIOS? Does anyone have any suggestions for other forums/venues of support for pure hardware or general tech discussions? Has anyone ever heard of a bug or security threat that could have caused this?

To the best of my knowledge, I have done nothing on my computer recently that is any different from normal use. I honestly don't know where to start for troubleshooting this aside form just yanking components from other computers, plugging them in, and seeing what causes the issue to stop.

Thanks in advance for any input.

Cheers,
Brady

---

### Post by ndiVianBG on 2009-07-18
I guess its the video card. How does the BIOS look like ?
Hmm... but still now I have an NVidia card but before I had a similiar problem
with an ATI Radeon 9600.

---

### Post by philcamlin on 2009-07-18
yeah it looks like a video card issue

---

### Post by BJ_Covert_Action on 2009-07-19
Well if it's the video card, that's a relief.

I don't know what the BIOS looks like as I cannot access it since my boot screens go all to crap (I could probably do so after rebooting from the shutdown menu but when I do that, there doesn't seem to be a problem).

I have some scrapped boxes from work with old video cards in them I could swap out to see if that helps. I will probably do that tonight.

If anyone else has any ideas or knowledge, I would still be interested in hearing about them. 

Also, does anyone know if Ubuntu has issues with restarting after a video card swap? I don't have the driver discs for the replacement cards from work so I may need to download those prior to the swap?

---

### Post by learners permit on 2009-07-20
BJ is that the NF3 socket 939 board with an AGP slot? I had one of those until about a year ago (gave it a friend) and its still running awesome in a friends box. Before ya jump out the window for new hardware try testing the cmos battery or just replace it as its getting a bit old now.

---

### Post by BJ_Covert_Action on 2009-07-20
Ummm, honestly I cannot remember the specifics, but it does have an AGP slot. I did pull the Radeon card and put in some old beater video card from a scrap computer I had sitting around. It seems to have solved the problem, but that's not a bad idea on the CMOS battery, that probably will need to be changed here eventually. Thanks for the suggestions guys.

Also, I have never had any other problems with the motherboard so, I would agree that, in general, it is a good chipset.

Cheers,
Brady

---

