---
title: "What kernel is best for AMD Duron 1600?"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by Luke771 on 2006-01-30
The title pretty much says it, I add only that I *did* try to figure it out by reading other threads and How-Tos, but I couldn't: Is it the 686 or the k7 the one I need? Or should I stick with the 386?

---

### Post by Sokraates on 2006-01-30
Take a look at [this](http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel) thread.

On a short notice: 686 is **strictly** Intel. k7 is **strictly **AMD.

---

### Post by Luke771 on 2006-01-30
Thanks for the answer, Socrates (wow, I feel like I was Plato) That was exactly the thread that made me wonder what kernel I should install, I tried the k7 and I had some problems: the screen started to flicker, go on and off and so on, I couldnt even log in, then I got tired of trying and reinstalled the whole OS from scratch, which solved the problem (well, ok, that solves almost any problem, but it's a bit radical).
Now I'm back on 386 nd it works fine, but I dont' really know if the screen problem was caused by the kernel or not, maybe it was something else that I did: after all it *did* work fine for a couple of weeks or so and the flickering-screen thing started when I hitted ctrl-alt-backspace to get out of a frozen install... well, maybe *that* was a bit radical too, but anyways: now I dont' know if I should install the k7 again or stick with the 386.

---

### Post by az on 2006-01-30
To install the k7 kernel, install the linux-k7 package.  That pulls in the linux-restricted-modules package you need to keep your graphics running if you are using the proprietary nvidia or ati drivers....

The same goes for any other arch

Example:

linux-686

---

### Post by GTvulse on 2006-01-30
[QUOTE=Luke771]The title pretty much says it, I add only that I *did* try to figure it out by reading other threads and How-Tos, but I couldn't: Is it the 686 or the k7 the one I need? Or should I stick with the 386?[/QUOTE]
An AMD Duron is a K6 chip. There is no such beast available in the repositories but, if you feel adventurous, you can compile it yourself with the right settings for a K6 CPU. (Hint, you need at least, kernel-package, fakeroot, gcc-3.4, ncurses-devel and the sources package for your running kernel, in addition to build-essential. All available from the main and universe repositories; do read kernel-package documentation. Don't read the howtos in the forums, most are confused and give even dangerous advice such as tell you to use sudo for every command.).

---

### Post by az on 2006-01-30
I really though that the Duron was a K7:

"This package will always depend on the latest complete Linux kernel available
 for AMD Duron/Athlon."

---

### Post by Sokraates on 2006-01-31
[quote=Luke771]I tried the k7 and I had some problems: the screen started to flicker, go on and off and so on, I couldnt even log in, then I got tired of trying and reinstalled the whole OS from scratch, which solved the problem (well, ok, that solves almost any problem, but it's a bit radical).[/quote]

Usually you don't need to reinstall the whole system if a kernel causes problems. The old kernel(s) are kept wich the newest one being the new default in GRUB. 

If it causes problems, just select another kernel or the recovery mode in GRUB. If it doesn't help, something else is wrong.

---

### Post by GTvulse on 2006-02-01
[QUOTE=azz]I really though that the Duron was a K7:

"This package will always depend on the latest complete Linux kernel available
 for AMD Duron/Athlon."[/QUOTE]
In theory, yes. But the Duron doesn't have 3dNow+ instructions, its support for SSE is weak, if existent at all, and its backplane bus has been maimed on purpose. It is the same problem as with the Semprons. They are lobotomized Atlhon XP/64 chips, not worth the money you throw at them, although if you are short of money they will seem like a godsend but only for the first week ;-).

---

### Post by az on 2006-02-01
[QUOTE=dradul]In theory, yes. But the Duron doesn't have 3dNow+ instructions, its support for SSE is weak, if existent at all, and its backplane bus has been maimed on purpose. It is the same problem as with the Semprons. They are lobotomized Atlhon XP/64 chips, not worth the money you throw at them, although if you are short of money they will seem like a godsend but only for the first week ;-).[/QUOTE]
Will it run the 386 kernel better than the k7, then?

---

### Post by GTvulse on 2006-02-03
[QUOTE=azz]Will it run the 386 kernel better than the k7, then?[/QUOTE]
Sorry for the delay :-)

For a Duron? I'm afraid so. The ideal would be to install a kernel tuned for the K6 architecture, or if you are in a rush or need some of the binary-only drivers in the restricted modules packages, using the 686 kernel. It is false that 686 is for Intel chips only. The K6 is the moral and technological equivalent of a Pentium2, in the same venue as an Athlon-XP is the equivalent of a Pentium 3 (but performs as a Pentium 4 ;-)). There is a lot of confusion about what an i686 is and many think that it is the code name of the pentium 3 (I used to believe so), but nope. The 586 is the original Pentium and the 686 is the PentiumPro. 

As a corollary, if one has a Pentium 3 or a Pentium 4 and wanted to compile optimized binaries for it, one should use "gcc -march=pentium3" or "gcc -march=pentium4" . All the story is in gcc's texinfo documentation ("apt-get install gcc-doc") but there are major hints in the gcc man page as well  (installed by default, "man gcc") in the section titled "Intel 386 and AMD x86-64 Options". The fact is that if you have a very flashy dual-core Pentium4 and you want to squeeze all the juice out from that fruit, you need to compile your kernel yourself. And even if you have a lowly 5-year-old Pentium 3, you still want to compile your kernel for optimum performance. The reason I can see why the default kernel is a 386 binary is because all Intel and AMD chips are backwards compatible and use the 386 as a standard baseline, therefore you can run a 386 kernel even in a 15-year-old computer, including the control systems of the Space Shuttle ;-)

---

### Post by GTvulse on 2006-02-03
But watch this: [http://people.ubuntu.com/~scott/20060131_dropping-pre-i686_jbailey-doko.ogg](http://people.ubuntu.com/~scott/20060131_dropping-pre-i686_jbailey-doko.ogg)

There is already a push to leave pre-i686 behind...

---

