---
title: "Will memory work to boost the computer"
date: 2019-11-26
forum: Hardware
---

### Post by vanquishedangel on 2019-11-26
So I have taken a new position at a non profit and am a house manager of a group home, however, the computer is slow.

It is an HP p2-1317cb. It has an AMD 1800 processor (dual core, 1.7 ghz), 6 gb ram, AMD 7340 Graphics.

Now this computer is used for work and is really efficient energy wise. It logs for residents and it hold the client files, all it needs to do. So replacing it is not required. The problem is it is slow at loading webpages and things, or video, or when many things are open.

I checked on a hunch how much vram (shared with computer) it has, it is 385mb. I suspect that this is a major part of the slowness as the monitor is newer and is 1920 x 1080p and is connected via a vga connection. My thought is if I upgraded the ram to 8GB (its max) that the computer would allocate more towards hardware dedicated memory (including graphics) and this would speed things up. It has a 30GB internet connection so that is not an issue. Upgrading the ram would cost about $14-$25.

---

### Post by cybrsaylr on 2019-11-26
Open up your System Monitor and look at what 'Resources' shows. This will give you an idea of how much you are pushing your PC.  Opening up many things will slow down any PC.

As far as RAM goes, you can never have too much RAM. More is always better.

---

### Post by oldfred on 2019-11-26
I also suggest an SSD, even if just a small boot drive.

When a small SSD dropped below $100 in 2011, I purchased it planning on using it as a boot drive in a new UEFI system in 2012. But it sped up my old BIOS system enough that I could not really justify new system until about 3 years later.

Systems need balance on CPU, graphics, RAM, and drives. Over spending on one does not speed system up as much you you may think. 
But I have found even with fast SSD, fast Internet, that the biggest bottleneck seems to be between chair and keyboard. Typist in fact seems to keep getting slower (may be related to "old" in oldfred?

---

### Post by CatKiller on 2019-11-27
SSD. Definitely.

With RAM it's not the case that more will be faster, it's that running out cripples everything. If you *have* free RAM, the system will use it as a disc cache, so things that you've loaded before don't need to be loaded again, which helps if your computer has been on for a while and you keep doing the same things.

Old spinning rust drives aren't actually that bad for throughtput, but they're terrible at random access. Unfortunately, most computer use is random access. An SSD is awesome at random access. It's the best bang-for-the-buck performance boost for everyone.

You'll probably also benefit from installing some extensions to the browser to stop every site running a bajillion javascript applications on every page; an ad-blocker, or NoScript, or something like that.

---

### Post by Autodave on 2019-11-27
You are very unlikely to notice any difference at all in going from 6 to 8 gig RAM.  An SSD will give you instant, noticeable speed increase.

---

### Post by TheFu on 2019-11-27
I had an AMD Athlon 1800+ and replaced it with an AMD Athlon  2000+ CPU in the early 2000s.  A $35 raspberry pi will be faster and have better GPU capabilities for video playback.
 AMD 1800 passmarks: 300

Memory won't won't matter since you already have 6G.

A SATA SSD will help.

---

### Post by mörgæs on 2019-11-27
You didn't say which OS is running so I guess Ubutnu.

If you have a need for speed you could try a fresh install of a lighter Buntu. Also take a look at how stuff is distributed (classic repository or Snap).

---

### Post by Yellow Pasque on 2019-11-27
> **TheFu said:**
> I had an AMD Athlon 1800+ and replaced it with an AMD Athlon  2000+ CPU in the early 2000s.  A $35 raspberry pi will be faster and have better GPU capabilities for video playback

No. It's an E2-1800 "Zacate" chip circa 2011-2012.

> I checked on a hunch how much vram (shared with computer) it has, it is 385mb. I suspect that this is a major part of the slowness 

Probably not. Video RAM is allocated dynamically in modern IGP systems. I don't think adding 2GB would help you significantly. Now if you would completely replace the DDR3L-1333 RAM with DDR3L-1866 (assuming the system supports that), that would give more bandwidth to the APU and you might notice a difference. That's going to be a bit more costly though and the SSD is a better upgrade bang for buck-wise.

---

### Post by TheFu on 2019-11-28
E2-1800 passmark is 800.  A slow chromeook is 1000 and a fast chromebook is 3000.

For video playback or streaming, a r-pi with a dedicated mpeg2/h.264 decoder would still be faster.  The chromebooks also have mpeg2/h.264 decoders.

Between 2010 and 2015, pretty much all the GPUs got dedicated video decoders which make a huge difference for video playback.  I have an AMD-E450  (750 passmarks) that could only play 600p videos, which wasn't an issue with before the world went hidef.  Then it needed to be replaced.  I'd already replaced it with a $50 pentium CPU before the F/LOSS GPU drivers took over.

---

### Post by crip720 on 2019-11-28
Quite a few people are suggesting a SSD, before you buy one make sure your system has sata 3 or the speed difference will not be as great as you hope.

---

### Post by Yellow Pasque on 2019-11-28
> **crip720 said:**
> Quite a few people are suggesting a SSD, before you buy one make sure your system has sata 3 or the speed difference will not be as great as you hope.

The system only has SATA-II (300 MBps). An SSD will still be significantly faster than a hard disk in real world usage.

[QUOTE=TheFu]For video playback or streaming, a r-pi with a dedicated mpeg2/h.264 decoder would still be faster. The chromebooks also have mpeg2/h.264 decoders.[/QUOTE]

The E2-1800 has UVD3, which is a dedicated video decoder block (including mpeg2/h.264). That doesn't help in Linux web browsers, though, since they don't have hardware video decoding (except the experimental chromium-vaapi PPA). The h264ify extension might help on YouTube.

---

### Post by vanquishedangel on 2019-11-29
> **mörgæs said:**
> You didn't say which OS is running so I guess Ubutnu.

If you have a need for speed you could try a fresh install of a lighter Buntu. Also take a look at how stuff is distributed (classic repository or Snap).

Windows 8.1 actually. But I am an avid Linux  user. I just wanted to ask you guys because I feel you know more, and the ram upgrade is$14 so I can justify it, the task manager says 2.5 gigs used and 3 gigs cached with 428 megs dedicated for hardware. I bought faster ram the computer is able to use, from 1333mhz to 1600mhz, 8 gigs. It may cache more with the new ram. My thought was the bios has no setting for dedicated ram, though it is most likely dynamic. It might set aside more for hardware if the ram capacity is maxed out. The inter net should not be slow but it is, when loading pictures like at Walmart.com. The slowness seems to display graphics related. Though the cpu does go up to 100 percent while loading pages but then down to 5 percent. I also noticed that there is 2gigs of virtual memory allocated. I suspect this is in use.

Side note I replaced the wall paper with a 120 byte black square.

---

### Post by CatKiller on 2019-11-29
> **vanquishedangel said:**
> The inter net should not be slow but it is, when loading pictures like at Walmart.com.

Every site you visit will try to run dozens of additional programs. They don't have to come from the actual site you're visiting and, since JavaScript is Turing-complete, they could be doing literally anything; normally what they're doing is tracking your activities across the internet. Those all need to be downloaded from wherever, which takes time and bandwidth, and running them takes processing capability that, frankly, you don't have to spare. There are plenty of extensions available, for all the browsers, to get those scripts under control. Online advertising is a vector for malware, removes whatever privacy you think you might have, and makes your internet experience slow and unpleasant. And they're using your resources to do it.

---

### Post by TheFu on 2019-11-29
I'm with CatKiller on all the other programs that get run.

There are many techniques to prevent many, but not all.  Some work by controlling DNS, like **pi-hole** does.

Others work by limiting access to hundreds of thousands of advertising/tracking sites, with the /etc/hosts file. This works best for portable devices, but isn't as convenient as running pi-hole somewhere on your network.  [https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279) explains.  I use this. My /etc/hosts file has 
```
$ wc -l /etc/hosts
131537 /etc/hosts
```
131K lines to block ads, trackers, and specific social networking sights I consider abusive.

Lastly there are different javascript/ad blockers as browser addons.  These tend to be a hassle for non-technical users and almost all ad-blockers eventually sell-out to allow ads for payment.  **NoScript** is the normal browser addon for this.  By default, I block all javascript, then only allow a few specific domains.  Tracking domains aren't allowed.  If a website doesn't work without lots of trackers, I stop visiting. "Lots" to me is 2.  If i dont haven't any choice and must use a website, then I'll run a separate browser instance inside a **firejail** in "Private" mode.  This doesn't allow anything to be written to disk. Nothing. It does use more RAM and it is more hassle, but there are only a few sites like that and they aren't on my daily-use list.  I've never trusted incognito modes. Browsers are so complex these days that incognito mode seems to always misbehave.  Must easier to use firejail --private.

In the end, there isn't much to be done when a CPU is slow other than to use a different device, try to use the "mobile" version of the website, or use a stripped down browser that doesn't support most of the capabilities that really slow browsing.  Try running **dillo** as your browser. Websites are really FAST with it, if they work.   UbuntuForums doesn't work in dillo.

RAM buffers in Linux are used in a priority method. If programs need the RAM, it is used for programs. If disk storage needs it and some is available, it will be used for that. Same for network, though having large network buffers usually is a terrible idea for network performance.  **free -hm** will show disk buffer use.

Replacing the desktop image probably doesn't matter for performance, assuming you aren't using a 50MB or larger image.

---

### Post by mörgæs on 2019-11-29
If you haven't tried Buntu yet then give it a spin before buying additional hardware. One can't predict the page loading speed under Xubuntu from Windows experience. 

Agree on the privacy-and-speed-savings tips above.

---

### Post by Yellow Pasque on 2019-11-29
> **vanquishedangel said:**
> I bought faster ram the computer is able to use, from 1333mhz to 1600mhz, 8 gigs.

The system doesn't officially support > DDR3-1333 from what I've read. I was just brainstorming. If you actually did that, you probably wasted money..

---

### Post by RobGoss on 2019-11-30
Adding a **SSD** is a great start for increasing your machines speed. I swap all my mechanical drives for SSD's and it's a big different is speed

---

### Post by vanquishedangel on 2019-12-02
So I have received the ram and it is installed, things actually did improve though not a whole lot. I suspect though that the reason is because the ram installed originally was 2 different brands. Hynix, and micron, and two different sizes. The jinx was 2 gig and the micron was 4 gig. This thing has single channel memory so I suspect that may have cause issues. 

This machine has no room for upgrades like even a low wattage graphics card (like and AMD radeon 7450) or that. The ram was all that can be upgraded. Perhaps switching to a DVI cable instead of vga but that is all. I would say $14 was well spent. Possibly and sad would help, if I can find a cheap one but I am not sure windows would play nice, maybe use a old flash drive for readyboost.

---

### Post by mörgæs on 2019-12-03
So, can the thread go to 'solved'?

---

