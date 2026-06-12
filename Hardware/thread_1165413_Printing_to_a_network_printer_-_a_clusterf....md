---
title: "Printing to a network printer - a clusterf..."
date: 2009-05-20
forum: Hardware
---

### Post by rumplestilts on 2009-05-20
I took an old Acer Aspire, lobotomized XP off of it and installed Ubuntu. Everything on the unit (audio, ethernet, wireless, etc.) was recognized and worked perfectly.

Then I took an older G4 iMac (the "snowball" flat-screen model) and did a network install using a really small (MB, not physical size) CD. That also worked like a charm.

However (and this seems to be a theme running through many linux forums), getting both of these machines to print to a network-connected printer is virtually impossible. Oh, I see a few people claiming to have done it (and I don't doubt them) but almost every response to that thread is "well, I can't do it following your instructions". I've tried a half-dozen suggestions and none of them did anything more than cause the printer's activity light to flash once.

Until now.

I finally found a way to get both the iMac and the Acer to print to my Brother MFC-465cn (haven't tried the scan or fax functions and, frankly, I don't need them). The solution? I just configured the Mac already on my network and configured to print to that printer properly (which used the Brother-supplied software to accomplish this) to *share *that printer to other computers on the network. I do have filesharing turned on in that Mac (with SMB) but I can't tell if SMB has anything to do with the successful printer-sharing.

How did I configure the Ubuntu machines? Using the usual System>Administration>Printing and asking for a "New" printer. The Brother (shared by the Mac) was immediately seen on the network and I used all defaults through the process. I will note that the printer was already seen (the printer itself) before I shared it from the Mac but, no matter what I did, it never worked.

So now I have another purpose for that old Mac mini: As well as being a media server for my network, it will also be a print server for the Ubuntu clients on my network.

I'm really quite pleased that this works properly as I -do- want to use Ubuntu. While it's not OSX (and I bleed in six colors since '86), the ability to use PC hardware with something akin to OSX (close enough that it's obvious they are the offspring of the same mother) is a fantastic benefit...and a kick in the balls of Balmer.

However&#8212;and I'll stop being giddy about the shared-printer solution for now&#8212;this failure of the Linux community to deal with the printer manufacturers' failure to produce adequate stand-alone software solutions is the 800 pound gorilla in the room which Linux does not like to mention to the world. Certainly with CUPS available to everyone (in spite of being owned by Apple), we should have simple solutions. Once Apple standardized their printing architecture in Tiger, all the printer manufacturers had the (CUPS) solution handed to them. (Well, HP still likes to do things in their own proprietary manner which is, I guess, why I don't buy any HP products any more.)

Perhaps it's the software installation process in Linux that is to blame? This "if-it's-not-in-our-repository-it's-your-problem" attitude appears to be the cause. I assume that this is a security issue. If so, OSX seems to have managed to overcome it.

Okay, okay! I can hear you now: "So use OSX and begone!"

I'm not trying to start a flame here (as I really do like Ubuntu!) but I guess I'm pointing out what I see as the major issue standing in the way of Linux's success in spreading to the Desktop (or Notebook). If you think I'm wrong, look at the return rates of the Linux-equipped Netbooks. Why are they being returned? Much of the peripheral hardware and connectivity (to printers, etc.) just isn't enabled properly. (In all fairness, this could be caused by totally inadequate configuration by the Netbook vendors; if so, this further points out how far away the goal remains.)

Okay; that's my story and I'm sticking to it. :D And I'm having fun with my Ubuntu Mac & PC.

Thanks for taking the time to read this. Remember, if all you're going to do is reply "No, you're wrong", don't bother. Rather, why not *prove* me wrong by providing the one-step app that makes my network printer work without a Mac serving it up. I (and hundreds more who are having printing issues) will thank you.

Oh, one more thing! A big thank you to those whose posts I've already read and found useful enough to lead me down this path to Ubuntu. I feel very much like I did when I used my first Mac 20+ years ago.

---

