---
title: "Recommended Radeon cards"
date: 2014-03-22
forum: Hardware
---

### Post by jwbrase on 2014-03-22
It has generally been the case that NVidia cards have had fewer issues with Linux than Radeon cards, and indeed, this has been my experience with the machines I've run Linux on (though the Radeon card that contributed to that experience had severe performance and glitching issues with OpenGL on Windows as well, which makes me suspect that the real issue with Radeon cards on Linux is shoddy cross-platform OpenGL support rather than issues with Linux itself).

That said, there are some points of dissatisfaction that I have with NVidia's proprietary drivers, and my understanding is that noveau's 3D support is limited. I plan on building a machine in the near future and need to select a GPU.

As a result, I'd like to ask if there are any specific Radeon cards that have Linux drivers of acceptable quality. I have heard that above a certain price point Radeons tend to be an acceptable option, but I don't have a good sense of where that price point is or whether it's within my budget (part of that being uncertainty in my budget, I'll probably budget about $800 to $1000 for the whole machine, but this being my first machine build I'm a bit uncertain as to how I should divide that between components).

So, does anyone have a Linux box with a well behaved ATI card that they would recommend?

---

### Post by Mark Phelps on 2014-03-22
Any AMD HD cards of the 5x/6x series will work well with the fglrx drivers -- if you can find them. Avoid the HD 7x series as there are problems with those. The HD 8xxx cards (R7s) work OK, too -- but, from what I've read, the newer R9s don't have Linux drivers yet.

---

### Post by QIII on 2014-03-22
I still have several HD 5870s on a couple of machines.  They work extremely well.

Problem is that even though they are old, they are still highly desirable.  Sometimes you see them used for as low as around $200, depending on whether they are reference or not.  That's still about what I paid for mine new several years ago.  Generally they are more expensive -- even used they've increased in price!

The HD 6000s work well, too.

I agree about the R9s.  The driver for Linux is not available yet.

You can pick up an HD 5450 for < $50US.  They work fine, but they are pretty much a utility card.

---

### Post by Yellow Pasque on 2014-03-22
> Any AMD HD cards of the 5x/6x series will work well with the fglrx drivers
..and with the open-source driver as well, which is very important since AMD could drop fglrx support for those cards at any moment, which would limit your options when trying to run newer versions of Ubuntu/Linux.

The RadeonHD 7000 series should work fairly well with the open-source driver moving forward, but you may have to run a PPA to get the best support today.

---

### Post by jwbrase on 2014-03-22
> **Mark Phelps said:**
> Any AMD HD cards of the 5x/6x series will work well with the fglrx drivers -- if you can find them. Avoid the HD 7x series as there are problems with those. The HD 8xxx cards (R7s) work OK, too -- but, from what I've read, the newer R9s don't have Linux drivers yet.

I notice that you say 5x/6x works "well", but 8x works "OK". Could you define "OK" there? Are you using it as another word for "well", or are there issues to be aware of?

---

### Post by Mark Phelps on 2014-03-22
The use of "OK" and "well" was not to distinguish one from the other -- but as was mentioned, the HD 5x/6x series are getting older and AMD is infamous for dropping driver support on older chipsets.   I personally have used one of the HD 8x-series and have found it to work well with the fglrx drivers.

---

### Post by jwbrase on 2014-04-11
I eventually ended up going with an R7 260x. It does much better than the previous ATI card I'd had experience with as far as rendering goes, but the drivers have some rather horrible stability issues: I've found at least one way to reproducibly hang the entire X11 stack unkillably (and put 1 CPU core under 100% load) with no way out but to reboot. The only thing to be said for that situation is that the kernel doesn't panic: The machine is still quite operable via SSH (but all local interactivity fails completely, even magic SysRq does nothing), and can be shut down gracefully. Fortunately, while it does make one (fairly important) part of one program unusable, as well as making Xscreensaver a Russian Roulette game, the hang seems to be fairly limited in scope: I'll probably be able to manage with the card, although I won't be able to completely retire and repurpose my laptop as I'd hoped, as I'll need its NVidia card for certain things. Also, the drivers do not seem to play well with Wine.

On the other hand, I now have high resolution virtual terminals and a working framebuffer together with good 3D performance. It's just frustrating that I have to choose between that and drivers that don't lock up unrecoverably in kernel-space. Between them, AMD and NVidia could write a perfect Linux video driver. Either alone seems to be quite deserving of Linus's infamous gesture...

---

### Post by Coolgirl on 2014-04-12
[h=1][B][SIZE=2]Asus ATI Radeon HD6450  , I use this in my Asus Rampage IV Black Edition EATX mother board .. never a problem in the world!
[/SIZE][/B][/h][B][SIZE=2]
Hope this helps
[/SIZE][/B]

---

