---
title: "AMD Athlon 64 X2 3800+ -- how can I disable one core / 'seesaw' processes?"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by perixx on 2008-01-24
Problem: 

I want to disable one core for testing purposes, as some games / apps seem to dislike the dualcore multithreading...
Perhaps there's also some tool like 'smp seesaw' under Win?

perixx

---

### Post by shad0w_walker on 2008-01-24
Ok, ignore this post as I didn't get the main bulk of your post (Showed up empty) and I assumed you were relying on the title.

---

### Post by scxtt on 2008-01-24
how about using a kernel that doesn't support SMP?

---

### Post by shad0w_walker on 2008-01-24
Thanks to the guy above, forgot about that option (Been up all night) boot up with the kernel option nosmp and you should be good to go.

---

### Post by perixx on 2008-01-24
Thanks to the two of you! I'll try it out...

perixx

---

### Post by perixx on 2008-01-26
Hi shad0w_waker....

I tried your command, but it only resulted in very shortly displayed error messages (can't see what it is - contains '0'). After that, the boot-splash shows up and system freezes.

perixx

---

### Post by shad0w_walker on 2008-01-26
Odd. Not sure what to suggest as I haven't really used the nosmp option (Never had a reason) so I'm only aware of it. I will however give you another bump and hopefully someone with some more experience with it will chime in,

---

### Post by perixx on 2008-01-26
'...invalid reference to irq 0' - that's what the printout says (several times)... thanks anyway.

perixx

---

### Post by perixx on 2008-01-27
Somebody got another idea perhaps?

---

### Post by perixx on 2008-02-02
*bumpthis*

---

### Post by pudgewack on 2008-02-02
I have never tried this on my AMD desktops, but I have been able to disable a core on my laptop (Dell Latitude D620 with an Intel C2D) when I was running Mac OSx on it.  There was an option in the bios that let you change the number of cores that will be used.

On my two AMD X2 desktops, I have not seen that as an option in the bios (but I have never looked though)....but that could just be because of a limitation of my motherboards.

Good luck,
Matt

---

### Post by perixx on 2008-02-03
Thx for reply, pudgewack... 

My BIOS doesn't support a switching-feature like the one you mentioned. So I'm in need of some kernel-switch to boot Linux with.

perixx

---

### Post by perixx on 2008-02-08
*bumpagain*

---

### Post by scxtt on 2008-02-09
have you looked into downloading a vanilla kernel and compiling it w/o smp support?

---

### Post by perixx on 2008-02-09
> have you looked into downloading a vanilla kernel and compiling it w/o smp support? What exactly do you mean with w/o smp support? I haven't copiled a kernel before, by the way... only a few apps, with altering success.

perixx

---

### Post by scxtt on 2008-02-09
basically, you get the source for a kernel - then run menuconfig on it selecting the options you want the kernel to have ... in this case, you wouldn't select SMP support.

i'm not going to say it's "easy", but it isn't all that hard ... the only time i've done it was w/ gentoo, and i'd used genkernel - but it worked fine.

---

### Post by perixx on 2008-02-10
Hmm.... so compiling such a kernel would result in one core completely disabled, thus I'd have to create another boot entry for that kernel, in order to have both options availible, right?
Sounds a little tedious to me - mostly the compiling, but also having to reboot every time I do want multi-threaded dual-core processing again :-k

If there was only a CLI command how to run an application with a dedicated core... I mean, there should be such a thing - it's even possible under Windows' taskmanager...
 
perixx

---

### Post by scxtt on 2008-02-10
well, to use **nosmp** (if it actually worked) would require a reboot each time ...

compiling a kernel doesn't take that much time AND using -j2 would compile it using BOTH cores ... i just did it in a VM last night (using source from kernel.org) and it didn't take all that much time (somewhere b/t 10min. and 20min. -- didn't watch it the whole time) ... after it was done, it didn't work, but i believe that's cause i need to work out the modules for that kernel (can't just reuse the initrd from the prev. kernel) ...
> If there was only a CLI command how to run an application with a dedicated core... I mean, there should be such a thing - it's even possible under Windows' taskmanager...really, i've never seen that ...

---

### Post by perixx on 2008-02-25
Ok, so I've tried out the following kernel switches in menu.lst:
```
nosmp
maxcpus=0
cachesize=512
```
I used them separately and in combination; at first I got the '...ACPI...invalid reference to irq 0' booting failure again. Since I first didn't notice the 'ACPI', I figured, it might be a good idea to shut it down in BIOS. And it even worked...

Alas, SeriousSam2 wouldn't boot in spite of this measure and crash with a 'core dumped' message again. In XP, starting with a single core or using 'seesaw' would let me at least play SS2 before I had applied the AMD dualcore patch.

Is there a program like 'seesaw' in Linux? Has anyone encountered similar problems with SS2 under Linux on an INTEL platform?

perixx

---

### Post by perixx on 2008-03-11
*gives it another try*

Someone knows about a core priority 'seesaw'-like app for linux, please?

perixx

---

