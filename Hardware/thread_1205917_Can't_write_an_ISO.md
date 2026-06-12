---
title: "Can't write an ISO"
date: 2009-07-06
forum: Hardware
---

### Post by LittleKoy on 2009-07-06
Lately I've had a lot of problems with burning. I bought 15 tdk dvd-r, and failed about 13 (!!!). I tried 3 different recorders, two OS and 4 different programs, but none of them could make it, so I put the blame on the dvd.
But now I'm trying to burn an ISO on a CD using a Plextor px-860sa. I tried Brasero, Nero Linux and K3b, but none can burn it. I could burn those CD very nicely with my crappy old recorder, but I can't with my brand-new Plextor. Something IS wrong :( Couldn't it be an OS-side problem? Or an hardware compatibility issue?

I saved the logs

---

### Post by JC Cheloven on 2009-07-06
> **LittleKoy said:**
> I tried 3 different recorders, two OS and 4 different programs, but none of them could make it, so I put the blame on the dvd.

That's terrible, though. 
[INDENT]3 recorders => 3 different "toasters"
2 OS => linux & windows (most likely?)
4 programs => brasero, k3b, nero ...(as you said)[/INDENT]
If the above is right, I'd consider an exorcism :-D 

Even if yor OSes are two linux distros, 3 toasters are very unlikely to fail altogether. Perhaps something is wrong in your motherboard. 

Sorry to not have a more clever bet. It is way too strange.

---

### Post by LittleKoy on 2009-07-06
> **JC Cheloven said:**
> That's terrible, though. 
[INDENT]3 recorders => 3 different "toasters"
2 OS => linux & windows (most likely?)
4 programs => brasero, k3b, nero ...(as you said)[/INDENT]
If the above is right, I'd consider an exorcism :-D 

Even if yor OSes are two linux distros, 3 toasters are very unlikely to fail altogether. Perhaps something is wrong in your motherboard. 

Sorry to not have a more clever bet. It is way too strange.

Here is my situation, a bit more detailed:

I bought a bunch of TDK dvd-r colour

Desktop->old burner = fails with Ubuntu + brasero, k3b and Nero Linux.
Laptop->2yo burner = fails with Ubuntu + brasero, k3b (but I could make 1 right), Nero Linux and Windows XP + Nero 7

So, since my desktop recorder was pretty dated, I purchased a Plextor px-860sa. But:
Desktop->plextor = no better than old burner.

I blamed the dvd, because it's simply impossible for so many different configuration to fail so badly.

But now I'm trying to burn karmic iso on a Philips cd. I burnt several of those cd and never had a problem. But now I'm failing miserably, all of the programs telling me something like "Cannot send CUE sheet" or something like that. That's why I was wondering if there was some issue with plextor+ubuntu.

All of this is very frustrating, I never had a problem before.
At this point, if you know how to make an exorcism, I might seriously try :(

---

### Post by JC Cheloven on 2009-07-06
Well, I'd really like to help, but I'm admittedly a bit lost. The facts that you used to burn cd-dvd's with no problem, and the fact that some (seldom) times you still get a valid copy with k3b, are confusing to me. So let's brainstorming a bit:

- have you tried to burn at lowest speed?
- have you checked that your toaster supports the dvd "+R" or "-R" option, as applicable? Ditto for the settings in the program.
- have a look in places -> computer (if using gnome desktop). Your burner should appear with options such as CD-RW, DVD+-RW. Are they as expected?
- I had myself problems burning disks in the past, but instead of starting brasero or whatever, I left-click the iso image and choose "burn to disk". This worked for me. Have you tried it?
- If you have enough ram, you could try to burn from livecd, to see if it makes any difference.

Best of luck.

---

### Post by zepita on 2009-07-06
try swapping the PATA or SATA cable for a new one. It's a common soultion  whenever you have unexpected results.
Sometimes may be the PSU, so double check with another one or try any of your burners in another computer.

I hope it helps

---

### Post by LittleKoy on 2009-07-07
@JC Cheloven

- Yes, my lowest possible speed for cd is 4x. Tried but no luck.
- Yes, it supports cd-r
- As expected
- I have "Write to disk", but it only triggers brasero, that obviously fails
- Tried but same result

Thanks anyway :(

@Zepita

I don't think that's the problem, I think it's OS-side. But I'll try when I have a second SATA cable..


News:
I went around googling
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'

I found something interesting:
[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/149076](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/149076)

especially this:
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076/comments/57](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076/comments/57)

I can't say this solved my problem, but that line or warning disappeared. The rest is the same as before..

---

### Post by diesal3 on 2009-07-07
have you tried brasero?

---

