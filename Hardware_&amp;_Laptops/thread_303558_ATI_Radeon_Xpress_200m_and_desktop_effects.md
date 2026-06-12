---
title: "ATI Radeon Xpress 200m and desktop effects"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by oskie on 2006-11-20
I have this dreaded video card and would love to use beryl or compiz. I can't seem to find a definitive post that answers all the questions regarding 3D desktop effects and use of this driver. It appears that I cannot use this videocard for the time being because none of the new drivers support it, or at least none of them allow 3D effects. Is this so? If not, I have the following questions:

1. The key is getting 3D enabled and direct rendering right? If so, which driver is best: the fglrx driver that comes with Edgy or the ATI website driver or something else I haven't thought of.

2. Should I go with XGL or AIGLX?

3. Should I go with Beryl or Compiz?

Many thanks for your help.

---

### Post by tubasoldier on 2006-11-20
Good luck with that load of crap from ATI

---

### Post by oskie on 2006-11-20
> Good luck with that load of crap from ATI

That bad, eh? Next computer I buy will have an Nvidia or Intel card that's for sure. Are you listening AMD? Open source your drivers!

---

### Post by monokrome on 2006-11-23
I have this card on my laptop. You can get 3D effects/direct rendering perfectly fine. Only problem is you have to use the memory in the motherboard, so go into your BIOS and change it from sideport to UMA.

After that, install the FGLRX drivers, and disable composite in your XOrg.conf file.

This arises another problem... Disabling composite makes it so that we can't run Beryl/Compiz. Which sucks. But that will get you 3D acceleration :)

Peace,
  - monokrome -

---

### Post by monokrome on 2006-11-23
I should also mention that another friend of mine has this card, and he got Beryl working on it. He didn't do anything special to set it up... It just worked.

---

### Post by adam.tropics on 2006-11-23
Ok, yes it does work on this card, though seemingly not for everyone!

You need the fglrx driver installed....and working first...[TRY HERE]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

You currently have to go the Xgl route, as ATI haven't enabled the necesary stuff for AIGLX yet.

Compiz more stable, Beryl more fun and less stable! A good guide for Beryl is [here]("http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome"), along with [dedicated forums]("http://forum.beryl-project.org/index.html").

---

### Post by oskie on 2006-11-25
Thanks for the replys. Will give it a try.

---

### Post by dndawson on 2006-11-29
I have a friend who also has this card (in a HP pavilion, not sure the exact model) and got 3d acceleration and beryl to work under Dapper. The problem he runs into is that beryl seems to run very unstably for him and crashes after only a few minutes.  Given the fact that this card seems to work differently for everyone, I would not give up hope. 

The guide he followed for 3d acceleration is several posts down (#15, I think) on this page: [http://www.ubuntuforums.org/showthread.php?t=199421&page=2](http://www.ubuntuforums.org/showthread.php?t=199421&page=2)

The guide he followed for beryl was here: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)
(they seem to be having server problems, you might try google's cache [here:]("http://64.233.161.104/search?q=cache:Xemu6CKrE6EJ:wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL+beryl+dapper+xgl&hl=en&gl=us&ct=clnk&cd=1") )

The only other thing he did which may not be mentioned in the links is that he did have to change sideport to UMA + sideport (he had no option for just UMA) and give up 128MB for shared.

So as an overview: the fglrx drivers in the repos did not work for him, he used 8.24.8; he used XGL (don't think fglrx supports AIGLX); and he used beryl (maybe compiz would have been better, who knows?)

Good luck

---

### Post by electrocutioner on 2006-11-29
> **adam.tropics said:**
> Ok, yes it does work on this card, though seemingly not for everyone!

You need the fglrx driver installed....and working first...[TRY HERE]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

You currently have to go the Xgl route, as ATI haven't enabled the necesary stuff for AIGLX yet.

Compiz more stable, Beryl more fun and less stable! A good guide for Beryl is [here]("http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome"), along with [dedicated forums]("http://forum.beryl-project.org/index.html").

 First of all, a hearty CHEERS!!! I have never gotten my ati radeon 200m card in my Compaq (HP) laptop to work in ubuntu (well dapper anyways).
 I got it running surprisingly quickly under this installation of EDGY using your first link and method 1.

 Had a little more difficulty with getting compiz to work using your link, however I have now been using beryl for about 1.5 hrs, no problem.
 Try this very easy to follow graphical how to,which uses only the gui for installation
\\:D/ [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")

---

### Post by Angafirith on 2006-11-29
> **electrocutioner said:**
> First of all, a hearty CHEERS!!! I have never gotten my ati radeon 200m card in my Compaq (HP) laptop to work in ubuntu (well dapper anyways).

Which Compaq laptop do you have? I have a Presario v5210us and never quite managed to get Beryl working properly on it.

I can get Xgl to run, but not Compiz or Beryl. I'm not sure if it is even worthwhile, as my screen goes black anytime I open certain applications.

---

### Post by TusharG on 2006-12-04
I've spent days in configuring this card on Ubuntu/Edgy and still have not managed. However I have successfully used it/configured it in just 20 min in Ubuntu Dapper using 8.24 drivers released by ATI.
 If you want to stick to old Ubuntu release then ATI is fine...else... 

Next time when I sell my notebook I'm gonna make sure I never buy ATI product again and go for Nvedia when has better driver and community support

Good luck with your ATI card... I'm trapped and just wished you shouldnt... :)

---

### Post by xphere on 2006-12-09
Hello:

I have a dell inspiron 1501 with this ati card. When I boot and enter the cmos I can't find anything about the memory administration of the video card:confused: . If somebody knows somthing that could help whit this problem it would be great. Its the only thing left to configure, (with the exeption of the card reader), on my laptop.  

Thanks in advance for your input.

---

### Post by firest0rm on 2006-12-10
Just for the record, I had Beryl working like a charm last night on a Compaq V2305 laptop with the XPRESS 200M.  Started up the computer this morning and only got lock-ups.  Gah!  Back to square one, I guess... trying to figure out what the heck I did right to get it to work... and what changed... grr...

---

### Post by Adler on 2006-12-11
> Good luck with that load of crap from ATI

Tubasoldier,

My words exactly...

Adler

---

### Post by Adler on 2006-12-23
So Folks,

What is the solution?

I'm running a CompaQ Presario V500 Notebook, can do 3D, and have great fps 150-200 running GL-117, but no Beryl. 

I did compile all the latest ATI drivers for my 64-bit system, but not Beryl. I do have the Diamond in my takbar.

What's the better / best Notebook card?

Merry Christmas, and a Happy New Year!

---

### Post by Angafirith on 2007-01-31
I hate to revive a dead thread, but I just noticed I had bookmarked this thread. With recent fglrx drivers (8.32.5) and XGl (7.0.0.git.20060725-0ubuntu2 from edgy universe), I am running Compiz (3.6) without any issues.

Edit: I realize after posting that there's a guide on the front page on exactly how to do it: [http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766)

---

