---
title: "Gateway 7405GX w/ Broadcom WiFi"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by suspend on 2007-02-28
I've been debating whether or not to go with Ubuntu for a bit, but am worried about the hardware support for my laptop.  I've been parsing the forums, et. al. for a while and I think everything will work.  The only thing that troubles me is the possibility that my wifi will not work.  I am using a Broadcom with the BCMWL5 driver.  Currently I am using windows and am very unsatisfied with the amount of modding I have to do to the system for it to work well and free of foreign bodies.  I downloaded and burned Edubuntu Edgy should I wait a few months and go with Feisty Fawn?  

Ubuntu is designed to "just work"  I need that.  Especially after working with MS for so long.  Please advise.

---

### Post by x64Jimbo on 2007-02-28
It's a very good thing that you found Ubuntu. It's an amazing distribution of Linux, and it is probably the most desktop-ready distribution out there. Broadcom cards that use the bcmwl5 driver are pretty well supported under Linux with NDISWRAPPER, so I recommend using that to get connected. There are a few tutorials around here about ndiswrapper, but it can be summed up like this:
put the bcmwl5.inf and bcmwl5.sys files in your home folder
> sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper
ifconfig
You should see your interface in the list now.

---

### Post by Praill on 2007-02-28
If youve never used linux before, don't expect the transition to be easy. It has a steep learning curve for those used to Winblows.
If you decide you want to try linux (you wont regret it) I would, initially, recommend keeping a windows partition for the times when you get fed up, so you can log back into windows cool down and come back to linux when youve got a few more ideas.
However, make sure you install windows FIRST. If you install ubuntu, and then windows, windows will completely over-ride the grub and not give you an option to boot back to unbuntu (yay windows).
So my recommendation would be to pop in a windows cd, install it on half the machine, then install edgy on your other half and try it out.

Of course, edgy is also a live cd. So you can try it out initially and see if you like it. The live CD experience isnt quite what you get with the actual install, but it might give you a close idea of what hardware is supported "out of the box".

---

### Post by suspend on 2007-02-28
Thanks for the great feedback.  x64Jimbo, are you running the 64bit variety of Ubuntu?  I noticed your icon thing.  My Gateway has the 64bit Athlon in it, would you recomend it for me over the x86 version?  Thanks!

---

### Post by x64Jimbo on 2007-02-28
For a beginner, you'll want the 32 bit version. There are still a lot of stupid little glitches out there that make running 64 bit versions of ANY OS very annoying if you don't know what you're doing or have the patience to fix them. The speed increase is nice for math-intensive apps like compression, but unless you're ripping tons of movies, you'll probably not notice the difference.

---

### Post by suspend on 2007-03-02
Will the broadcom thing with a live cd run as a test?

---

### Post by suspend on 2007-04-20
Did Feisty Fawn make any improvements in this arena?

---

### Post by x64Jimbo on 2007-04-23
I have not tested Feisty on my laptop yet. You could always try it, however, my experience tells me that the driver that is included by default in Ubuntu will be the open source kernel driver, and that is still somewhat shaky. You'll probably want to use ndiswrapper. It's really not bad at all - been working flawlessly on my laptop for years.

---

### Post by suspend on 2007-04-25
What type of laptop are you running?  In the past I have tried to run ndiswrapper with a variety of .inf drivers from the windows cds, the broadcom website and various other sources, like the broadcom project.  I have gone through every tutorial and every epic forum thread to get this to work and it never has.  Since the feisty fawn seemed to have a good deal of laptop and network supports added in, I was hoping that I would finally be able to take the 100% plunge off the win boat with my nice little laptop instead of having to run linux only on legacy desktops.  Its sad and frustrating, but I will keep trying.  Thanks for the support.

---

