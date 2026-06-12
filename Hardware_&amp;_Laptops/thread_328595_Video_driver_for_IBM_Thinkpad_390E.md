---
title: "Video driver for IBM Thinkpad 390E"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by bobpur on 2006-12-31
I recently became the owner of an IBM (Not Lenovo) Thinkpad 390E. It's in darn good shape for its age. It had Win 2000 installed on it.
The former owner removed a 64 mb memory stick and put in a 128 mb stick. 
I tried a couple of small distros because of harddrive size (4.33 gb) Damn Small Linux being the one that worked best. Anything else was really slow.
Anyhow, I found the old 64 mb stick of memory and added it back in to bring memory up to 192 mb. I then tried Xubuntu (Dapper) and it runs great. I'm going to max the memory for this laptop at 256 mb. 
The Video is another problem. This laptop uses the Neomagic NM 2200 chipset. 
I found on the web where someone got video to work with Xfree86. I checked that out and was about to take the plunge when the "Readme" stated that Xfree86 could handle most anything but what it couldn't the "Vesa" driver could. I backed off because Vesa is the default video driver in Ubuntu and a lot of other distros (Isn't it?)
Has anyone used Xfree86 that could help me out here. The picture isn't too bad, but it gets "wavy" when you scroll too fast.
The Website for Xfree86 is: [url]www.xfree86.org

                                                                        Thanks :)

---

### Post by fiestaforever on 2006-12-31
I have a Thinkpad 600E with the same video hardware. 
I installed Xubuntu 6.10 on it (and it was necessary to reduce the default in xorg.conf from 24 bit to 16 bit to get a halfway decent picture, but the "wavy" display is still annoying, esp. when moving windows, so I disabled "solid drag" for the window manager). 
Before that, I had Vector 4.3, which includes XFree86 (can't remember which version, 4.3?), but it was similar (probably the same driver), and it would also run on 16Bit colors only. 
IIRC, the picture quality was a little better then, but window manager and apps were too different to tell.

---

### Post by bobpur on 2006-12-31
[http://www.ecn.wfu.edu/~cottrell/tp390e/](http://www.ecn.wfu.edu/~cottrell/tp390e/)
This is the website where I got my info from if it will help you. My technical expertise is such that it is a little intimidating to try something like this. I wanted to find somebody that may have tried this already.
I got this laptop as a gift so I don't have any money in it. I wouldn't mind having to put some into it for a harddrive and memory upgrade. That is, if I can still find parts to do it with.
Thanks

---

### Post by fiestaforever on 2006-12-31
The information on that website is more than five years old. 
AFAIK, xorg is the successor of xfree (AFAIK they split over licensing issues, and almost all distros adopted xorg). From what I've seen in the config files, they don't seem to be very different. 
I doubt there would be any benefit installing the older package (if it's possible at all). And you'll probably find no packages for Ubuntu.

---

