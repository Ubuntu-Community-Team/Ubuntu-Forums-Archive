---
title: "Digital Camera: Olympus FE-210 Drivers"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by gunderwood on 2007-08-20
HI All,

I've just purchased an Olympus FE-210 digital Camera and it appears that there are no drivers listed for this particular camera. It automatically loads the Olympus C-370Z driver but is unable to import any photos. 

Does anybody have this camera and know if there are drivers available for it? I've never had a problem with my old camera so I'm not sure where to even start looking to find out if the drivers exist, and if they don't I'd be happy to assist in any way that I can to have them written. Even if it means writing them myself. 

I've never done any work on the kernel or drivers, but I am a decent C programmer so if somebody can give me some pointers and good documentation to look into I think it could be a wonderful opportunity to get involved and do something I've been procrastinating about for a couple years, learn how to write a driver.

I guess at the very worst I'll just start reading some other drivers code and see if I can figure anything out from there. 

So if any resident experts can give me a hand it'd be greatly appreciated.

G

---

### Post by kdborg on 2007-10-30
I had the same problem.  

The solution is to set the camera to MTP instead of STORAGE.  The steps I took:
1) Plug in USB cable to camera and computer.
2) PC is highlighted, so go to the right.
3) Select MTP.
4) Choose what you wish to do.  I'm in KDE 3.5, so it gives me some options.

---

### Post by cambirder on 2007-10-30
The best option by far is to never connect you camera directly to the computer. Get a card reader and transfer the images direct from the memory card. 

The camera USB socket is easily damaged easily damaged if constantly used and the battery failing half way through transferring your images can corrupt the files.

---

### Post by Fangorn59 on 2008-02-14
I am using an Olympus FE-110. This was being recognised as a removable drive until about a week ago. Now it is incorrectly labelled as C-370Z and won't import pictures. I found that changing the camera detection settings enabled me to download pictures again. Go to System/Preferences/Removable Drives and Media, then click on the Cameras tab. Uncheck the box under Digital Camera labelled "Import digital photographs when connected", and click close. Now when attaching the camera it is recognised as removable media and I can use gthumb to import the pictures.

---

### Post by oldsoundguy on 2008-02-14
AMEN to cambirder!!  Not only will a reader WORK, it will save batteries and wear and tear on the camera.  A good 10 buck investment.  I have readers that install in a floppy slot on all of my computers .. slightly higher spread at 20 bucks, but they work!  Ya can't ask for more than that!

---

### Post by freund on 2008-02-23
In Gusty. Interestingly I had the same problem with two versions Olypus cameras FE220 and D590. But I didn't have this problem with a Kodak C713. I didn't have any problems with Fiesty. 

For the Olympus I found that instead of connecting via the PC, I pressed the one for the printer it would connect and show the photos and you can download the pictures. The FE220 would disconnect every once in a while though. 

The kernel in Gusty has been blamed for this issue and I hope they will have it fixed in the next distro.

---

### Post by wilcan34 on 2008-03-04
Thanks Fangorn59  Fangorn59.
Did as you said in your post re digital camera,Have Fujifilm S3000,now no trouble importing to gThum.
Thank you very much for the clue!

---

