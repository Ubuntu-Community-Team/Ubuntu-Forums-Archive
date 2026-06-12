---
title: "Need some extra space in /"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by shahdharmit on 2009-06-02
Hello all..

I have recently installed Ubuntu 9.04 in my system. I used to use Fedora 10 till now. Now the problem is that when I was updating Ubuntu, it showed me that there's less space in / partition. So can someone give me a way of increasing this size without having to re-install Ubuntu? I also use Windows 7 due to my academics. Thanks in advance.

---

### Post by logos34 on 2009-06-02
shrink win7 using its own disk utilities.  Then boot the ubuntu live cd, go to system>admin>partition editor, and expand / partition to incorporate unallocated space.  (You have to work from the live cd because root cannot be mounted during resize).

hope that helps

---

### Post by merlinus on 2009-06-02
You can try shrinking your windows partition using its built-in disk manager, if it has one.

Then you can use gparted to increase the size of ubuntu, using the space that was freed up.

I know nothing about the particulars of win 7, but you also should defrag that partition before resizing, if possible.  This is usually the case with any version of that os.

---

### Post by shahdharmit on 2009-06-02
Ok. Through Win7 I'll shrink a drive (an NTFS one) that has 30 GB free space. But can't I do it using gparted itself? Sorry if I m sounding foolish 'cause I'm using gparted for the 1st time.

---

### Post by logos34 on 2009-06-02
gparted doesn't handle vista or win7 NTFS too well.  Better to use windows own disk tool. That's the recommended way.

---

### Post by merlinus on 2009-06-02
Hi logos34!

Does win 7 need defragging before shrinking, like all the previous versions?

---

### Post by shahdharmit on 2009-06-02
i dont think so. I never used to defrag it before shrinking. And yet it all worked well

---

### Post by shahdharmit on 2009-06-02
> **logos34 said:**
> gparted doesn't handle vista or win7 NTFS too well.  Better to use windows own disk tool. That's the recommended way.

Thanks. Vl follow ur told way...

---

### Post by logos34 on 2009-06-02
> **merlinus said:**
> Hi logos34!

Does win 7 need defragging before shrinking, like all the previous versions?

Yo merlinus!

wazzup?

probably needs it, so I'd go with your suggestion...But I have to admit I'm not sure, since I've never tried win7 ntfs

---

### Post by merlinus on 2009-06-02
Finally got a new machine, and so my interest in sharing about and helping with ubuntu is back, at least for awhile.

I am loving the 64-bit version, as it runs the apps I need for digital photo processing much faster and better.

Glad to see at least one person I remember from the "old days" is still active!

---

### Post by logos34 on 2009-06-02
yeah, still around...go through phases where I get burned out with 'buntu and won't post anything, then others where I get my interest back...So, x64 is a lot faster for digital pix editing, eh?  Sounds right...I run x64 too but have no way of really knowing how much better the performance is because my processor is so crappy (wimpy sempy amd single core--don't laugh)...Compiling anything takes forever...I can overclock it to 2 ghz though, so that's some consolation...all I can say its whisper quiet...

---

### Post by merlinus on 2009-06-02
still around, and still giving excellent advice and help!  you da man!!!

when my 6-1/2 year-old machine basically died, i figured i merited something much better. so i went for a 3GHz dual core, 4G ram, nvidia geforce 9400 gt, 500G hdd.  and it is quite a bit quieter than the old one as well.

the app i use for working with raw photo files has a 64-bit version, so that was another reason to go this route.

and although i set up the disk with a 20G primary partition at the very front, i have yet to feel any need whatsoever to install win 2000.  someday -- maybe....  because the one win app i use refuses to run in a vm.

good to re-connect....

---

### Post by logos34 on 2009-06-02
just curious--what photo apps are you using/like best? 

gee, it would be nice to have a shiny new digital SLR camera...I could get into it, since there's no processing likein the old days

nice machine specs...god I need another hdd

---

### Post by merlinus on 2009-06-02
i use rawtherapee for opening, editing, processing, and saving the raw files.  i generally export them as 16-bit tiffs, and can do further processing, if need be, in gimp -- although it makes the tiffs into 8-bits.  after editing and sharpening i save them as high-quality jpegs, both for the web and for sharing with friends and family.

i use digikam -- a kde app which runs great with gnome -- for cataloging. 

those digital photos add up very, very fast.  i shoot both raw and jpegs, so i can use image viewer to decide if they are worth keeping and/or processing further.

the quality is amazing -- i don't miss film at all, and the instant gratification of viewing them is awesome!  i only wonder why it took me so long to jump on board, but of course the newer dslrs are quite something.

---

### Post by logos34 on 2009-06-02
'rawtherapee'-hah! love it

I know what you mean about gratification...I find myself spending hours looking through peoples jpegs over at AccuWeather photo section...average people (nature-lovers) taking great photos...I dl a lot of them, they add up quick space-wise

yeahm the resolution can be phenomenal..no reason for nostalgia for the old way (unless you're some purist into view cameras and dark rooms)

---

### Post by shahdharmit on 2009-06-02
Defrag was necessary. Without that I was given a free space of just 79 mb for a new partition. Thanks. Defrag going on. Hope I get some reasonable space after it's over.

---

### Post by merlinus on 2009-06-03
Yeah, I thought so.  I have had to do this with every dual-boot installation.  There is almost always a large green chunk near the end of the drive on the defrag screen, which makes it nigh-onto-impossible to claim all of the free space without a complete defrag.  

Another thing you might do is to get rid of any temp files, especially the ones with a tilde in front of the filename.  They can take up loads of hdd space as well.

BTW, sorry that logos34 and I had a conversation in the middle of your thread, but it had been quite a while since we last connected.

Thanks for being indulgent.  And good luck with your install!

---

### Post by logos34 on 2009-06-03
yeah, sorry too...I can get chatty at times!

---

### Post by shahdharmit on 2009-06-03
Oh it's absolutely fine about your conversation. I hadn't removed Fedora 10 so I finally deleted that entire partition from Windows and then re-installed Ubuntu so finally Ubuntu got a 58 gigs of breathing space. :)

---

### Post by logos34 on 2009-06-03
> **shahdharmit said:**
> Oh it's absolutely fine about your conversation. I hadn't removed Fedora 10 so I finally deleted that entire partition from Windows and then re-installed Ubuntu so finally Ubuntu got a 58 gigs of breathing space. :)

cool.  wish I had that much!

---

