---
title: "HP LaserJet driver in Jaunty"
date: 2009-05-21
forum: Hardware
---

### Post by dclement on 2009-05-21
Hello,

I'm having what looks like a printer driver issue in Jaunty, with my faithful LaserJet 2200 (PS).

Most characters print out topped with one or two very thin lines. I think it's best explained with an image:

[IMG]http://pagesperso-orange.fr/math.pc.vh/test.jpg[/IMG]

It happens with every program, and only with this printer. 

The only workaround I have found is to switch from the (recommended) Postscript driver to the: HP LaserJet 2200 hpijs.

But it's limited to 600 dpi so I doubt I get the full performance of the printer. Unfortunately, the other PS drivers seem to have the same issue.

What could I do? Maybe revert to the Hardy driver (which worked well), but I don't know how.

TIA for help - best regards, Daniel

---

### Post by muzincs on 2009-05-29
I have an HP Laserjet 2200D printer that is doing exactly the same thing since I upgraded to Jaunty.  Has anyone figured out how to solve this problem?  Thanks.

---

### Post by ghost_zero on 2009-05-30
I have the same problem.
I hope there is a solution to this.
I have now tried to upgrade the cups package, as well as ghostscript and various cups drivers (I am not sure if I got all of them) to the versions that are in the currenct Karmic repository and the problem still exists.
However, I am sure the printer works fine because under Windows XP it prints correctly with the PostScript driver.

Btw.: Is there a way to set the RAM size for the hpijs driver?

---

### Post by dclement on 2009-05-30
Hi,

Good not to feel alone...

Here is the choice of drivers that we are offered:

1. HP Laserjet 2200 Postscript [en] (recommended)
2. HP Laserjet 2200  hpijs [en]
3. HP Laserjet 2200 Series hpijs [en]
4. HP Laserjet 2200 - CUPS+Gutenprint v5.2.3 [en]
5. HP Laserjet 2200 - CUPS+Gutenprint v5.2.3 Simplified [en]
6. HP Laserjet 2200 Foomatic/Postscript [en]
7. HP Laserjet 2200 Foomatic/lj4dith [en]
8. HP Laserjet 2200 Foomatic/lj5gray [en]
9. HP Laserjet 2200 Foomatic/lj4 [en]
10.HP Laserjet 2200 Foomatic/pxlmono [en]

The ones called "Postscript" have the problem. I have found that one could print text with drivers 2. to -5., but only the latter two print graphics acceptably, though far from perfectly. (I have a fair amount of .eps graphics, and I can tell you that the loss in quality is huge compared to a PS driver.)

I have not tested 6. ~ 10. but I did test some 2100 or 2300 drivers, with the same result.

Since all these PS drivers appear to rely on Ghostscript (namely, 8.64), I am convinced that the issue is there. But, to downgrade Ghostscript seems a lot of trouble.

To hear that the karmic version doesn't fix it is not very good news...

---

### Post by ghost_zero on 2009-05-30
Well: Regarding Karmic: I might have forgotten to update some packages, as I didn't want to upgrade everything to Karmic but just the printer part.
Btw. I also thought it very likely is GhostScript which was why I upgraded that one first but if I create a PS file (output to file) the problem doesn't seem to exist when viewing the output file on the PC.

Btw.: Do you know if the problem also occurs on Intrepid?

EDIT:
I have now tried the following. I added 

deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse

to the software sources of Ubuntu and then I run the following command in the terminal:

sudo apt-get install ghostscript=8.61.dfsg.1-1ubuntu3 libgs8=8.61.dfsg.1-1ubuntu3 ghostscript-x=8.61.dfsg.1-1ubuntu3 gs-common=8.61.dfsg.1-1ubuntu3

That way I was able to downgrade those packages without uninstalling other packages. HOWEVER, it doesn't seem to solve my problem.

Btw. the printer I tried it was a HP LaserJet 4050TN.

I also thought about trying to downgrade hplip but that is near to impossible because it depends on python 2.5 and default is python 2.6 installed and there are various programs that depend on python. Meaning there would be many applications to remove or to downgrade.

---

### Post by dclement on 2009-05-31
> **ghost_zero said:**
>  [...]
Btw. I also thought it very likely is GhostScript which was why I upgraded that one first but if I create a PS file (output to file) the problem doesn't seem to exist when viewing the output file on the PC. [...]

Definitely. I use TeX to produce PS files and they appear correctly in Evince.
>  [...]
Btw.: Do you know if the problem also occurs on Intrepid? [...]

Well, my wife has an Eee-PC running Intrepid. She has some updates-lag (no more than 160 though ;-) ). As it is, it can print WELL.

However, I checked some version numbers among the updates suggested by the update manager:

cups, cups-bsd, cups-client, cups-common, libcups2, libcupsimage2:
1.3.9-2ubuntu6 -> 1.3.9-2ubuntu9.1

ghostscript, ghostscript-x, libgs8:
8.63-dfsg1-0ubuntu6.1 -> 8.63-dfsg1-0ubuntu6.4

foo2ajs:
20080810-0ubuntu4 -> 20080810-0ubuntu4.1

foomatic-filters:
4.0.0~br177-0ubuntu1 -> 4.0.0ubuntu3

(Do you think I'm overlooking something?)

These could be downgraded without too much hassle, so I could update one after one and see when the problem appears -- if it does.

I'm also curious to see if Jaunty printed well when run from the original liveCD.

I'm planning to test this ASAP.

---

### Post by ghost_zero on 2009-05-31
hplip and hpijs might be a problem too, after all up to now it seems it is only HP printers that have problems.
It is unlikely though because hpijs works fine and hplip is from what I understand more for the connection to the printer - like you could also use Samba or IPP or whatever - but who knows...
I mean: The problem itself is already strange because the PostScript created seems to be fine (using the printer driver and selecting output to file) when looking at it with a PostScript-Viewer.

---

### Post by dclement on 2009-06-01
A little update, but not much progress:

- I noticed this:
[https://answers.launchpad.net/hplip/+question/69906]("https://answers.launchpad.net/hplip/+question/69906")
The user notices that the streak above a letters mirror the foot of this letter. Well observed, but doesn't help much, though. He claims that the issue is "solved" by changing th driver. He doesn't seem to have noticed the drawbacks in doing so.

- This issue is part of Jaunty even from the original liveCD.

- Intrepid (all updates) does NOT have this issue. So... should we say that the issue lies in a given package, somewhere between the latest Intrepid and Jaunty versions (thus threatening to appear also in Intrepid)? Or is it more tightly bound to Jaunty?

There is need for a bug report for sure, but where?

Also, I'm curious about testing Karmic live, to see how it behaves.

---

### Post by ghost_zero on 2009-06-01
Regarding Karmic Live testing. That is a good idea because as said I didn't upgrade everything just some parts and those I already downgraded again.

The point regarding switching the driver, we already knew (actually) but that isn't really a solution. It is in best case a workaround. [www.openprinting.org](www.openprinting.org) doesn't recommend the PostScript driver for no reasons after all.

I really wonder in which package the problem lies.

---

### Post by dclement on 2009-06-03
There has been a bunch of CUPS-related updates for Jaunty today. Alas, they did not solve the issue.

Nor does the HP-made .ppd from openprinting.org, which appears to be exactly the same as the one in Ubuntu.

Isn't Karmic alpha 2 due out in a week or so? Let's hope it comes with a LiveCD.

---

### Post by ghost_zero on 2009-06-03
I am not sure but isn't there a live-cd already available here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
?
I thought about trying it out but I read somewhere that the currently Karmic has some issues with RAID partitions and as my main data lies on such partitions I currently don't want to try it out and I don't want to unplug them before trying it out :)

---

### Post by dclement on 2009-06-05
Indeed, the web page address contains "live" as well as two comments below ("livecd filesystem").

It won't be easy for me to test, though, because the current image exceeds the capacity of a regular CD. And my (not so new) notebook doesn't allow booting from an USB device.

BTW, I'm using Jaunty 32 bits. I wonder if the 64 bits edition has the same issue.

---

### Post by ghost_zero on 2009-06-07
I have Jaunty 64Bit. So I would guess: It does :)

---

### Post by dclement on 2009-06-09
Good news at last!

While I was searching to see if the bug was already known, I came across _[this bug report]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/362186")_.

Doesn't it recall something? The real good news is that the poster Till Kamppeter (a developer?) has eventually been able to provide a patched file in _[post #80]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/362186/comments/80")_.

It took him several attempts to get the file working, so the instructions for setting it up are located back in _[post #43]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/362186/comments/43")_. (You must not forget to make the file executable.)

It worked for me. I can now print PS from Jaunty. Graphics in my PS files output fine.

@ghost_zero: I'm particularly interested in knowing whether it also works for Jaunty 64, as I have a brand new PC to set up by the end of the week. Will Jaunty eventually be on it?

Then, let me now if you think we can mark this thread as solved.

Regards, Daniel.

---

### Post by ghost_zero on 2009-06-09
I tested that file and it seem to work on my Jaunty 64Bit. At least I tried to print the same document with the pdf2ps file supplied with Jaunty and the one of that thread. I couldn't fine the "lines" I saw with the pdftops file from Jaunty after using the one supplied in the thread BUT I haven't done too much testing but it seems to work. It isn't too surprising though as it is a shell script and therefore it was very likely to also work fine on 64Bit when it already works fine on 32Bit. Of course, I couldn't be sure before testing it though.

It seems though that with that pdftops filter there is still some other problem left which, however, according to the mentioned bug in comment #72 seem to be fixed though in Karmic repository (because it is related to the poppler library and that one got updated).

But I wonder: Why is this related to the pdftops file? I thought normally it is different: You create the PostScript-File during printing and from it you can create a PDF file if wanted. Furthermore, why is the new pdftops way smaller than the original (about a third of the original size).

Furthermore: I wonder why this fix isn't available as update to Jaunty yet - I mean: OK it could be related to the still remaining problem with that fix..?

Btw.: I am thankful that you found that bug-report. Finally, I can use the PDF driver :)

---

### Post by dclement on 2009-06-10
> **ghost_zero said:**
> I tested that file and it seem to work on my Jaunty 64Bit. [...]

Glad to hear that.

> [...]It seems though that with that pdftops filter there is still some other problem left which, however, according to the mentioned bug in comment #72 [...]

I meant to point at this latest file. It's apparently the one that works best.

> [...]But I wonder: Why is this related to the pdftops file? I thought normally it is different: You create the PostScript-File during printing and from it you can create a PDF file if wanted.[...]
I have no clue about that -- but I generally prefer things working without my understanding why, than the converse ;-).

> [...]Furthermore, why is the new pdftops way smaller than the original (about a third of the original size).[...]

Wild guess: the developer has made his fix in a hurry, possibly dropping some functionnality in order to prevent side-effects?

> [...]Furthermore: I wonder why this fix isn't available as update to Jaunty yet - I mean: OK it could be related to the still remaining problem with that fix..?[...]

You may notice that this bug discussion is pretty recent. I guess the developer wants to iron out his fix before allowing it to make it into the repos.

---

### Post by ghost_zero on 2009-06-10
> **dclement said:**
> 
I meant to point at this latest file. It's apparently the one that works best.

I know but there still seems to be one small bug that, however, is not related to the pdftops file but to the used library and that one was fixed in Karmic-Repository :)

Regarding the size point: Actually, to ensure that the document prints even if not yet implemented functions are used, there normally has to be some kind of core of them there, like passing the output through unchanged or such and that also requires space. Therefore, I wonder if one third just comes from this.

However, if my guess is currect that pdftops filter uses a different library than the previous one. I think that it is very likely that the decrease comes from this. Especially, since that different library seems to have an own pdftops binary (not shell script) stored in /usr/bin (obviously different path :) ), so that one probably mostly is used for passing the correct information over to the other one.

Regarding repos: That is true - at least for Jaunty but it could at least have been in the Karmic-Repositories or the Jaunty-Backport ones but of course, we actually don't know with which package that pdftops file is included. I would guess cups but...

---

### Post by dclement on 2009-06-30
Today there has been a bunch of cups-related updates for Jaunty.

I forgot to take note of the description, but it seems to me that they took care of our Postscript problem. I would say it is solved now.

Can someone confirm? (and possibly retrieve the link to the description of the updates, which I was unable to do)

Regards, Daniel

---

### Post by Jofarmer on 2009-07-02
I can confirm that the updates fixed it for me (LaserJet 3015)

---

