---
title: "XSane Out of memory scanning"
date: 2008-10-28
forum: General Help
---

### Post by johnuk on 2008-10-28
Xsane is working fine with my scanner up until the point where I bump the resolution from 600 to 1200dpi. 

Before the scan will even start, it hits me with an out of memory error and nothing happens.

If I try it in Kooka, I get no message, the scan just doesn't start.

I've seen other people having this problem, but with no resolution.

I have of coarse tried this with nothing else running. The computer has a gig of RAM, so it should be okay with the scan.

Is this an error in XSane or the backends I can't fix? Or might Ubuntu be assigning the RAM in some way that's tricking XSane into thinking it doesn't have enough available.

I'm particularly bothered because I'm considering bumping my scanning up to the Epson V700 - so it'll be a pain if the resolution dies on that as well.

I've also been having a problem with Flash that I think may be related, as they both seem to do with memory allocation to imaging;

[Here's the flash problem]("http://ubuntuforums.org/showthread.php?p=6050505#post6050505")

Any thoughts about what could be up?

Thanks!

---

### Post by phidia on 2008-10-28
You can try the scan from a terminal-that should provide more detailed output-use the scanimage command (see man scanimage How much space-memory do you have available in your /home/user directory?

---

### Post by johnuk on 2008-10-28
Thanks!

/user has around 20gb free. I tried running scanimage --test and the backend all reported okay. I tried running a scan at 1200dpi. It took long enough for it to be convincing that it was actually running at the setting, but it was black and white. When I tried running it again with colour;

user:~$ scanimage --mode color --resolution 1200 --format=tiff --verbose > film.tiff
scanimage: sane_start: Out of memory

---

### Post by johnuk on 2008-10-29
I tried splicing my image in the xsane preview. The original was around 70 - 80mb with the area I'd selected at 1200dpi

I accidentally knocked a boarder for the scan and it ran without a memory error.

This suggests that the error isn't simply some glitch from the dpi setting, it's genuinely assessing the scan size and then comparing it to the memory available.

Now the question becomes, why does it think I have about 60mb free with a 1 gig stick?

---

### Post by habana on 2008-11-24
Hi Johnuk. Did you get a resolution (no pun intended) to this? I have an Epson V700 and get the same error message above 1200 dpi

---

### Post by johnuk on 2008-11-24
I haven't tried doing a big scan recently, but I never did find a fix either.

The only way I could use the high resolutions was making sure I kept the scan area small enough to make the scan around 60mb in size.

Try it on yours and see if you get the same memory amount.

As I've said, this is significantly less than my computer actually has in it, and I'm often not running anything else.

---

### Post by habana on 2008-11-24
I scan at 1200 dpi and get a 392MB file, all OK. If I reduce the image size and up the resolution to 1600 dpi I get the 'out of memory' message even though xsane says the file will be 354MB.

Like you I have plenty of resources - see output of 'free' below.

```
             total       used       free     shared    buffers     cached
Mem:       2065444    1109912     955532          0      63276     504856
-/+ buffers/cache:     541780    1523664
Swap:      1992040          0    1992040
```

Not sure where to go from here but if I sort it out I will post it.

---

