---
title: "AspireOne 751h: fan control with Ubuntu 12.04"
date: 2012-10-01
forum: Hardware
---

### Post by ventikappa on 2012-10-01
Ubuntu 12.04 apparently comes with version 0.5.24 of acerhdf module, which is not the latest version according to [author's site]("http://piie.net/").
With version 0.5.24 of acerhdf, fan control module does not load at boot on AO751h.
I could confirm that by using well known 'dmesg | grep acerhdf' and finding an error about unsupported bios version.
By following instructions given here I could download, compile and install latest version of acerhdf (i.e 0.5.27, as of today), as well as configure it.
Immediately after boot, the very annoying fan noise peacefully stopped :-)
Having me also a 128 SSD drive on my machine, I can now enjoy the beautiful silence!
 - Carlo

---

### Post by ahallubuntu on 2012-10-01
Out of curiosity, how does your Acer work in general with 12.04?  I assume you had to install some hacks to get it to work.  My 751h has 11.04 on it (with special video driver, etc. as recommended elsewhere) and has issues with the video driver.  The resolution is correct, but if I open too many windows (use too much RAM I assume), the display goes nuts (diagonal lines), and suspend freezes and requires a hard restart about 1/10 times.   Plus, it is very, very slow.  I used my 751h on a long vacation recently and it was very frustrating to use.  I said, "Never again!"  Time to put the XP drive back in it and get rid of it and buy something newer that has good Linux support.   Not sure if it is worth the trouble of trying 12.04 on it or not.

---

### Post by offgridguy on 2012-10-01
> **ahallubuntu said:**
> Out of curiosity, how does your Acer work in general with 12.04?  I assume you had to install some hacks to get it to work.  My 751h has 11.04 on it (with special video driver, etc. as recommended elsewhere) and has issues with the video driver.  The resolution is correct, but if I open too many windows (use too much RAM I assume), the display goes nuts (diagonal lines), and suspend freezes and requires a hard restart about 1/10 times.   Plus, it is very, very slow.  I used my 751h on a long vacation recently and it was very frustrating to use.  I said, "Never again!"  Time to put the XP drive back in it and get rid of it and buy something newer that has good Linux support.   Not sure if it is worth the trouble of trying 12.04 on it or not.

If I may jump in here,although i am not familiar with the 751h, i do have a
5735z that works well with ubuntu 12.04

---

### Post by offgridguy on 2012-10-01
> **ventikappa said:**
> Ubuntu 12.04 apparently comes with version 0.5.24 of acerhdf module, which is not the latest version according to [author's site]("http://piie.net/").
With version 0.5.24 of acerhdf, fan control module does not load at boot on AO751h.
I could confirm that by using well known 'dmesg | grep acerhdf' and finding an error about unsupported bios version.
By following instructions given here I could download, compile and install latest version of acerhdf (i.e 0.5.27, as of today), as well as configure it.
Immediately after boot, the very annoying fan noise peacefully stopped :-)
Having me also a 128 SSD drive on my machine, I can now enjoy the beautiful silence!
 - Carlo

I am curious here, as a lot of acer laptops have a problem with overheating,
is this not a concern?

---

### Post by ahallubuntu on 2012-10-01
> **offgridguy said:**
> If I may jump in here,although i am not familiar with the 751h, i do have a
5735z that works well with ubuntu 12.04

Thanks, but the AO751H is a special case, along with several other netbooks that unfortunately use Intel's GMA500 "Poulsbo" chipset.  Intel licensed this chipset from someone so has not provided open support for it.  Linux support for it has been spotty at best and has traditionally required many hacks to make everything work.  There are some open source drivers now that have been reserve engineered, I believe, by developers.  Each new release of Ubuntu seems to work a little better/easier, but I'm not sure how much more time I want to invest trying make yet another version of Ubuntu work on this slow, poorly-supported hardware...

---

### Post by offgridguy on 2012-10-01
ahallubuntu;  Thank you for the clarification.  In my rather limited experience, I have found
that learning and applying ubuntu in real world operation is very time consuming, regardless
of the hardware it is installed on.

---

### Post by ahallubuntu on 2012-10-01
> **offgridguy said:**
> ahallubuntu;  Thank you for the clarification.  In my rather limited experience, I have found
that learning and applying ubuntu in real world operation is very time consuming, regardless
of the hardware it is installed on.

In my experience, some hardware is much easier than other hardware.  Desktops are infinitely easier than laptops to deal with, too.  I have installed Ubuntu on many desktops often without issue (except in rare cases).  I used to volunteer for a local computer recycler that would install Ubuntu en masse on  many computers: they would make the exact same image on a pile of hard drives and you would just install a drive into the next desktop.  Maybe 95% of time, it would work perfectly.  Then again, they never worried about suspend/hibernate/resume.

Laptops are more difficult, often because of the wireless cards.  My Dell laptop was very easy, though.  I put an Intel wireless card in it, and it worked pretty much automatically with 10.04 .  The tweaks I've had to do are roughly the same kind of stuff I've needed to do in Windows laptops, more or less, to get things working the way I've wanted.

These days, I try to choose laptops based on their compatibility with Linux.  I bought my Acer AO751h before I was using Ubuntu on laptops.  I will research future laptop hardware before buying it based on its compatibility with Linux.

---

### Post by ventikappa on 2012-10-04
Luckily my experience is not as bad as yours.
After having applied the small fixes and tweaks suggested [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") I'm now having a fairly usable machine.
For instance, I once tried out and kicked open all LibreOffice applications, Synaptic, Chrome and Gedit at the same time: I had no issues at all with video quality.
Of course it does run on an Atom processor, DDR2 RAM, etc. so you need to be a bit more patient than with newer and more powerful machines , but still I intend to give my AO751h a try over the next months in SOHO kind of activities.

---

### Post by ventikappa on 2012-10-04
> **offgridguy said:**
> I am curious here, as a lot of acer laptops have a problem with overheating,
is this not a concern?
Hopefully it seems not to be the case at least for me.
I check it every now and then with 'sensors' and the reported temperature is in the 50's (°C, obviously).
For sure, having replaced a spinning HD with an SSD helps to keep internal temperature low.
However, whenever the machine gets more loaded the fan kicks in for a few seconds every minute or so, so it seems that the tweak I indicated works correctly.

---

### Post by Catherine29 on 2012-11-03
@vetikappa

so how did you get acerhdf to work exactly? 
when i try 'dmesg|grep acerhdf' i get: 'acerhdf: unknown (unsupported) BIOS version Acer            /AO751h           /V0.3210, please report, aborting!'

so what exactly did you do to get a compatible bios?

---

### Post by sisyphus1978 on 2012-11-08
I'm running an AO753 and getting the same error message with acerhdf. I *was* running an acer 1810TZ previously which worked fine. Any ideas on how to get it working on the 753? Thanks.

---

