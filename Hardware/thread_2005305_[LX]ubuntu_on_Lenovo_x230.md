---
title: "[L|X]ubuntu on Lenovo x230"
date: 2012-06-17
forum: Hardware
---

### Post by antrek on 2012-06-17
Hello!

This is a brief report of my experience with [L|X]ubuntu on a new Lenovo x230 (i5 3320/HD4000, no discrete GPU).

I specify only the processor here, because other things (RAM, HDD) seem to be of no relevance.

So, first I installed Xubuntu 12.04. It installed, updated to the latest kernel, and worked for a while, but then it started to freeze randomly about once an hour, with nothing special going on (browsing, Eclipse/java compiling, etc). The screen was just freezing and the CPU fan went somewhat up, with no response to kb/mouse.

After that I installed regular Ubuntu 12.04. It installed, but froze during the update. I managed to finish the update (including the latest kernel - everything the system wanted to update by default) via Ctrl+Alt+F1, but after the update Ubuntu started to freeze at the login screen, and Ctrl+Alt+F1 was just switching to the dirty-orange background, without a console. So the system was not usable at all (maybe single user/root console would have worked - I did not try).

Then I installed Lubuntu 12.04, and everything seems to be working so far, no freezes. So the problem is not with the kernel, as somebody was suggesting in another thread, but probably with the X11/GPU/3D drivers.

To summarize, Lubuntu 12.04 works, Xubuntu freezes occasionally, and Ubuntu proper is not usable at all (freezes immediately).

I did not run any advanced GPU/3D tests, but regular stuff, including watching video through VLC, works.

---

### Post by fsando on 2012-06-18
Thanks for sharing your experience.

I'm looking to get a x230 (perhaps the tablet version) over the summer.
So I'll be watching if someone drops by with more or updated info.

---

### Post by mobad on 2012-06-18
[http://partiallysanedeveloper.blogspot.com/2012/05/ivy-bridge-hd4000-linux-freeze.html](http://partiallysanedeveloper.blogspot.com/2012/05/ivy-bridge-hd4000-linux-freeze.html)

The kernel in Ubuntu 12.04 doesn't seem to have great Ivy Bridge HD4000 support, you should just need to upgrade it.

The reason why it doesn't freeze in Lubuntu is probably because it doesn't use compositing.

---

### Post by aariel on 2012-06-20
Hey Antrek, fellow x230 owner here reporting on my own experiences.

I have been running Ubuntu 12.04 64-bit Desktop since I got my x230 last week, and almost everything worked perfectly out of the box. 

However, I found that whenever I started up any virtual machines (I tried Ubuntu 12.04 guests in VirtualBox and KVM / libvirt / virt-manager), I would experience complete lock-ups just like the ones you described at random intervals (usually within an hour).

After narrowing the problem down to the virtual machines, a friend recommended that I try the official 3.4 kernel release (the current release available in apt is 3.2). After installing this kernel, the experience for me was night and day. I went from locking up within an hour of starting up a VM, to not locking up at all. That was three days ago, but unfortunately I had a lock-up today, so I'm worried that the problem may not be completely resolved.

If you are interested in installing the 3.4 kernel, I used the one found here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/)

I downloaded the .debs and installed them manually.

I'm going to try to get a kernel crash dump the next time I experience a lock up, and if I find anything useful I'll report back in here.

---

### Post by antrek on 2012-06-21
Thanks, Aariel! 

After I had a freeze in Lubuntu with 3.2 (after two days w/o any issues), I tried 3.4, but it didn't work well - I don't remember exactly what was wrong. Then I installed 3.3.7, and now no freezes, even in Unity (didn't use Unity much - don't like it; I prefer Xfce/Xubuntu).

The only issue I have is a complete mess with sound cards - there are like 50 "internal" and 50 "external" listed (in VLC, for example - when choosing Audio output device), and sometimes sound playback is distorted.

I'm kind of disappointed with Canonical - they put a lot of effort into Unity, which is just not convenient for my usage pattern (s/w development: multiple windows/terminals) and neglect basic things like system stability.

---

### Post by fsando on 2012-06-22
> **antrek said:**
> Thanks, Aariel! 

After I had a freeze in Lubuntu with 3.2 (after two days w/o any issues), I tried 3.4, but it didn't work well - I don't remember exactly what was wrong. Then I installed 3.3.7, and now no freezes, even in Unity (didn't use Unity much - don't like it; I prefer Xfce/Xubuntu).

The only issue I have is a complete mess with sound cards - there are like 50 "internal" and 50 "external" listed (in VLC, for example - when choosing Audio output device), and sometimes sound playback is distorted.

I'm kind of disappointed with Canonical - they put a lot of effort into Unity, which is just not convenient for my usage pattern (s/w development: multiple windows/terminals) and neglect basic things like system stability.

I set up an old laptop for some testing, I soon gave up on unity and went for gnome-panel. Unity wasn't tight enough and the shortcuts didn't act predictably enough. Gnome-panel is almost exactly like gnome 2. So this is fine with me. I get the newest with what I like from the old. There are so many choices other than Unity and even Ubuntu itself can easily be replaced (just use Mint instead).

Though I didn't stay with unity I still respect what canonical is doing. They are aiming for mobile devices. It's a tremendous undertaking to create an entirely new interface, they've spent more than two years doing it and they are racing against the clock. If they fail Ubuntu may well disappear again or at least loose a lot of its momentum. So I really wish them luck they're gonna need it.

---

