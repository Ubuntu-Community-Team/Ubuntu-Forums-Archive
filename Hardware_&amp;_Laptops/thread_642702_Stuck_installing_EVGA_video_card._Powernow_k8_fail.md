---
title: "Stuck installing EVGA video card. Powernow k8 failure"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by feenicks on 2007-12-16
Hello world! :)

I just barely started using Ubuntu this past week on a rebuilt eMachine.  Everything has been going super smooth.  More people should use this.  Actually I don't suppose it's an eMachine anymore since the only original parts are the case, floppy and CD drive.  Just tonight I put in a DVD-RW drive and was watching "Fellowship of the Ring" after a few package downloads.  I haven't tried burning anything yet but so far so good.  However, the onboard graphics weren't handling the movie playback like I'd like to see.  A little pixelation, you really have to look for it.  Not bad but not real good.

Emboldened by my success I then slapped in an EVGA e-GeForce MX 4000 graphics card (128MB, PCI, Nvidia) and caused some trouble.  The system starts to boot, Ubuntu splash screen shows for a bit then it gets stuck on

powernow-k8: failing targ, change pending bit set
powernow-k8: failing targ, change pending bit set
powernow-k8: failing targ, change pending bit set
.... like forever.

I'm back on my Windows machine and according to Google this failing targ thing is bad.  This card had been used only once for a few hours in another machine before going back in its baggie so I'm pretty sure it's good.  I have the driver CD but it's only got Windows drivers on it (does that matter?) and I don't know how much good it will do if Ubuntu won't even start with the card in.

Bottom line:  I want to use this card in the Ubuntu box but I NEED HELP.

Thanks in advance!

---

### Post by feenicks on 2007-12-17
Giving the thread a bump.  I really need some help here.  I'm running Ubuntu 7.10 and everything's peachy with the onboard graphics, but as soon as that card goes in, it won't boot at all.

---

### Post by feenicks on 2007-12-19
Hallelujah it WORKS!!

After much searching through the forums I found someone having a problem that might be kinda like mine.  (A bug regarding CPU voltage.)  First I went into my BIOS and disabled "Cool 'n' Quiet" and that stopped the endless powernow-k8 error.  

Then the system just stopped in the middle of starting the GUI it seems.  Then I found another lovely soul who had a partial solution to a problem similar to my new issue.  

So for anyone who was stuck like me, during boot hit ESC when GRUB starts.  Select recovery mode and at the root prompt type sudo dpkg-reconfigure xserver-xorg.  Most of the defaults were good.  After that the system rebooted and there was the desktop!

Everything after that was easy (non-CLI) and there are gobs of walk-throughs on activating restricted drivers and all.

The only weird thing that was bugging me was some messed up DVD playback.  The top and bottom halves of the screen looked out of sync by a frame.  I disabled desktop effects and installed xine and enabled deinterlace and post-processing (under video menu in xine).  Beautiful video at fullscreen, just like the old Windows box.

It's only been three days of serious work and research, and this is shaping up to be a nice little multimedia machine. :guitar:

---

