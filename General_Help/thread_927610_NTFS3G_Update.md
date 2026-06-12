---
title: "NTFS3G Update ?"
date: 2008-09-23
forum: General Help
---

### Post by Zakhafr on 2008-09-23
Hello,

I suffered from a noticeable slowdown writing big files with NTFS-3G

(Big files = files >1GB)

This is confirmed by the FAQ of NTFS3G

[http://www.ntfs-3g.org/support.html#slowwrite]("http://www.ntfs-3g.org/support.html#slowwrite")

The symptom (through a tool showing KB/s written) is that everything is OK for a few seconds: throughput is correct, disk access is showing, them suddenly throughput falls down to 0 disk  stops accessing for a few seconds... then, hopefully, the writing process starts again. It looks like things are blocked as in a garbage collection syndrome.

A similar slowdown happens also while reading DVD, if they are stored on the disk (although the NTFS3G FAQ mentions only writing). At certain times, reading is frozen during several seconds.

According to the FAQ at NTFS3G **1.2506** (at least) is needed to fix this problem. But, due to the feature freeze process in Ubuntu releases, Hardy contains a release dating back from february, and it is a **1.2216**

So, the question is :

**Did someone already updated the NTFS-3G driver in Hardy (there is no such update yet in the backports repository), if someone did, can he/she share his knowledge (how to compile it, binary, bugs...) ?**


This driver is highly used in my configuration as I'm still running under Wubi. :)

*Keep up the good job!*

---

### Post by blk_jack on 2008-10-02
bump!

Any plans for the current version of NTFS-3g to be supported in Ubuntu, or a brief write-up on how to install it from source/another repository?

Thanks :D

---

### Post by blk_jack on 2008-10-02
Further time spent on google provided me with this: [http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/)

A new(er) version is available through their backports repositories.

---

### Post by hansdown on 2008-10-02
Hi blk_jack.

Do you have automatic updates turned on?

Sorry to ask a silly question.

---

### Post by blk_jack on 2008-10-02
Sorry, I don't understand what you mean by "Automatic updates".  I have all the "Ubuntu Updates" checked off in the Updates tab of Software Sources, if that's what you mean.

I have it set to notify me about available updates, not to automatically install them without confirmation.

If I'm completely off the mark here, my apologies.  I'm a long time Gentoo user who's been running Ubuntu on his laptop for a few years, so to be honest I don't know Ubuntu as well as Gentoo.

Anyway to follow up w/ my previous post.  I've added the backports repository to my sources and now have a newer (and much faster) version of NTFS-3g on my system.

---

### Post by hansdown on 2008-10-02
My apologies blk_jack.

I'm only trying to help, so please bear with me. 

Do you have all the repositories?

System> administration> software sources. Check the "main,universe,restricted, and multiverse" boxes.

Click on third party software, check the first three boxes.

Hopefuly I've helped you without sounding like an ***. I've been accused of that, perhaps truthfuly.

You are wise not to have the updates install automatically.

---

### Post by blk_jack on 2008-10-02
I think you missed the point of this thread entirely, hansdown.

The OP was commenting on how Ubuntu has an old version of the program NTFS-3g in their Hardy repositories.

> According to the FAQ at NTFS3G **1.2506** (at least) is needed to fix this problem. But, due to the feature freeze process in Ubuntu releases, Hardy contains a release dating back from february, and it is a **1.2216**

He wanted a new version because it contains fixes to the slowdowns that he's been having.  I found a new build of NTFS-3g for Ubuntu through the Backports repository, so I posted the link.

---

### Post by hansdown on 2008-10-02
My apologies again.

I will let someone better equiped than I to solve your problem.

---

### Post by blk_jack on 2008-10-02
> **hansdown said:**
> My apologies again.

I will let someone better equiped than I to solve your problem.

Don't apologize, yo.  My "problem" was solved by me (as indicated in my response to myself) and also the OP in the 3rd comment.  Problem solved, case closed, etc.

---

### Post by hansdown on 2008-10-02
I'm a sucker for a happy ending blk_jack.

---

### Post by ju2wheels on 2008-10-02
Intrepid has 1.2506 out of the box so it will be out soon.

---

### Post by Zakhafr on 2008-10-02
Thank's blk_jack for the link on the Morgoth repository.

I'm just hoping now this sort of update would be made "official", as there's always a security risk installing software from unofficial repository. I know I could download the code, check if it has no harmful additions, and compile it myself... but it's quite a longer process than just downloading from an "official" repository.


> **ju2wheels said:**
> Intrepid has 1.2506 out of the box so it will be out soon.

That's right ju2wheels, but it's good to see someone compiles successfuly a more recent ntfs3G on hardy (LTS), it proves backporting of this kind of thing is possible... and precisely, **that's what backporting is for**: don't wait for new release, or don't have to migrate to new release to install important updates!
There might also be reasons for some people to stick with Hardy (especially since it is LTS, it is supposed to have better/longer support). As for Intrepid, my personnal thoughs are not to jump immediately on bright new shining things... I waited till 8.04.1 for Hardy and I'm glad of that because there were quite a lot of bugs on the initial relase (tried it on a test drive, it was quite awful), and it's bound to be the same for every new release!

Nevertheless, I might still try Intrepid when it's out, but it'll be on a test partition.

---

