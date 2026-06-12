---
title: "Cardbus interface &amp; other audio questions"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by Scheater5 on 2007-02-17
I'm trying to find the best setup for music production (both score writing and audio recording) on a budget.  
I think I'm going to have to hang on to Windows for a while for Finale, much as I hate it.  NoteEdit is ok for school work, but not nearly good enough yet for songwriting.  And Rosegarden's midi score writing is nice, but clumsy to use (although the finished product is nice, so I'll probly use it for typesetting already written music).  
I was looking upgrading the sound card on an old desktop (and probably RAM to) to one more suited for semipro/professional audio, when I came across [this]("http://www.newegg.com/Product/Product.asp?Item=N82E16829110014").  My next hardware upgrade would probably be another laptop, and being able to record on the go is definitly a plus, so this option appeals to me.  Does anyone know anything about this card and interface?  I've never seen a cardbus audio interface so I don't know how it stacks up against firewire or USB interfaces.  (USB doesn't cut it for what I want to do)
That's mainly what I'm interested in - oppinions on the card, but I'll also gladly accept any other suggestions related to audio production, particullarly as it relates to Linux (I'm trying to stay away from windows, and I refuse to pay the prices for mac).

---

### Post by tgalati4 on 2007-02-20
I produce church music on a PII, 300 MHz system (396MB of memory) using Dynebolic (Live CD) and a pci-card (probably firewire) M-Audio 4 channel audio-headend.  Works great.  Real-time kernel keeps things on track.  Audacity works great.  Streaming is OK (can use a faster processor for real-time compression AND streaming).  Of course Ubuntu is installed on the machine for everything else.  I use it for recording live gigs and on-the-fly compression to mp3's for a web server.  Ubuntu and Dynebolic can access the same internal disks.

The PC and the sound card were donated.  Ubuntu and Dynebolic are priceless, of course.

The challenge with a cardbus card is that the D/A's will run hot in that small form factor.  E-Mu is a good product.  If portability is important, it may be the way to go.  If reliability is important (during recording of a live event) for instance, I would use a fan-cooled, sturdy, white-box PC, with a handle riveted to it (now that's portable) and a high-quality pci sound card with decent preamps.  UPS is important as well.  There are lots of reviews on decent audio equipment.

The other issue is reliable disk drives.  Most drives don't like continuous writing (as what occurs during recording).  The heads get hot and they warp.  Notebook drives are even worse.

For music recording and editing, it helps to get a server-quality drive (7200 rpm) they are more expensive, have 5-year warranties and can handle the abuse.  Keep Ubuntu and swap on a separate drive.  In Audacity, you can specify the drive for editing.  This way if the music drive takes a dump, it won't take out your operating system.

The M-Audio has decent 24-bit/192kHz Linux support as well.  Not sure what the E-MU support is under Linux, but a Google search can reveal that.
The E-MU has slightly better specs than my 3-year old M-Audio system, but for church production it is more than adequate.

Good Luck,

Terry

---

### Post by Scheater5 on 2007-02-21
Thanks for the info Tgalati.  I don't think that the laptop w/ cardbus route is the way I'm going to go after hearing about the problems with it from you and getting the same thing with some further research.  It's still a possibility, but now I'm looking at some whitebox pcs.  
I'd heard about them, but never been able to find a good price from an online dealer (I don't trust any of the local computer stores in my small town).  But I just found one called pcusa.com and "customized a pc" on their website  and came up with [this]("http://www.pcusa.com/shopkitconfig.asp?id=KIT-406&selectList=0,1,4,0,1,0,0,8,1,4,0,3,8,15,0,0,0,0,11,1,5,0,0"). From what I know about hardware this is a really nice compared to comparably equipped brand name computers.  The customer support of brand name pc is no factor - I generally come up with some way to void a warranty in short order anyway.  
So, what do you think about pairing that pc (and any suggestions for changes, or things I can do without) with [this soundcard]("http://www.digitalproaudio.com/esi-julia.html") for music production?

---

### Post by tgalati4 on 2007-02-22
Sound card has good specs and price at $159 is reasonable.  No microphone preamps so I assume that you will have a small Mackie mixer or equivalent.

The PC you spec'ed out is a screamer.  In some respects overkill for music production.  When I said whitebox PC, I meant atticware--something donated to a church for instance.  At a garage sale you can pick up a PII or PIII pc for $25 to $50.  Max out the memory (typically 512MB to 2GB depending on the motherboard), buy 2 server quality, 5-year warranty disk drives (Hitachi Deskstars--or Deathstars as people like to call them).  

A 64-bit machine is overkill for music because there is not a lot of mathematical processing involved.  Most filters and effects are pretty efficient in 32-bit.  Video editing and 3D rendering benefit from 64-bit.

Whatever you get, break in the memory (with memtest) for a couple of days and break in the disks by using security wipes--writing ones and zeros to the disk.  Installing an OS to a fresh drive is asking for trouble--quality control on drives today is nonexistant and they loosen up with use so do yourself a favor and work the drive before using it for serious work.

Report back when you have your system together and let us know how it performs.  I had mentioned Dynebolic as a streamlined, realtime kernel.  There is also a studio version of Ubuntu in the works with realtime kernel hooks, allowing you to turn the kernel realtime on and off, which is cool.  Dynebolic is only realtime and that is why I recommend CD booting because you can use Ubuntu on the disk for everything else.  

I would guess that Studio Ubuntu will have more overhead with gnome and all of the other processes running in the background.  Dynebolic is pretty slim and designed to do one thing really well.

---

### Post by Scheater5 on 2007-02-22
Yea, I know the pc is kinda overkill for music production, but it was such an awesome price for 64-bit I thought I would explore that.  There's some saying about thd difference between cheap and affordable??  Well, I might upgrade my desktop instead of my original plan to upgrade my laptop, and use that desktop pc for both "regular" desktop use and music production.  But, it's also interesting to hear how cheap I could do it, too...I also have an old desktop (shipped with Win98) that is just collecting dust...I think I'm going to start by seeing if that thing even still works, and if it does, putting Xubuntu and Rosegarden on it and ordering that soundcard.

---

