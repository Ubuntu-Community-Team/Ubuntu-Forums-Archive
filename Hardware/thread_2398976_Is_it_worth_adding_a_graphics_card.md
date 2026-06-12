---
title: "Is it worth adding a graphics card?"
date: 2018-08-20
forum: Hardware
---

### Post by geofftf on 2018-08-20
I bought a 10 year old PC that was loaded with Windows 7 and hardly ran at all. Installing Lubuntu converted it into a usable machine. I have doubled the RAM to 2 GB DDR2 667 MHz, doubled the number of memory channels to 2, doubled the processing power to a Core 2 Duo E6700 (Passmark 1694) and installed an SSD. Performance with Lubuntu 18.04 is now pretty good. Boot time is 20 seconds. Firefox takes 5 seconds to load, and most web pages load very quickly. Installing U-Block Origin has helped for sites with lots of adds. Nonetheless, some websites load slowly with Firefox (e.g. Google News with all its little pictures). The motherboard is an Intel D945GCNL with GNA 950 graphics, and has a PCI Express x16 slot. I am using the original 1024x768 monitor. A GT 710 is relatively cheap, and should be easy to install. Would it significantly reduce the load time for complex web pages?

---

### Post by Autodave on 2018-08-20
A better graphics card will *slightly *help load time, but nothing really great. However, since you now have a decent machine, a cheap graphics card would probably be a good choice for the next improvement.

---

### Post by Holger_Gehrke on 2018-08-20
Probably not. Your example news.google.com is 4.5 MEGABYTES, most of which is JavaScript. It ends up making over 100 network requests for various additional bits and pieces - 60 images, some more JavaScript, a few CSS-files and a lot of small JSON-files. The JavaScript does a lot of DOM-Manipulation which necessitates complete recalculation of the page layout. A more powerful graphics board won't help with that.

Holger

---

### Post by geofftf on 2018-08-20
> **Holger_Gehrke said:**
> Probably not. Your example news.google.com is 4.5 MEGABYTES, most of which is JavaScript. It ends up making over 100 network requests for various additional bits and pieces - 60 images, some more JavaScript, a few CSS-files and a lot of small JSON-files. The JavaScript does a lot of DOM-Manipulation which necessitates complete recalculation of the page layout. A more powerful graphics board won't help with that.

Holger
I feared that would be the case. It should save a little memory, but I now have plenty with 2 GB. It should also save a little contention for memory. The graphics processing will also be quicker, but there probably is not much to do. Firefox can offload some processing to the GPU, but, again, I doubt whether that would be noticeable.

I am comparing this old PC with a Haswell i5 4460, which is about four times as fast. That is inevitably going to be faster.

---

### Post by Yellow Pasque on 2018-08-20
I would still try and add a cheap, passively-cooled GPU if I planned on seriously using this system. The GMA950 is woeful (only OpenGL 1.4 and no H.264 decode accel).

---

### Post by geofftf on 2018-08-20
I have done a couple of experiments. Scrolling in Firefox has been flicking. I tried turning off "Use hardware acceleration when available". That seemed to marginally improve scrolling. I turned off "Smooth scrolling". That was much better. The scroll moves in jumps, but everything moves cleanly together. Again, if anything, the scroll is better with hardware acceleration turned off.

The GT 710 that is was considering fitting was the passively cooled 1 GB version.

---

### Post by geofftf on 2018-08-21
Those modifications have made a huge difference. Firefox scrolling is much better. Google News now loads in 4 seconds over a 10 Mb/s line. More to the point, the images are displayed immediately, so that I can scroll down immediately. Using graphics acceleration with the GMA 950 clobbers the performance. Perhaps putting in a half decent GPU would enable hardware acceleration to give a tangible benefit. I can only accommodate a half height card, and I only have a 250 W power supply. Nonetheless, the MSI passively cooled 1GB version of the FT 710 comes with half height brackets and only consumes 19 W, or probably less with 2D graphics.

What we really want is someone who has an old machine with a graphics card who can compare the performance with and without using the card.

---

### Post by geofftf on 2018-08-21
It is not up to date, but I found this:

[https://helgeklein.com/blog/2014/12/impact-gpu-acceleration-browser-cpu-usage/](https://helgeklein.com/blog/2014/12/impact-gpu-acceleration-browser-cpu-usage/)

This article leads me to doubt whether hardware acceleration would help me even with a powerful GPU. It appears to increase CPU for the basic stuff, and I have the original PCI Express, which is half as fast as PCI Express 2.0. The web is full of sites saying that Firefox hardware acceleration causes all sorts of problems and worsens performance rather than improving it.

---

### Post by abe532 on 2018-08-25
> **geofftf said:**
> Those modifications have made a huge difference. Firefox scrolling is much better. Google News now loads in 4 seconds over a 10 Mb/s line. More to the point, the images are displayed immediately, so that I can scroll down immediately. Using graphics acceleration with the GMA 950 clobbers the performance. Perhaps putting in a half decent GPU would enable hardware acceleration to give a tangible benefit. I can only accommodate a half height card, and I only have a 250 W power supply. Nonetheless, the MSI passively cooled 1GB version of the FT 710 comes with half height brackets and only consumes 19 W, or probably less with 2D graphics.

What we really want is someone who has an old machine with a graphics card who can compare the performance with and without using the card.
.
Hi geofftf, you have such.
(the leaning towards using lower case around here leads me to think I might be the only grey-beard over here?)
Instead of binning an old little used Pentium PC, decided to play Linux. Have spare GT 710 GPU.
Now, someone please tell me how to start?
Have downloaded Lubuntu image, do I just flash it to a HDD after giving Bill Gates a Format:C: ?
Abe53.

---

### Post by geofftf on 2018-08-27
Put a blank DVD in the DVD drive. Right click on the downloaded iso file. Select Burn. Tick the box to verify after burning. Boot with the newly burned DVD in the DVD drive. You may need to select the DVD drive as the boot drive by going into the boot menu, or alter the boot priority by going into the BIOS.

---

### Post by geofftf on 2018-09-10
Here is a very helpful assessment of the GT 710:

[https://www.youtube.com/watch?v=1b9mGdsL2Vg](https://www.youtube.com/watch?v=1b9mGdsL2Vg)

His assessment is that the card is useless for modern machines. The integrated graphics is better. He says that what it will do is improve video playback on an old machine and provide DVI and HDMI outputs in addition to the usual D-SUB. He also says that it will speed web page rendering on an old machine, but says that his old machine is fine for web browsing. His old machine is not as old as mine, but it is weighed down by Windows.

Web browsing is mostly fast on my old machine, but not quite as fast as on my fourth generation Haswell i5 4460. Youtube full screen video playback is good on a 1440 x 900 monitor for some videos, but is a little jumpy on some others.

---

### Post by pqwoerituytrueiwoq on 2018-09-10
While i do agree with that assessment, your onboard graphics are a joke compared to modern integrated graphics, so a low end card would be helpful for it, i would not spend a lot on it for a system that old probably just slap a 1gb GT 430/520/610 what ever i get around $15 to 25 $ used that the power supply can handle
installing a gpu will free up what little ram your system has for the system to use as a integrated gpu reserves some ram for it (can usually be adjusted in bios)

My mom's system was starting to feel slow to me with basic web usage Phenom II 965/GT 430/4GB DDR3 1333 (single channel)
I slapped a second ram stick in there and it feels fine to me now (8GB DDR3 1333 dual channel)
* If someone here wants to lecture me about mixing ram sticks i under-clocked the new one to match the old one

Firefox will use more ram if it has more available to it, on my system firefox and it's child processes are using 3976.4 MiB (i5 4690k@4.35Ghz/GTX 1060 3gb/16GB 4GBx4 1600 cl 9)
so i would not be surprised if ram is your biggest limiter, a video card would help with this as you would no longer be sharing system ram with a gpu, but it is still not much compared to what would be ideal

---

### Post by geofftf on 2018-09-11
I started with 1 GB and one memory channel and upgraded to 2 GB with two memory channels, which is the maximum for my motherboard. This upgrade speeded up web browsing a little. Doubling the processor power had a much bigger effect.

My BIOS says:

[B]Video Configuration

DVMT Mode <DVMT>
IGD DVMT Memory <128MB>
Primary Video Adapter <Auto>[/B]

There is scope for some saving here:

[https://www.techarp.com/bios-guide/dvmt-mode/](https://www.techarp.com/bios-guide/dvmt-mode/)

free -m with no applications running:

              total        used        free      shared  buff/cache   available
Mem:           1983         187        1283          42         511        1611
Swap:          2047           0        2047

Memory used by the BIOS = 2048 -1983 = 65 MB

free -m with Firefox running and playing a Youtube video:

              total        used        free      shared  buff/cache   available
Mem:           1983         546         788          86         648        1206
Swap:          2047           0        2047

The BIOS is still using 65 MB.

The space used for video appears to be minimal. The recommendation appears to be to leave the BIOS graphics settings as they are when using a graphics card. Firefox grabs a lot of space for cache, but gives it up when it is needed elsewhere.

The Lubuntu community was not at all happy when the developers dared to recommend 2 GB of RAM rather than 1 GB. Nonetheless, I would not recommend that anyone goes out and buys a 1 GB machine to run Lubuntu. It will run fine, but there will not be much elbow room.

This guy is playing games with a GT 710 and a machine with a similar specification to mine:

[https://www.youtube.com/watch?v=TrTJj6ThxZQ](https://www.youtube.com/watch?v=TrTJj6ThxZQ)

---

### Post by geofftf on 2018-09-18
I found this:

[https://www.linuxquestions.org/questions/linux-newbie-8/a-graphics-for-older-machine-4175605193/page2.html](https://www.linuxquestions.org/questions/linux-newbie-8/a-graphics-for-older-machine-4175605193/page2.html)

It appears that there can be problems with Firefox and other software failing to make full use of the GT 710.

I installed youtube-dl, which installed mpv as dependency. Playing YouTube videos directly with mpv is terrible. The video keeps pausing. It does not do that with Firefox. Firefox playback is almost perfect, and the CPU utilization is not particularly high, but can peak at nearly 100% in full screen mode. Downloading the video with youtube-dl and then playing the downloaded file does, however, appear to give perfect playback. A side effect of installing mpv is that Gnome MPV will now play YouTube videos, which it did not do before, but just as badly as mpv does directly.

The graphics of my old machine appears to be doing a decent job. Installing a graphics card makes no economic sense. The graphics card would cost more than I paid for the machine, even if I include the cost of the additional memory and used processor. If I add the cost of the graphics card to the cost of the cost of my old machine, it is roughly the cost of modern used machine with graphics as good as the GT 710, and much better in other respects too. Nonetheless, any improvement in Firefox performance over my existing machine would be marginal, at least until websites become more heavy. My old machine is doing a decent job for now, and the price of used machines can only be expected to fall.

---

