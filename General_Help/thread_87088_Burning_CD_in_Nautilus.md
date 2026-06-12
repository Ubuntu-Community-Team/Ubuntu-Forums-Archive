---
title: "Burning CD in Nautilus"
date: 2005-11-07
forum: General Help
---

### Post by canadianwriterman on 2005-11-07
When I put a blank, recordable CD in my burner, Ubunto recognizes it and places an icon on the desktop labelled "blank CD."

However, if I use Nautilus to burn a file onto the CD, Nautilus tells me there's no media in the drive.

I installed k3b and it works just fine. Do I need to do something to have Nautilus work just as well? Thanks.

---

### Post by earobinson on 2005-11-07
not that i know of. the nautilus burner is not very good anyway imho. I assume you are draging all the files to the cd dir then clicking the write icon (Just like in windows)?

---

### Post by KingBahamut on 2005-11-07
Yes, if your on Gnome, and you like the Gnomey look, try GnomeBaker its a bit simpler interface than K3b.

---

### Post by canadianwriterman on 2005-11-07
[QUOTE=earobinson]not that i know of. the nautilus burner is not very good anyway imho. I assume you are draging all the files to the cd dir then clicking the write icon (Just like in windows)?[/QUOTE]

Yes I did. I find it really strange that Nautilus recognized that I put a blank disk in the drive and opened a dialogue to guide me through the burning process, then asked me to insert a blank media. Very odd!

It's a moot point, because k3b worked perfectly, but I'm always interested in getting the Ubuntu defaults to work properly just for the heck of it.

---

### Post by earobinson on 2005-11-07
ya it is a good point, I would bugzilla it since i dont think you are doing anything wrong

---

### Post by steve.horsley on 2005-11-07
[QUOTE=canadianwriterman]When I put a blank, recordable CD in my burner, Ubunto recognizes it and places an icon on the desktop labelled "blank CD."

However, if I use Nautilus to burn a file onto the CD, Nautilus tells me there's no media in the drive.

I installed k3b and it works just fine. Do I need to do something to have Nautilus work just as well? Thanks.[/QUOTE]

By my experience, you need a freaking miracle to get Nautilus to burn CDs! I haven't managed it in 2 years. The most annoying is when it simultaneously says "please insert a blank CD" and pops up a new burn\\\ window because you inserted a blank CD. Although I have managed to burn the occasional coaster.

My advice is to stick with K3B. It works consistently and reliably, no funny stuff.

---

### Post by earobinson on 2005-11-07
I never have a problem with any burners, if you have problems and its a SW thing bugzilla it!

---

### Post by rawler on 2005-11-12
Hey, seeing the same problem here now that I installed on my fathers box. He's got a Sony CDRW 4x2x24, and though I can record and blank fine using Serpentine, Nautilus claims there's no disc in the drive. Any ideas? Is it bug-reported yet?

---

### Post by luopio on 2005-11-22
Any progress on this? I had nautilus-cd-burner working some time ago on my old gentoo installation, but now I ran into the good old problem here on ubuntu510 -> the burn-dialog only shows *"file image"*. Gnomebaker does the job, but IMHO cd-burning is something that the filemanager should do.

---

### Post by ed_d on 2005-11-22
I had the same problem, but use the gnome baker instead. Using the burn image through nautilus worked in core, but not on 510. Not a show stopper, but would be nice if addressed.

---

### Post by luopio on 2005-11-23
Just remembered that I fixed the issue by changing some permissions on the cdrecord, etc. commands. A little googling provided [this]("http://lists.debian.org/debian-powerpc/2004/02/msg00254.html"), but it seems a bit too much.. I'll just wait and see if dapper supports it :)

[EDIT] this might be a better solution if you want to get cd burning in nautilus: [http://www.linuxquestions.org/questions/archive/35/2004/12/3/220842](http://www.linuxquestions.org/questions/archive/35/2004/12/3/220842)  (let me know if it works)[/EDIT]

---

### Post by queenorych on 2005-11-23
Enabling overburn and burnproof in gconf fixed it for me when I had troubles.

---

### Post by bcl on 2005-12-10
I have this same problem on a clean install of 5.10 -- I can no longer burn CDs from Nautilus.

It used to work under 5.04 and Gnome Baker works under 5.10 so its not a hardware issue. Someone broke the nautilus cd app and it would be nice if they would fix it. Excuses like 'it works with app xx' are not good enough when you are trying to convince new users to use Linux.

bcl

---

