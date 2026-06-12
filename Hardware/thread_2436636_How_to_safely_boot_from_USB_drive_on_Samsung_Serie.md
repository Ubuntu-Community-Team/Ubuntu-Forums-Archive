---
title: "How to safely boot from USB drive on Samsung Series 5 laptop"
date: 2020-02-10
forum: Hardware
---

### Post by random turnip on 2020-02-10
I've recently gotten a Samsung Series 5 laptop (NP550P5C) which I plan to install some form of Linux on (probably Ubuntu) as soon as its new SSD arrives today.  However, in preparation I stumbled upon people talking about bricking their systems when trying to boot from a USB device (both Linux and Windows).  Something to do with a UEFI bug which messes up how much VRAM is being used killing the BIOS.  

Here's an example thread about this with my exact laptop:-
[https://askubuntu.com/questions/252653/samsung-uefi-brick](https://askubuntu.com/questions/252653/samsung-uefi-brick)
There are loads more similar threads.  Not many answers.  In fact, Googling "NP550P5C Linux" gives up things about this:-
[https://www.google.co.uk/search?safe=strict&sxsrf=ACYBGNR2uK82PNITc8ox4UTda-9fPKtyHA%3A1581340425909&source=hp&ei=CVdBXo2iNcqdlwSXpZz4CA&q=NP550P5C+linux&oq=NP550P5C+linux&gs_l=psy-ab.3..35i39.839.7847..7995...1.0..0.58.443.8......0....2j1..gws-wiz.......0j0i20i263j0i22i30.b37EMa2tDtQ&ved=0ahUKEwjNyumSiMfnAhXKzoUKHZcSB48Q4dUDCAc&uact=5](https://www.google.co.uk/search?safe=strict&sxsrf=ACYBGNR2uK82PNITc8ox4UTda-9fPKtyHA%3A1581340425909&source=hp&ei=CVdBXo2iNcqdlwSXpZz4CA&q=NP550P5C+linux&oq=NP550P5C+linux&gs_l=psy-ab.3..35i39.839.7847..7995...1.0..0.58.443.8......0....2j1..gws-wiz.......0j0i20i263j0i22i30.b37EMa2tDtQ&ved=0ahUKEwjNyumSiMfnAhXKzoUKHZcSB48Q4dUDCAc&uact=5)

I'd obviously like to avoid this so am slightly concerned about booting via a USB stick now.  I've found instructions on how to get the laptop to boot through a USB stick on YouTube:-
[https://www.youtube.com/watch?v=JHmZX-Kk_zI](https://www.youtube.com/watch?v=JHmZX-Kk_zI)
[https://www.youtube.com/watch?v=D0ylA1ltqEo](https://www.youtube.com/watch?v=D0ylA1ltqEo)

I'm unsure if these are my exact laptop, they look pretty similar, so assume the BIOS will be the same either way (I haven't checked my BIOS settings yet). I'm not sure if these are supposed to be ways of avoiding this issue or still risk it happening.

How do I find out if this is something fixed by a BIOS update?  I can't find anything on Google.
How do I avoid this happening when booting from USB?  Or is this going to be inevitable/completely random?
Would booting from a live DVD run the same risk (this laptop actually has a disc drive!)?
Could I install Linux onto the blank SSD another way and then put it into the laptop already installed (I have a desktop also)?  If so, how do I do that?

Thanks very much for any help, I plan to give this a go tonight.


Edit:
After doing a little more research, is this as simple as turning the secure boot option off as shown in some of these videos? Or would the but still exist after that?

I'm also wondering if hardware was the correct section for this question.


Edit 2:
I found this thread, where numerous people state that booting in bios mode will remove the risk, is it really that simple?
https://superuser.com/questions/549941/how-to-safely-install-gnu-linux-distro-on-a-samsung-uefi-enabled-laptop

---

### Post by yancek on 2020-02-10
The link below will take you to the official Ubuntu documentation on installing UEFI.  You don't indicate whether you have windows or any other OS already installed but it also explains dual booting w/windows if you do.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

First thing I would recommend is to actually take a look around in your BIOS firmware so you are familiar with it before beginning.

---

### Post by random turnip on 2020-02-10
> **yancek said:**
> The link below will take you to the official Ubuntu documentation on installing UEFI.  You don't indicate whether you have windows or any other OS already installed but it also explains dual booting w/windows if you do.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

First thing I would recommend is to actually take a look around in your BIOS firmware so you are familiar with it before beginning.

Thanks, that's helpful. I dont intend on dual booting, and after reading that I'll install a traditional BIOS version rather than UEFI. Question is though, does me turning UEFI mode off stop the risk of the VRAM bug bricking my system?

I also found a thread saying that it might be fixed with a kernel update anyway...
[https://askubuntu.com/questions/391166/will-booting-ubuntu-in-my-samsung-np550p5c-s06in-brick-it](https://askubuntu.com/questions/391166/will-booting-ubuntu-in-my-samsung-np550p5c-s06in-brick-it)
But is it possible that the Linux kernel could be updated the avoid a bug in the UEFI of a machine like that?

---

### Post by oldfred on 2020-02-10
I deleted my notes on this old issue. You are the first to mention it in years, but Samsung has fewer installs posted with issues. So either no issues, or not many Samsungs.
It was with early UEFI implementations and originally blamed on Linux. It was a case where too many UEFI boot entries filled UEFI NVRAM 50% and it quit.
But then they proved, Windows would also cause issue, so vendors really at fault.

You should make sure you have latest UEFI that is available for your system.
Linux did create a kernel work around so later versions were ok.

Found bug. Says fixed.
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

---

### Post by random turnip on 2020-02-11
> **oldfred said:**
> I deleted my notes on this old issue. You are the first to mention it in years, but Samsung has fewer installs posted with issues. So either no issues, or not many Samsungs.
It was with early UEFI implementations and originally blamed on Linux. It was a case where too many UEFI boot entries filled UEFI NVRAM 50% and it quit.
But then they proved, Windows would also cause issue, so vendors really at fault.

You should make sure you have latest UEFI that is available for your system.
Linux did create a kernel work around so later versions were ok.

Found bug. Says fixed.
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

That bug thread was quite an interesting read.  Seems like you say, both Samsung and Linux fixed/worked around this issue, so I'll make sure I update the BIOS through Windows before swapping the hard drives and installing.

I'm assuming that any Linux distro newer than this should have this fix included?  I've been toying with trying out Pop_OS on this machine too (which is Ubuntu based anyway).

Thanks for the research and link.

---

### Post by random turnip on 2020-02-14
For anyone stumbling across this wanting the outcome; I turned off all aspects of safe booting and followed the usual guides for BIOS options.  I decided to use CMS mode rather than UEFI mainly because I'd read of people complaining that certain hardware aspects didn't work properly with UEFI enabled for some reason (mainly lights, slow speeds while charging and the lid being closed).  But the laptop works perfectly well (and performs better than I expected) in CMS mode.  I guess just make sure you have the latest BIOS installed (version P09ABI in my case).

---

