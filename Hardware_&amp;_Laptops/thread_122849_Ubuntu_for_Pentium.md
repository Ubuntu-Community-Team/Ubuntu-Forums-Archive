---
title: "Ubuntu for Pentium?"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by dgermann on 2006-01-28
Hi--

Which version of Ubuntu, if any, would work with my old Pentium machine with 96 megs of ram?

If Ubuntu is not an option, what would you recommend?

Thanks!

---

### Post by earobinson on 2006-01-28
[dsl]("http://www.damnsmalllinux.org/")

---

### Post by MrFahrenheit on 2006-01-28
do a server install, then use either xubuntu-desktop or the icewm (there are other packages you need with icewm, try searching the forum for icewm)

---

### Post by christhemonkey on 2006-01-28
I used a standard install, but then changed to aewm++ window manager, extremely minimalist ( ie nothing, haha ) but it works faster for me with 64mb ram p2

---

### Post by dgermann on 2006-01-29
So folks--

What you are telling me is that Ubuntu, even say a couple of versions back, will not work with a Pentium machine? One of them says it will run if you have 1.8 gigs of space, and I do have one of these old boxes with 2.0.... I do have an old 4.10 install disk.

Thanks for the quick replies, folks!:D

---

### Post by PaganHippie on 2006-01-29
It may work, if you stick with the i386 kernel, but it'll be slow. If you seriously want to try it, stick as much RAM as you possibly can into the system (and let us know how it works out for you).  You'll want a minimum of 256 MB.

Alternatively, you may want to check out the Ubuntu-Lite project at [http://ubuntulite.org/]("http://ubuntulite.org/")

---

### Post by markcaetano@gmail.com on 2006-01-29
i disagree
i have a celeron 500mhz with 128 ram
and it runs like an early pentium 4:mrgreen:

---

### Post by moopere on 2006-01-29
[QUOTE=markcaetano@gmail.com]i disagree
i have a celeron 500mhz with 128 ram
and it runs like an early pentium 4:mrgreen:[/QUOTE]

I've got a Celly 400 with 128MB here running Breezy and it runs like a dog with no legs :-?

This is one of my favourite subjects right now, I can't believe how slow the new distro's are becoming.  Well, I guess what I really mean is that I can't _understand_ whats making them so slow.

After a ton of empirical testing using a myriad test machines I have here (from 486DX2/66 through P4/3GHz) I'd have to say that Ubuntu Gnome drives me nuts on anything less than an early coppermine with 256MB (about 600MHz).

Ive tried XFCE (which used to be fast!), almost no difference.  Although the memory footprint appears to be a lot lower with xfce, we appear to be completely CPU bound with slow processors.  

XFCE _used_ to be mighty quick, almost like windowmaker, but since the change to V4 and gtk its a dog like gnome is (smaller dog though).

Speed and 'fast enough' is so user subjective its not funny, and usually not worth debating - noone can argue the numbers though, so benchmarking is what we need to be doing.  I'm going to fire up a wiki page soon with some results of simple bench's I've been doing.

If you search these forums you will see  a post to which I replied, in which I did some testing on i386, i686 and i686SMP kernels, my advice would be not to bother wasting your time trying to optimise the hell out of your kernel.  I'm pretty interested to see if theres a measurable difference in compiling the whole of ubunutu for your arch though.  

apt-build would appear to allow just such a path and I think would provide a closer match when comparing benchmarks than say an ubuntu standard versus gentoo comparison might provide.

Cheers,
Craig

---

### Post by az on 2006-01-30
[QUOTE=moopere]I've got a Celly 400 with 128MB here running Breezy and it runs like a dog with no legs :-?

This is one of my favourite subjects right now, I can't believe how slow the new distro's are becoming.  Well, I guess what I really mean is that I can't _understand_ whats making them so slow.

...

Ive tried XFCE (which used to be fast!), almost no difference.  Although the memory footprint appears to be a lot lower with xfce, we appear to be completely CPU bound with slow processors.  

XFCE _used_ to be mighty quick, almost like windowmaker, but since the change to V4 and gtk its a dog like gnome is (smaller dog though).

Craig[/QUOTE]

Dapper is turning out to be a lot faster than breezy.  It looks like it will run a lot better on older hardware.  It boots faster and firefox renders pages as fast as any other browser on any other platform.

I agree about XFCE - On a processor with no cache, it is slow as hell.  On a PII with a big cache, it is much faster than Gnome, but gnome runs perfectly well on a pII 400Mgz with a 512 cache!

Icewm has always done it for me for older and slower hardware.

---

### Post by moopere on 2006-01-30
[QUOTE=azz]Dapper is turning out to be a lot faster than breezy.  It looks like it will run a lot better on older hardware.  It boots faster and firefox renders pages as fast as any other browser on any other platform.

I agree about XFCE - On a processor with no cache, it is slow as hell.  On a PII with a big cache, it is much faster than Gnome, but gnome runs perfectly well on a pII 400Mgz with a 512 cache!

Icewm has always done it for me for older and slower hardware.[/QUOTE]

Mmm, interesting, I've got a PII450/512K someplace around here...I should bench it as against the Celly 400 and see....  Do you think its the cache at work here or the FSB speed to RAM/IO?

As for Dapper, yes, I agree, shaping up nicely.  I've yet to try it out on any older hardware though so I'm not sure if the optimisations, such as there are, will be enough to make the <600MHz beasts workable.

I used to love ICEWM, but configuring the damn thing is just too much hassle.  I stopped using it when there was a flurry of acitivity which kept on breaking my tweaked configs (arrghh!).  If someone were to write a decent configuration/menu utility I think you'd see an instant resurgance of people using it.

Cheers,
Craig

---

### Post by az on 2006-01-30
[QUOTE=moopere]Mmm, interesting, I've got a PII450/512K someplace around here...I should bench it as against the Celly 400 and see....  Do you think its the cache at work here or the FSB speed to RAM/IO?

As for Dapper, yes, I agree, shaping up nicely.  I've yet to try it out on any older hardware though so I'm not sure if the optimisations, such as there are, will be enough to make the <600MHz beasts workable.

I used to love ICEWM, but configuring the damn thing is just too much hassle.  I stopped using it when there was a flurry of acitivity which kept on breaking my tweaked configs (arrghh!).  If someone were to write a decent configuration/menu utility I think you'd see an instant resurgance of people using it.

Cheers,
Craig[/QUOTE]

I ran a VIA C3 733 MHz/32k cache for the longest time and when I ran a PII400/512, I could barely see a difference.  Now I am running a PIII 700 (100 MHz FSB) and it is about twice as fast as the VIA.

I could never get icewm control panel to run.  I haven't tried in a while, though.

[http://www.phrozensmoke.com/projects/icewmcp/](http://www.phrozensmoke.com/projects/icewmcp/)
[http://www.phrozensmoke.com/projects/icewmcp/icewmcp1.png](http://www.phrozensmoke.com/projects/icewmcp/icewmcp1.png)

---

### Post by dgermann on 2006-01-30
Well folks, lotsa differences of opinions on this one. Sounds like I can either try it and see if I can stand it, or save my pennies and buy a new box and not bother.

This conversation has really been a good one--I am learning a lot. Thanks, folks!

---

### Post by nalmeth on 2006-01-30
I was running Ubuntu on an old computer with 96 megs of ram. I don't dig XFCE all that much, but it of course made it faster. After a while I just used Gnome anyway. Sure the computer isn't fast, but its an old computer that is now doing more than collecting dust. 

Ubuntu works just fine with it.

---

### Post by dgermann on 2006-01-31
nalmeth--

What version of Ubuntu do you have on the 96 meg box? How much disk space?

Thanks. You have given me hope....

---

### Post by zojas on 2006-01-31
according to the ubuntu support faq, the server install only needs about 350mb of disk space. (type 'custom' at the boot prompt to get the server install)

---

### Post by zojas on 2006-01-31
I happen to have a 90MHz pentium with 128mb of ram, currently running gentoo linux. this machine has X on it, but I never run X on the desktop, I usually ssh in and display any X apps I might run remotely. typically the only X app I run is gvim. the machine is my firewall and router. it has a 2.6 kernel with a good set of iptables rules. it also runs bind, configured as a caching name server for my network.

I used to have redhat 7.2 on it when it first became my firewall. the conversion to gentoo took about a week, checking on the machine 3 times a day. the machine seems faster with gentoo than it did with redhat. I didn't do any timing though. everything on the system was compiled with '-O2 -march=pentium -fomit-frame-pointer'

I doubt I'll ever switch that box away from gentoo, since it works now. I don't mind if major updates (like glibc and gcc) take a few days, it's just sitting there happily routing packets.

in about 1999 or 2000 I used to run a light desktop on it (blackbox) and did some development using it. gvim runs great. compiles take some time though. I think it had redhat 6.2 on it then. but it was definitely usable.

the only downside to running gentoo on it is that python runs pretty slow

---

### Post by sabredog on 2006-01-31
I am going to try and install Xubuntu on my old P166MMX with 128Mb RAM and see how that runs. 

I am not a big fan currently of Feather Linux and Fluxbox.

---

### Post by moopere on 2006-02-01
[QUOTE=sabredog]I am going to try and install Xubuntu on my old P166MMX with 128Mb RAM and see how that runs. 

I am not a big fan currently of Feather Linux and Fluxbox.[/QUOTE]

You are not going to enjoy the ride with Breezy believe me.  I've got a P200 (non mmx) 96MB RAM running Breezy as my firewall/NAT.  I've run it with XFCE and gnome and theres no difference in interactivity as far as I can tell - XFCE is small on RAM, but with gnome and XFCE I appear to be CPU bound.  Gnome is running, but its no fun.

As a result of this thread though I have run up another old box to check how dapper is going.  Its a P166 (mmx this time) and only 64MB RAM, 1.2GB disk.  I have cherry picked my install as a full ubuntu-desktop wouldn't fit on the disk, but I ended up with a good gnome desktop, firefox, etc etc (left out all the python stuff and OpenOffice + other junk)

I've just done a series of tests in single user mode and am surprised - this box is faster than the P200!  

Not fast, but faster, I've timed a few things like login, starting firefox etc and the speed difference is measurable.  I'm going to up the P200 tomorrow to Dapper, prelink it then post some "before and after" timings for all to see.

If you're just messing around with this box I'd suggest having a look at Dapper right now.  Its only got a few reasonably serious bugs, nothing to stop you having a bit of fun.

Cheers,
Craig

---

### Post by moopere on 2006-02-02
I still have not had a chance to upgrade my P200 to Dapper, but I did do some before and after testing with the P166MMX 64MB - the testing being 'before' prelinking and 'after' prelinking.

I didn't compile anything, just installed a carefully picked set of Dapper debs, running a stock Ubuntu i386 kernel, installed prelink, changed the conf file for it, and ran some tests (in single user mode).  

I'll put the results up on my benchmark page (as soon as I get _that_ done), but for those that can't wait...don't bother with prelinking on old boxes that are CPU bound.  Seriously.  It looks like it might be making things slower.

My strong suspicion is that if you have a bit extra CPU, but are IO bound (probably disk more than anything else on an old box) then prelinking would probably make a difference - this should (hopefully)  show up when I do the P200.

Oh, and the placebo effect is in full swing too.  I could have sworn that the box was faster after I prelinked it - but you can't argue with the numbers, when I got a stopwatch out my 'speedy feeling' was clearly wrong.

Cheers,
Craig

---

### Post by mohapi on 2006-02-03
I put straight Ubuntu onto a 233Mhz/64Mb laptop, but it was kind of laggy. I swapped it out for Xubuntu and it flies. DSL was lightning fast, but a little sparse for my taste. I'll save that for my next project ... a Presario 1020! Whee!

---

