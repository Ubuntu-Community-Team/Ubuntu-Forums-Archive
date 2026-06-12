---
title: "Intel 945 GM (i9xx) Graphics Problems"
date: 2009-07-02
forum: Hardware
---

### Post by Shibblet on 2009-07-02
I have three computers that I currently use.

I have a desktop (Dell Inspiron 531)
Dual Core AMD Athlon XP
Nvidia 8600 PCIe Video
250g & 500g HD

I have a Laptop (Dell Inspiron 1545)
Intel Core 2 Duo
Intel Graphics 945GM
250g HD

I have a Netbook (MSI Wind U100)
Intel Atom N270
Intel Graphics 945GM
80G HD.

Now, my desktop runs Ubuntu FLAWLESSLY.  But there were quite a few little additions I had to add in order to make it work that way.  (Nvidia Drivers, SMPlayer for vdpau, change Compiz settings to 60hz.)  

When the Nvidia drivers are installed, they update your xorg.conf for you. 

My Laptop has graphics issues.  I get tearing on video playback, and I get some screen flicker.

My Netbook has the same problems as my Laptop.  So I blame it on the 945GM Intel Graphics Adapter.

The xorg.cong looks to be "default".  And I don't know a thing about changing it.  I don't really even know if this is the problem.

Does anyone have a xorg.conf file on an MSI Wind with actual settings in it they could share?  I am assuming this is the problem.

---

### Post by Shibblet on 2009-07-03
Bumpity Bump-Bump.

---

### Post by Hobgoblin on 2009-07-03
Did you try a [search?](http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+graphics) because it's mentioned in nearly every "intel video jaunty" thread.

---

### Post by Shibblet on 2009-07-03
> **Hobgoblin said:**
> Did you try a [search?](http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+graphics) because it's mentioned in nearly every "intel video jaunty" thread.

I have.  This one has the most information.

[http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+video+jaunty]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+video+jaunty")

But I have to tell you, I'm not comfortable enough with terminal to understand what's going on there.

Isn't there an update available in the repository?

---

### Post by Hobgoblin on 2009-07-03
> **Shibblet said:**
> 

Isn't there an update available in the repository?

Not yet.

You could go back to 8.10, or put up with it and wait for 9.10

I found the safe configuration made enough difference (the .30 kernel made a big difference but broke more important things).  

You could also try disabling desktop effects, some people have said that helps flash video.

---

### Post by Shibblet on 2009-07-03
> **Hobgoblin said:**
> Not yet.

You could go back to 8.10, or put up with it and wait for 9.10

I found the safe configuration made enough difference (the .30 kernel made a big difference but broke more important things).  

You could also try disabling desktop effects, some people have said that helps flash video.

So this is going to be addressed in 9.10 Karmic?  It's a known bug then?

---

### Post by Hobgoblin on 2009-07-03
> **Shibblet said:**
> So this is going to be addressed in 9.10 Karmic?  It's a known bug then?

Did you read the thread both you and I linked to?

Yes it's known.

Yes (as far as I know) it should be fixed in 9.10, Karmic has a new Intel driver as well as a new kernel.

---

### Post by Shibblet on 2009-07-05
> **Hobgoblin said:**
> Did you read the thread both you and I linked to?

Yes it's known.

Yes (as far as I know) it should be fixed in 9.10, Karmic has a new Intel driver as well as a new kernel.

I walked through as much as I could, even to the "optimal" settings.  Downloaded the 2.8.30 Kernel, and it cleared up a lot of problems.  It majorly messes up if you turn on "Sync to VBlank" in your Compiz settings.

It seems sometimes, every time one bug is worked out, another pops up.  I know they're not directly related, but I waited for Jaunty so that my MSI Wind would have Realtek 8187 (Wireless) support, and then as soon as I get it, my graphics driver sucks donkeys.

You know, most people blame Ubuntu or Linux in general for these problems, I blame the hardware manufacturers.  If they would just support their product, this wouldn't happen.

But the funny part of this is, someone who isn't employed by Intel, fixed Intel's driver and released the fixes to the public faster than Intel could have.  That's why I love the open source community.

---

### Post by Hobgoblin on 2009-07-09
There is another fix you can try.

[Revert intel driver to 2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by vivichrist on 2009-11-17
is one of the cpu's at 100% ?

---

