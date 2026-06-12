---
title: "The UNR in my netbook is far worse than W Vista!"
date: 2010-04-24
forum: Hardware
---

### Post by ArchGabriel on 2010-04-24
Hey guys,

I just installed UNR (Ubuntu Netbook Remix) into my netbook (ACER Aspire One). I made two partitions: one for Windows Vista and other for UNR. My net HD has 250Gb (175Gb for Vista and 75 for UNR).
.
I did everything rigth during the installation proccess, but now, my UNR is very very slow. It is worse than any other OS that I've ever seen!
Does anybody know what is going on and how can I fix it?
If it is possible, I would like to solve this problem without formnating my HD.

---

### Post by akand074 on 2010-04-24
hmm, maybe a damaged disk? I'd try burning it at a low speed and reinstalling it. Otherwise I'm not sure why this is happening.. nothing is worse than Windows Vista.. :| aha.

---

### Post by ArchGabriel on 2010-04-24
> **akand074 said:**
> hmm, maybe a damaged disk? I'd try burning it at a low speed and reinstalling it. Otherwise I'm not sure why this is happening.. nothing is worse than Windows Vista.. :| aha.

:confused: Sorry, this may sound a very stupid question, but I am new at this thing. How can I "burn it in a low speed"? And how can I reinstall it without formating all of my net's HD?
.
1 - I used unetbooting to create a bootable flash drive and I didn't see any options about speed there!
.
2 - Everytime I try to reinstall the UNR it gives me three options:

a - Format all of my netbook's HD (wich I can't do, since I don't want to loose my Vista);
b - Create a third partition (one for w. vista, and two DIFFERENT partitions for URN);
c - Choose manually where to install UNR (afte I choose this option I don't know what to do after!);

---

### Post by ArchGabriel on 2010-04-24
Anybody??? Please?!?!?!?! This is Urgent!

---

### Post by wilee-nilee on 2010-04-24
Since you still have the usb installer I hope boot from it and see if it is running slow to begin with. 

The problem here is that your description has no actual description other then runs slow, how is anybody going to interpret that into a fix? Personally I don't like UNR and I have a acer aspire netbook, I plug my flat screen monitor into it at home and wear my reading glasses when I have to look at the 10 inch screen, running a regular Lucid install. I would try the regular OS and see if it doesn't work. Don't forget this is only days from release, and I suspect the UNR is not keeping up.

It would also help if you named the actual OS your using besides vista.

I would also recognize that your thread title alone comparing vista with Linux has probably cut your chances of getting help in half at the least.

---

### Post by ArchGabriel on 2010-04-24
> **wilee-nilee said:**
> Since you still have the usb installer I hope boot from it and see if it is running slow to begin with. 

The problem here is that your description has no actual description other then runs slow, how is anybody going to interpret that into a fix? Personally I don't like UNR and I have a acer aspire netbook, I plug my flat screen monitor into it at home and wear my reading glasses when I have to look at the 10 inch screen, running a regular Lucid install. I would try the regular OS and see if it doesn't work. Don't forget this is only days from release, and I suspect the UNR is not keeping up.

It would also help if you named the actual OS your using besides vista.

I would also recognize that your thread title alone comparing vista with Linux has probably cut your chances of getting help in half at the least.

:( As I said, I am new at this thing, so I do not know what else I can say. My problem is that URN is slower than Vista or anything else I've ever seen. Everytime I try to open anything there, it takes more than 10 seconds to respond the  command.

---

### Post by wojox on 2010-04-24
Sounds like a video driver. Go into Hardware Drivers and see if there's one to activate. Open a terminal and run and copy back this command:

```
lspci | grep VGA
```

---

### Post by ArchGabriel on 2010-04-24
> **wojox said:**
> Sounds like a video driver. Go into Hardware Drivers and see if there's one to activate. Open a terminal and run and copy back this command:

```
lspci | grep VGA
```

There is nothing to activate in there... :(
Actually, there is no "hardware drive", the list is empty.

---

### Post by ArchGabriel on 2010-04-24
Is there a way to delete UNR from my computer WITHOUT formating my net's HD? I mean, recover the HD section that I used to install UNR?

---

### Post by ArchGabriel on 2010-04-24
Just installed URN on mmy notebook (Toshiba) and it is NOT working fine! I have Ubuntu 9.10 there and it works wonders. So the problem is NOT in my net's hardware, but in UNR!

---

### Post by ccw127 on 2010-04-27
The following is not so much a solution, as it is just some observations of my own situation.

I have an HP mini 110. This Atom n270 1 gig ram netbook came with winXPsp3 and ran quite fast. It would boot quick, open apps quick, etc...

I installed 10.04rc NBE and right away noticed it was not nearly as fast. I then looked around on the forums and saw this thread.

Finally my brain kicked in...

Taking a look at system performance (via top on the cli) I see that my cpu usage is quite low (this is good), but ram is right up there in the 900mb range. You see, NBE is using quite a bit (almost all, in fact) of the available physical memory. By comparison, WinXP is in the 400MB range.

Since so much of the memory is being used, this forces the OS to page quite a bit. Most netbooks (mine included) use a quite slow harddrive (5k rpm), so every page is expensive (time wise).

This is where all that slow down is likely coming from.

Your choices are upgrading the ram (if possible, as many times it is not), or at least upgrading to a faster HD (although I doubt that it would help all that much). You can also try using the plain version of Ubuntu since the pretty netbook interface of NBE is sucking up quite a bit of memory.

Hope this helps,

Chris

---

### Post by Deihmos on 2010-05-01
Netbook remix is super slow in my opinion. Windows 7 and Xp are much faster in comparison. Opening Firefox has a long pause but it seems to work better in the desktop ubuntu version. I installed 10.04 Netbook on my Asus 1005HA 2GB ram and it was just terrible.

---

### Post by EricDP on 2010-05-01
I tried netbook remix for my old laptop with 512MB RAM thinking it would be a lightweight version of Ubuntu, but it seems to be a real RAM hog. The machine thrashes nonstop. Firefox seems to be a big part of the problem though, with all the memory leaks. :(

---

