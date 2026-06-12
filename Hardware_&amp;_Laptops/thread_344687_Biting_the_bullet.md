---
title: "Biting the bullet"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by NY Tel Guy on 2007-01-23
Ok I know nothing about Linux but am a legend in my own mind for Windows.  Currently running XP Pro on all machines and want to start to learn Ubuntu.
So I don't get OS shock I plan to dual boot the system on my IBM Thinkpad A20 P with 512k RAM, 40 gig HD.

Any general advice etc.?  But primarily once I burn the image to a CD - is installing it as a dual boot similar to when I used to dual boot Win 98 and NT?
Thanks

---

### Post by AndrewB on 2007-01-23
A laptop is not a painless platform to start learning on.  better to dedicate a older desktop to the job, the likelyhood of all your hardware being properly detected and configured is much, much higher.

just MHO.
Andrew

---

### Post by NY Tel Guy on 2007-01-23
[FONT=Trebuchet MS][SIZE=3][COLOR=Blue]Thanks but I don't own a desktop...:o.  I use the laptops in place of them and use docking stations.  I'll try it out on one of my machines and see what happens.  Worst thing would be it would have to be re-formatted for XP which is what happened when I wanted to erase the evil copy of Vista.[/COLOR][/SIZE][/FONT]

---

### Post by darrenm on 2007-01-23
Thinkpads are apparently pretty good with Ubuntu.

Although the Windows legends are normally the people who find it hardest to learn a different way of doing things.

If you understand how computers work and not just how Windows computers work then you'll love it :)

Good luck and ask anything here.

---

### Post by NY Tel Guy on 2007-01-23
[FONT=Trebuchet MS][COLOR=Blue]Yes I should have clarified my self-assessment...lol
I have only focused on Windows PC's but have a good mind for all of this.  I already burned an image to a CD and have been experimenting with it on the Thinkpad.  Seems to run fine and so far I have just chosen to run it from the CD to see how it performs.  I'll keep everyone posted.
I just don't want to pay Microsoft another dime for Vista or anything else if I can avoid it.  I'm even considering a Mac as my next machine just to challenge myself and have fun.
Thanks[/COLOR][/FONT]

---

### Post by darrenm on 2007-01-23
> **NY Tel Guy said:**
> [FONT=Trebuchet MS][COLOR=Blue]Yes I should have clarified my self-assessment...lol
I have only focused on Windows PC's but have a good mind for all of this.  I already burned an image to a CD and have been experimenting with it on the Thinkpad.  Seems to run fine and so far I have just chosen to run it from the CD to see how it performs.  I'll keep everyone posted.
I just don't want to pay Microsoft another dime for Vista or anything else if I can avoid it.  I'm even considering a Mac as my next machine just to challenge myself and have fun.
Thanks[/COLOR][/FONT]

If you use the live cd then ignore the speed altogether. Forget the Mac, it wont be anywhere near as enjoyable.

---

### Post by allwin on 2007-01-23
> **NY Tel Guy said:**
> Ok I know nothing about Linux but am a legend in my own mind for Windows.  Currently running XP Pro on all machines and want to start to learn Ubuntu.
So I don't get OS shock I plan to dual boot the system on my IBM Thinkpad A20 P with 512k RAM, 40 gig HD.

Any general advice etc.?  But primarily once I burn the image to a CD - is installing it as a dual boot similar to when I used to dual boot Win 98 and NT?
Thanks

Yeah, it should dual boot just fine.  Your chief problems will be with multimedia, USB devices, wireless, and if you decide to play around, getting Beryl to work with whatever video is on that laptop.  Oh, and power management and the touchpad.

Just remember to go out and get AUTOMATIX and ENVY (if you have nVidia onboard), which simplify a lot of those problems.  And install NDISWRAPPER and have a go at getting your wireless working using pieces parts of the Windows driver files.  Not to mention there are splendid things out there for free, such as a driver that reads EXT3 file systems for Windows, and the XFCE window manager which is faster than GNOME or KDE, but as you can imagine, often limited in capabilities in ways you wouldn't expect.

If your LIVE CD runs OK and most of your stuff seems to work, I'd say have a go at installing it.  Eventually you'll get most of it working.  Don't forget you'll probably want to use HDPARM to tune up your disk access after installing as often DMA and 32 bit access are not enabled after the install.

And you'll have a time getting XORG.CONF set up just right for your desired screen res, too.  Often that's a battle.

Stuff like MIDI, webcam, and simple video editing (non DV cameras) just ain't there yet.  Sound can be a problem (distortion, volume, stuttering).  But a lot depends upon exactly what hardware you've got.  Try it and see.

---

### Post by darrenm on 2007-01-23
> **allwin said:**
> Yeah, it should dual boot just fine.  Your chief problems will be with multimedia, USB devices, wireless, and if you decide to play around, getting Beryl to work with whatever video is on that laptop.  Oh, and power management and the touchpad.

Why wouldn't multimedia, USB devices, wireless and Beryl just work? On almost any VGA adapter you just add the Beryl repo and apt-get install beryl* then press alt-f2 and type beryl-manager and it works.

> **allwin said:**
> Just remember to go out and get AUTOMATIX and ENVY (if you have nVidia onboard), which simplify a lot of those problems.  

I think Automatix causes more problems than it fixes and the user is far better following the Ubuntu wiki to get any extra codecs etc. they need so they understand how apt-get, synaptic and debs work as early as possible.

> **allwin said:**
> And install NDISWRAPPER and have a go at getting your wireless working using pieces parts of the Windows driver files.  

Depending on the wifi adapter, it should just work with Edgy+ Only use ndiswrapper if you need it.

> **allwin said:**
> Don't forget you'll probably want to use HDPARM to tune up your disk access after installing as often DMA and 32 bit access are not enabled after the install.

I'd say very few cases this happens. DMA has always been enabled on any PC I install Ubuntu on.

> **allwin said:**
> And you'll have a time getting XORG.CONF set up just right for your desired screen res, too.  Often that's a battle.

In what way? If you need a non-standard res surely you just add the resolutions you need to xorg.conf?

> **allwin said:**
> Stuff like MIDI, webcam, and simple video editing (non DV cameras) just ain't there yet.  Sound can be a problem (distortion, volume, stuttering). 

I've never had any audio problems with various hardware

 > **allwin said:**
> But a lot depends upon exactly what hardware you've got.  Try it and see.

Sounds like you've had lots of problems? Not everyone has the same hardware dude :biggrin:

---

