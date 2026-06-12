---
title: "Multiple issues - MSI Mobo Internet and CD Burns"
date: 2022-07-29
forum: Hardware
---

### Post by sdsurfer on 2022-07-29
Posting this in Hardware because the second problem **may** by my burner, not sure. Recently updated my comp, love it, it is a screamer and way better than what I had, except for these two things. Specs:

Board: MSI B560M Pro-VDH
CPU: 11th Gen Intel® Core&#8482; i7-11700K @ 3.60GHz × 16 
GPU: GeForce 8400GS/PCIe/SSE (Yeah old, but it works for what I need)
RAM: 64 GB (overkill, but wanted to avoid RAM issues, board supports 128GB)
Internal drives:
 - 500 GB Western Digital (Windows 7, I never use it any more, grub menu)
 - 1 TB Western Digital (Ubuntu 18.04 OS only)
 - 2 TB Western Digital (all data only)
 - LG HL-DT-ST DVDRAM GH22NS50 (DVD/CD internal, brand is "LG.")

OS: Ubuntu 18.04 LTS (I haven't upgraded due to concerns about problem #1) ***(Edit: see below, now updated to 20.04)***

Religiously install updates as requested (root of problem #1.)

**Problem #1:** The OS repeatedly doesn't recognize the onboard Ethernet of the B560M. Whenever the system updates, it replaces/removes the kernel required to recognize the internal Ethernet. When it does that I run the r8125-9.007.01 executable and it immediately enables the Ethernet, all good until the next update. Aside, this **might** go away if I update to 20+, but not knowing, I am hesitant. I've been to all the posts to make this permanent, none of them appear to work, whenever I get an Ubuntu base update that updates the kernel, I have to rerun this executable to get the Internet (and local network)  working again.

**Problem #2:** this is the one that is driving me absolute bonkers. I have had my vehicles broken into and CD's stolen three times, we are talking thousands of dollars. My intention is only to copy CD's for the purpose of personal use in my vehicles with the originals in a safe at home.

This first appeared in the stock audio player in my 2003 Toyota Tacoma. I  also have a Pioneer home CD player, one of those 6-disk changer models (yeah I know, old school lol) and when it was broken in the Taco, it was broken in the Pioneer. Pop it in either Linux computer and they play fine (the MSI and my System76 lappie.)

 Using Brasero 3.12.1, I am doing direct disk copy - makes an image file on disk (temp is set to the newer 2 TB drive.)  I started with Verbatim 52x CD-R (not RW) and it seemed to work, but on some of these at about track 5 through 7, strange background artifacts appeared - background static, a rhythmic hiss, basically white noise rendering any of the later tracks at the outside of the disk a horrible experience in auditory assault.

**Things I have tried:**
When first discovered it was just the last two tracks of an album. I copied the .wav files to the internal drive, opened the offending tracks in Audacity, and re-saved them as new tracks, then created a new Brasero audio project, and it worked. For one CD. In a subsequent CD, it did not work - same hissing static.

The rest of the CD's are totally hosed and exhibit the same symptom: at about track 5 through 7 out of 10-12, the pulsing static begins.

From various articles, it is recommended to turn the burn speed down for audio.** Brasero only lets me go to 2x.** Same problem.

Now it gets really fun. Basically throwing money down the drain on worthless CD's, I decided to go cheap and bought a 50 pack of myeco CD's. Biggest waste of money ever (although not most expensive.) These things pop back out of the Taco CD player in 30 seconds, without playing a single track. In the home stereo they just throw a disk error. Put them in a computer and they're fine, but I don't need them in a computer, I need them for road trips!

So I have a stack of myeco CD's I might as well toss in the trash.

The one common factor I can see is that the tracks that are getting hosed up are always the ones toward the edge of the disks, from track 5-7 through the last track.I even saw someone mention that is was the reflective material of the CD's that was the issue, they put a label on the CD and it was fine. It may sound insane but at this point I'm about to try it - if I could find any labels for CD's!

Has anyone got any ideas? At this point I'm about to replace the internal CD/DVD drive with an Asus DRW-24B1ST or the newer Plextor, if throwing more money at it will help I'll do it. Eating beans for a week is fine by me if this gets out of my head. :-D

---

### Post by guiverc on 2022-07-29
My thoughts, and I have no answers sorry.

problem 1 - you didn't give any details as to which kernel stack you're using, ie. if you're using HWE then 18.04 is using the same tack as Ubuntu 20.04 LTS using the GA stack, thus I'd say its possible you'll have the issue you do currently on upgrades; but 20.04 using the HWE stack as you're using now could be very different (ie. kernel modules or *drivers* could be different).  You didn't give enough details of what you're using with your 18.04 system.

[I]If you want more details on kernel stack choices for Ubuntu LTS releases; there are multiple links but [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) is a start.
[/I]
As for CDs, on some older players I used to find getting a black texta/marker and just darkening the very outside **edge** used to help some older players.  I'm not talking about the surface it reads from, just the outer edge itself where your fingers usually grab the media. It's not a long term fix (*esp. if you grab it on the edge*), but you can always do it again. It worked with some cheaper media, where I found it wasn't needed for better branded media (eg. I never used it on original Kodak *gold *CDs).  It's no *magical bullet*, but something that maybe worth a try (*and it's more useful for data where you're closer to the edge where you describe the issue*).

Another thing, I've found my last writes have killed a few writers, but I'm using them on old equipment, and my replacement drives are salvaged from boxes at least as old (ie. >10 years old). If the writer is old; it maybe writing badly, however if you can read the disk fine on other computers, I doubt this is your issue  (*being able to read it on the drive you wrote with though doesn't mean much; esp. if you failed to close the disc*).

---

### Post by oldfred on 2022-07-29
Usually a system that new needs newer version of Ubuntu.

And you are crippling your graphics with that old card. CPU graphics almost 10 times better:

```

Intel UHD 750          1757
GeForce 8400 GS       129

```
[https://www.videocardbenchmark.net/mid_range_gpus.html](https://www.videocardbenchmark.net/mid_range_gpus.html)

I was doing some similar with my then new Skylake system. (new numbers now shown bit different)
```

GeForce GT 620                     430
Intel HD Graphics                   927  Skylake

```

---

### Post by sdsurfer on 2022-07-29
So are you telling me the Nvidia affects the functionality of the onboard Ethernet and the issue with burning CD's? :-\

The  CPU graphics and board don't support dual monitors, the Nivida is a  dual head card and as I said does what I need it to do - drives two Benq  monitors. 

> .  You didn't give enough details of what you're using with your 18.04 system.

While  I'm not sure exactly what this means (I did read the article) you are  probably on to something here. When I installed the new MSI board, I  just ran Ubuntu off the old hard drive and everything appeared to just  work (except the Ethernet driver.) It's entirely possible it's not  reading the new hardware correctly (?) 

> darkening the very outside **edge** used to help some older players

I  came across this technique in discussions of "old" copy protection  technology, the way they described it was the very outside edge of the  disk is where data tracks are stored. They "blacked out" the edge of  original CD before making a copy and it got around this copy protection.  I haven't tried it yet but will give it a shot, they're already useless  so no harm no foul.

Forgot to mention I also have an Asus  external CD/DVD drive I use for the System76 lappie, tried burning one  there and got the same result.

---

### Post by guiverc on 2022-07-29
> **sdsurfer said:**
> 
While  I'm not sure exactly what this means (I did read the article) you are  probably on to something here. When I installed the new MSI board, I  just ran Ubuntu off the old hard drive and everything appeared to just  work (except the Ethernet driver.) 


The 18.04 installation media used dictates what kernel stack you're using.

If you used 18.04 or 18.04.1 media, your system will use the GA kernel stack. If you used the 18.04.2 or later media, your system will be using the HWE kernel stack. Of course, either default kernel stack set by installation media used for install, can be changed post-install, which was the primary purpose of the link I provided (*also for generic information*).

Ubuntu 18.04 LTS released with the 4.15 kernel.

Ubuntu 18.04 LTS with the HWE kernel stack means it upgraded to 4.18 (from Ubuntu 18.10), then 5.0 (from Ubuntu 19.04), then 5.3 (from Ubuntu 19.10) before finally reaching the final kernel stack from Ubuntu 20.04 LTS ie. 5.4.  ie. the HWE kernel stack gets updated using stacks from later releases until it reaches it's final upgrade which is the GA kernel stack from the next LTS.

You didn't specify what kernel stack you were using.

If unsure which it is (*yes /var/log/installer/media-info would tell you what media you used, but it may have been changed*) I'd just use 

```
uname -r
```

Key detail is the first two numbers, ie. 4.15 will mean you're using the GA kernel stack, and 5.4 the HWE kernel stack (for Ubuntu 18.04 LTS). 

 If you see OEM in the kernel ID string you're using a specific OEM kernel stack for specific hardware detected at installation, and with a moved drive/installation from a different box, a wrong kernel stack will be used & problems are the result of the move (*without re-install so the installer can autodetect hardware, OR changing kernel stack manually to reflect box change*), though I suspect this is unlikely.

 I'd expect to see either GA (4.15) or 5.4 (HWE) kernel only.  and it's this detail that will give the clue I was trying to get at as for how you should expect 20.04 to run.  If using the HWE kernel stack on 18.04 (ie. 5.4 kernel), you could use the GA kernel stack on 20.04 (ie. 5.4) & results should be almost identical (*good and bad*), but we have choices with LTS releases of Ubuntu.

The easiest way to explore different kernel stacks, is just download a Ubuntu ISO that uses it, and have a quick [*live* test]("https://ubuntu.com/tutorials/try-ubuntu-before-you-install") on your actual hardware, as this requires no changes at all to your system. 

As 18.04 has both 4.15 & 5.4 available (*I'm excluding the other OEM options as that just complicates things; they're for specific hardware & thus of no benefit unless one matches your hardware*) you can have both installed as per the link I provided too (*some closed source kernel modules (ie. video drivers) can prevent both stacks from co-existing*) but before making any changes such as this (*esp. if using closed source kernel modules*) I'd use *live* media to see if the other stack performs well for you on your hardware (*esp. networking issue*).

FYI:  I didn't use it for any copy-protection issues; as I understood it, it was to attempt to reduce  light interference with the *disc* whilst in operation inside cars that usually have windows on all four sides (ie. *an attempt to reduce light reflecting into the lens*). It's simple and it'll help or not. I found it helped one brand of very cheap media I used on occasion.

---

### Post by Yellow Pasque on 2022-07-30
You need to use dkms if you don't want your ethernet module wiped out with every kernel update. Maybe something like this: [https://github.com/awesometic/realtek-r8125-dkms#launchpad-ppa-recommended](https://github.com/awesometic/realtek-r8125-dkms#launchpad-ppa-recommended)

---

### Post by him610 on 2022-07-30
> Problem #2....My intention is only to copy CD's for the purpose of personal use in my vehicles with the originals in a safe at home.
++1 Good idea. Some original CDs are out of production and difficult to find, and expensive if you do find them.
> Using Brasero 3.12.1....
I have experienced problems with Brasero in the past so I quit using it. I have only used Xfburn for several years now without any issues.

---

### Post by sdsurfer on 2022-07-30
Thank you all and will go through each of these. **New info: **I updated to 20.04 (and encountered lots of issues, but back up and running after 14 hours or so) and on first load, had to rerun the Realtek  ethernet driver update (20.04 didn't fix **problem #1 ** for me.) Probably still won't stick. Aside, kinda sad, 22.04 will roll out with updates next month and I'll have to do it all over again LOL

Yellow Pasque, that is exactly the driver process I use on kernel updates and think I tried this before but probably screwed something up, will try again.

> FYI:  I didn't use it for any copy-protection issues

I gathered that from the first suggestion, I only mentioned I stumbled across that info it in a copyright protection thread. Huxley was right, the truth would be buried in so much misinformation and white noise it would be difficult if not impossible to find it. :-P

---

### Post by sdsurfer on 2022-08-27
**Update:** Sorry for the late reply, been dealing with a lot of issues, and see 22.04 has just come out, hope to get that upgraded this weekend.

**Edit:** (Final, pretty sure!) the Asus burner came in, using Kb3, so far all burning successfully.
Kb3 warned device doesn't support 8x, burned at 16x, all good.

It appears **Problem #2** may be solved, but still experimenting here. I have a new Asus DRW-24B1ST on the way, but thought I'd give @him610's suggestion. I found xfburn more convoluted than I like, you have to create an ISO first then burn (guess I was spoiled by Brasero.)

What did appear to work, with my current burner, is installing and using K3b, which has the same functionality - insert disk to write, when temp is done, insert blank, continue. It appears to be way faster too. So far I am on my third CD and all tracks appear to play perfectly, testing each one as I go before burning another useless stack of computer-only CD's. :-P.

A side note, complete** fail with myEco CD's**, at least for audio. You'd think a CD is a CD, but apparently not, these appear to burn without error, when inserted into the player they still spit right back out. I still have to test if they're any good for straight data. 

I'm using Verbatim 700 MB CD-R's. When the new CD burner gets here I may just drop it in as a second burner, but it should be faster and more reliable, no real loss as it was only $30 new.

When I get a chance I'll install the script @Yellow Pasque suggested, just haven't gotten to it yet! Thanks again, you're all been very helpful.

---

### Post by oldfred on 2022-08-27
CDs are too small for Ubuntu.
And I stopped using DVDs years ago. Converted to flash drives as then they are reusable. Had too many coasters ( even used one as a coaster).
Now using external SSD or internal second drive to boot ISO directly to install. 

Using SSD and toram parameter (if you have enough RAM), I can install in 10 min. Restore from Backup. Longest time is still downloading a long list of installed apps. Only a bit manually configured anymore.

---

### Post by sdsurfer on 2022-08-28
> CDs are too small for Ubuntu.

This thread, in reference to CD's, is about creating audio CD's for backups to be used in in a vehicle that does not have MP3 capability.

>  to boot ISO directly to install. 

Discussion is not about install.

---

### Post by sdsurfer on 2022-09-24
Sorry for the delay but had to wait until I got a kernel update to test. Thank you @Yellow Pasque, this solution appears to have worked! One to install V 22 later today!

[https://github.com/awesometic/realtek-r8125-dkms#launchpad-ppa-recommended](https://github.com/awesometic/realtek-r8125-dkms#launchpad-ppa-recommended)

---

