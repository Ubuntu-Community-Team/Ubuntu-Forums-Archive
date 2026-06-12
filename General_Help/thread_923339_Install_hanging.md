---
title: "Install hanging"
date: 2008-09-18
forum: General Help
---

### Post by cgaudio on 2008-09-18
Hi, Thanks in advance for giving me a hand here!

I'm just starting, so If I'm in the wrong place, somebody please point me. 

I have a HPa450n with a gig of RAM.

Installing from the Gutsy CD, I get the logo and the progress bar, but after a couple minutes the graphics go crazy and a couple minutes after that, I get rolling yellow screen. 

Couldn't make heads or tails out of the "booting problems page, but tried appending noapci to the path. 

Here's some more things I've tried that didn't work: Add "grub" to quiet splash--, delete quiet splash, delete quiet splash and add grub there, delete intrid.gz quiet splash, delete intrid.gz quiet splash and add grub, delete casper/..., delete casper/... and add grub. 

This is my first experience with Linux so, when answering, assume that I know NOTHING. (I got sick of Windows crashes and loved the on-line Ubuntu demo.) 

Thanks!
-Chuck

---

### Post by phidia on 2008-09-18
> Installing from the Gutsy CD, I get the logo and the progress bar, but after a couple minutes the graphics go crazy and a couple minutes after that, I get rolling yellow screen.

That doesn't sound like something you should see during an install-are you trying to install or boot after a successful install?

Anyway if you have a video issue you can try and reconfigure your xserver by opening another commandline window ( press the Alt+Ctrl+F1 keys ) then type > sudo dpkg-reconfigure xserver-xorg if the doesn't work you can try > xfix see if that gets your xserver working correctly again.

---

### Post by cgaudio on 2008-09-20
Thanks for answering! 

I am not booting, just trying to install for the first time on a clean HD (no OS), using the Gutsy CD. 

When the Ubuntu menu comes up, I push F6, then when I push Alt Control and F1, nothing happens. 

Now what??
-Chuck

---

### Post by Monotoko on 2008-09-20
Can you boot up using the CD? (assuming its a live CD)

---

### Post by stickmangumby on 2008-09-20
It sounds like you are trying to boot up a Live CD to install Ubuntu, and can't get it to boot to the Live CD desktop. Is this correct?

If this is the case, I'd recommend downloading the Alternate install CD if bandwidth is not a problem. This provides a text based install option, which will install the same Ubuntu, but seems to work in a lot of cases where people have trouble using the Live CD.

If you can't download this for any reason, post back here and we'll go from there.

---

### Post by Sef on 2008-09-20
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Have you gone down the list instead of installing to 'Check Disk for Errors'?

---

### Post by cgaudio on 2008-09-22
I have tried every option on the CD menu including the tests (which ran fine), and can't get Ubuntu installed. I don't see an option to run the program right off the CD.
Thanks!
-Chuck

---

### Post by cgaudio on 2008-09-22
I'll try it. Thanks! Looking for it on the Ubuntu site...
-Chuck

---

### Post by cgaudio on 2008-09-22
> **Sef said:**
> 1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Have you gone down the list instead of installing to 'Check Disk for Errors'?

Sef, I think you missed the part about me being a beginner.
Thanks!
-Chuck

---

### Post by cgaudio on 2008-10-20
I really appreciate everybody trying to help. Here's my latest attempts. After a few tries, I did download the Alternate Ubuntu. I DID burn it at 4x. When I tried to boot with it, I got an error message indicating that I needed to insert a boot disk. I put in the Ubuntu Gutsy CD and when I got the menu, changed to the Alternate disk. Nothing. Pushed every button/function, still nothing.

Went to the HP site to get the boot software for this box. This is cut from the page,
"    
Which operating system is used with your product?»  Microsoft Windows XP  

Don't see your operating system?If you do not see an operating system listed on this page, then it is not supported by this product. 
"

So I can't get boot software from them for a Linux OS, nor, apparently for any OS other than WXP. Does this make sense??


So here's where I am: I have the original Gutsy CD and a fresh-burnt Ubuntu Alternate CD.   ...But no cigar. 

Am I screwed???
-Chuck

---

### Post by Dynamo_Joe on 2008-10-21
Hi cgaudio, 

If you had burnt the live CD correctly then: 
1. Set your BIOS to boot from the CDROM first. 
2. Boot the live CD. 
3. On the menu screen, after selecting your language, press function key "F4" to boot in "Safe Graphics Mode".
4. The install should continue on nicely from there. 

If the install hangs approximately around 5% to 15%, then format the HD into "ext3" first from the live CD environment. This has happened to me before and the install just stops dead. Pre-formating it to "ext3" first always seems to clear this little hurdle. 

Good luck!

---

### Post by cgaudio on 2008-10-21
The Gutsy, I bought; the Alternate, I burned at 4x.

Brought up the Gutsy menu, pushed F4, got a drop-down with resolutions, chose 800x16, then chose Safe Graphics mode. Same crash as usual. did this a couple times. 

Got the Gutsy menu, chose Install with driver update CD. Changed to Alternate CD. Instructions said to re-insert CD, did with no result. re-inserted Gutsy, same crash.

Addended ext3 to command line, pushed Enter, Got command to Enter driver CD, put in the Alternate, didn't work, went back to Gutsy, same crash.

Put ext3 after casper    ...casper/ext3  <enter>  Nothing happened. Put ext3 efore casper-nothing. Trying it after seed boot caused a Kernel Panic crash.

Thanks for the help. I hope I followed your instructions. 

I've had this OS over 2 months and can't get it to load. Very frustrating.
Thanks again!
-Chuck

---

### Post by cgaudio on 2008-11-07
OK, 2 more weeks without any help, so here's some more things I've tried: It turns out that there is another versuin of Ubuntu besides the alternate. It is the AMD version. I downloaded it at 4x, and gave it a shot. It wouldn't boot the computer. The only CD that will boot the computer is Gutsy. I have tried booting with Gutsy then changing the CD-no dice. 

For somebody coming in late, I can't seem to get get Ubuntu installed on my HPa450n.

All help, and attempts at such will be appreciated. I'm going on 3 month with an OS I can't use.
-Chuck

---

