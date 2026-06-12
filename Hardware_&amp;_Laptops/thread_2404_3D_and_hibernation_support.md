---
title: "3D and hibernation support"
date: 2004-10-27
forum: Hardware &amp; Laptops
---

### Post by Jerrac on 2004-10-27
Hey! I am thinking of installing Ubuntu soon, but I am wondering about a couple questions. Could you answer them for me? Thanks!

Does Ubuntu have 3D acceleration support for the ATI Radeon IGP 345 chipset?

And can you use hibernation/suspend on a laptop? How fast is it?

Thanks!

---

### Post by daniels on 2004-10-28
I believe the IGP345 stuff should work alright.

As for suspend/hibernate, it depends what sort of laptop you have.  Unfortunately we haven't had too much time to test with a very wide range of hardware, so we're still figuring out which modules we need to remove, et al.  But if you use the thinkpad-x40-support package available at [http://people.ubuntu.com/~daniels/x40/](http://people.ubuntu.com/~daniels/x40/), you should be able to get suspend working just fine without too much fiddling.

Hibernate is a little trickier, as we haven't really focussed on that.

---

### Post by Jerrac on 2004-10-29
So my graphics card would have 3d support? Cool!

Um, I was catagorizing hibernation and suspend as basically the same thing. It would be where you would save all the stuff in memory to the hard drive so that it starts back up really fast. Like when you hibernate in Windows XP.

---

### Post by daniels on 2004-10-29
There is suspend-to-RAM (generally known as 'standby' or 'suspend', and technically known as S3), and suspend-to-disk (generally known as 'hibernate', and technically known as S4).  We have fairly good S3 support, but S4 isn't quite ready yet.  Some people are reporting success with the swsusp kernel patchset, but it's not in our default kernel.

---

### Post by Jerrac on 2004-10-30
[QUOTE=daniels]There is suspend-to-RAM (generally known as 'standby' or 'suspend', and technically known as S3), and suspend-to-disk (generally known as 'hibernate', and technically known as S4).  We have fairly good S3 support, but S4 isn't quite ready yet.  Some people are reporting success with the swsusp kernel patchset, but it's not in our default kernel.[/QUOTE]
 Ah, ok, thanks for the clarification. Sometimes it is confusing. I hope you get the hibernate stuff working good! It is one of the reasons I haven't totally switched over to linux yet. My laptop really needs the hibernation, especially since I am at college.

Thanks again!

---

### Post by mattheweast on 2004-10-30
Hi there.

I have an IGP 340M video card, and 3d acceleration does not work out of the box with ubuntu, which does not surprise me at all as I believe it was solved in the most recent X11 releases (for example xorg version 6.8 ). I will try and solve the problems by compiling the dri modules as I have done with other distros. If I succeed I will post it here!! :)

X Matt

---

### Post by daniels on 2004-11-01
[QUOTE=Jerrac]Ah, ok, thanks for the clarification. Sometimes it is confusing. I hope you get the hibernate stuff working good! It is one of the reasons I haven't totally switched over to linux yet. My laptop really needs the hibernation, especially since I am at college.[/QUOTE]

You'll be surprised what S3 can do -- I've never bothered with suspend-to-RAM, because I find that losing all of 5% battery for every 8 hours in suspend-to-RAM is perfectly acceptable. :)

---

### Post by Jerrac on 2004-11-02
Seriously?! Wow, that is pretty good. 

What kind of heat output do you get with that? Because my laptop likes to spend time in the backpack.

Oh, and is there a way to dim the laptop screen? For better power management?

My laptop has a regular Pentium 4, not a Pentium M.

---

### Post by daniels on 2004-11-03
[QUOTE=Jerrac]Seriously?! Wow, that is pretty good.[/QUOTE]

The X40 is a stellar laptop all up -- phenomenal battery life, incredibly light, and doesn't use almost any battery.  I started off convinced that I wanted a 15" PowerBook, but at Oxford, Thom May and Matt Garrett convinced me that I really wanted an X40.  I was kind of unsure for quite a while, but when I got home, sliced open the boxes, and lifted it out, I was totally sure.

> What kind of heat output do you get with that? Because my laptop likes to spend time in the backpack.

It runs very, very cool normally, but virtually no heat in S3, which is rad.  I carry mine around in my bag all the time, and don't even notice it (and that's not just because of the weight).

> Oh, and is there a way to dim the laptop screen? For better power management?

This is generally a video BIOS thing, so check in your BIOS.  Mine has a setting to do this, which it does -- full brightness on external power, slightly dimmed when not.  But there are also hardware brightness buttons.

> My laptop has a regular Pentium 4, not a Pentium M.

Ah, then you'll get a lot more heat, and it will use a lot more power.  Sorry.

---

### Post by elempoimen on 2004-11-04
Has anyone tested this on a Thinkpad T23?  I tried it, but got display corruption.  It suspends OK, but upon resume I end up with a text-mode screen full of gibberish.  I tried to manually switch terminals, just in case I'd ended up back at tty1, but nothing.  I had to hard reset.  I installed the package as instructed and added the line to the kernel boot instruction...

I'd be happy with S3, although I'd really like S4, too.  I think I did get S3 working in MEPIS, maybe you'd want to talk to them.  I also had S4 half-working...but I couldn't get a resume from it.  I'm dual booting with XP, if that would make a difference (I wouldn't think so, as XP hibernates and resumes just fine).

---

### Post by elempoimen on 2004-11-04
As an addendum to my earlier post, my Thinkpad works the same way without the X40 package.  Just thought I'd mention it...

Gee, I wish Linux had decent power support...

---

### Post by Jerrac on 2004-11-10
[QUOTE=daniels]I believe the IGP345 stuff should work alright.
[/QUOTE]
 :cry: It doesn't. I finally installed Ubuntu to my hard drive, the I installed Tuxracer and Tuxkart. Neither runs well, very slow framerate. I am assuming it is because of the hardware acceleration. Any other suggestions?

---

### Post by daniels on 2004-11-10
[QUOTE=Jerrac]:cry: It doesn't. I finally installed Ubuntu to my hard drive, the I installed Tuxracer and Tuxkart. Neither runs well, very slow framerate. I am assuming it is because of the hardware acceleration. Any other suggestions?[/QUOTE]X.Org is in Hoary, which should have proper DRI for you ...

---

### Post by Jerrac on 2004-11-11
[QUOTE=daniels]X.Org is in Hoary, which should have proper DRI for you ...[/QUOTE]
 So how to I get that? I don't see a download for the hoary release.

Thanks!

---

### Post by Jerrac on 2004-11-12
Well, I figured out how to get Hoary, just look at the announcements... Heh.

---

### Post by Jerrac on 2004-11-27
[QUOTE=Jerrac]Well, I figured out how to get Hoary, just look at the announcements... Heh.[/QUOTE]
 And I should post that my graphics are working great now with Hoary! Yay! First time I have ever had 3d accel with linux on my laptop. Very happy with Ubuntu so far, it even detected my wireless card and network perfectly without me having to config anything. :D

Now all I have to figure out are my function keys and suspend to ram. :D

---

### Post by jdong on 2004-11-27
Can't say much good stuff about laptop ACPI support ([http://ubuntuforums.org/showthread.php?p=24951#post24951](http://ubuntuforums.org/showthread.php?p=24951#post24951))


But swsusp2 is definitely a robust solution. On my desktop, an average hibernate takes about 10 seconds from command to poweroff, and about half of that to read everything back (then again, that's an Athlon64 with SATA drives)


Chances are that S3 suspend won't work, but swsusp2 suspend-to-disk will work great. However, you're gonna have to patch that into the kernel manually. Always get the latest version -- lots of kernel patchsets include older versions of swsusp2 -- often times for me,the older versions fail.


swsusp/pmdisk (in official kernel) somewhat work, but they have the annoying destroy-the-cache behavior, which definitely causes a noticeable speed impact on my 512-1024MB RAM Linux systems.


Again, I recommend a custom kernel compile with the latest swsusp2 and acpi4linux patches.. Good luck!

---

