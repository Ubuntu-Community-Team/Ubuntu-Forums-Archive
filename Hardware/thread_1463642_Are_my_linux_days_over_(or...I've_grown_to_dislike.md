---
title: "Are my linux days over? (or...I've grown to dislike Toshiba. Help)"
date: 2010-04-27
forum: Hardware
---

### Post by Musmanno on 2010-04-27
Toshiba Satellite A505 with i3 processor and Realtek 8191SE wireless.  No distributions have booted properly from the LiveCD except the new Ubuntu.  Wireless wasn't working from the LiveCD but I'll troubleshoot that later.

I install to hard drive and NOW I have boot problems. It hangs for a long time on the purple background with the light effects. When a box finally appears for login, and I try to log in, it tells me some power management feature is still running and assumes I want to log out.  When I hit "log out anyway" it actually logs me in.

The boot process takes so long I can't use it.

I've tried passing commands like acpi=noirq as well as acpi=off irqpoll, and to no avail.  I do this by pressing 'e' in GRUB, adding the commands and booting with CTRL-x.  Is that right?

Incidentally, I couldn't see how to pass commands when booting up with the LiveCD.  That's an important feature to be lacking in the LiveCD.  Maybe I just missed it.

Any thoughts?  I've tried half a dozen distros and this is the only one that booted correctly from the LiveCD.  Now that it is installed on the hard drive it doesn't work well.

Am I pretty much stuck with Windows 7?

BTW I am using the 64-bit version of the 10.04 RC.

---

### Post by Mark Phelps on 2010-04-27
Have you tried the new PCLinuxOS 2010? I've read a couple of recent reviews of it and they think very highly of it. Using that would prevent you from being "stuck" with Win7.

---

### Post by quinntar on 2010-04-27
Well, actually a friend of mine has got the same problem as you seem to have... as for me I had a similar problem on my i5 HP... booting in 32bits live cd was desastrously slow, but i had quite a success with the 64bits version...
If you have any success with PClinuxOS 2010 just let us know

Quinntar

---

### Post by Linuxforall on 2010-04-27
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

For i3 to work, you need the latest kernel, otherwise all these issues crop up with the older kernel.

---

### Post by Musmanno on 2010-04-27
I did try PCLinuxOS 2010 and was also having some boot up issues, though I didn't spend a lot of time troubleshooting because Ubuntu seemed to be working better.  I'll give that another shot and report back.

I also tried:

Linux Mint (one of my favs)
Crunchbang linux
Fedora
OpenSUSE
Sabayon
MacPup
SliTaz
Mepis

No dice.

Does the new version of Ubuntu not have that latest kernel?  If not, how can I update the kernel of my installed Ubuntu 10.04 RC to the latest version?

---

### Post by Yellow Pasque on 2010-04-27
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by dabl on 2010-04-27
Because Toshiba also designs hard drives and so controls the interfaces and the firmware, they can make an integrated system that is really very power-efficient (with Windows drivers) or really a pain (with Linux).  I have a NB205 netbook, and it runs KDE 4 on sidux like a champ.  But, when a CLI task is running, like updates, when there's no user interaction for a couple of minutes, the hard drive "falls asleep" -- the whole thing just stops, until I tickle the touchpad or hit the spacebar.  I'm going to replace the hdd with a SSD, which will put an end to that nonsense.

---

### Post by Musmanno on 2010-04-27
Well, even though the PCLinuxOS 2010 LiveCD didn't work well at all, I went ahead and installed it to my hard drive just to see. Oddly enough, it booted perfectly.

Only issues are it doesn't like my Intel GMA4500HD graphics card or my RealTek wireless.  But at least it boots right and takes me into the OS smoothly.  I'll troubleshoot the rest.  Thanks for the advice!

---

### Post by compiz addict on 2010-04-27
Did you already try Debian? it's similar to Ubuntu. (Ubuntu was made based on Debian)

---

### Post by pcrat on 2010-04-27
I have a Toshibla L305 works VERY well with ubuntu 10.04 no problems at all yet. except for the atheroes wireless, but im not worried about that right now...

---

### Post by OU_Guy on 2010-04-27
It may be too late, but did you try to install ubuntu from windows? That is what I would try if I were you...

You basically put the live cd in after you are already in windows and it pops up as a program.

---

### Post by eduosoarm on 2010-04-29
I have the same model A505 (toshiba for LatinAmerican/Mexico) and ubuntu beta2 installed ok, sound is fine and function keys ESC (sound) F3, F4,
but no wireless (no hurry for that the eth0 works!!) but the screen is so bright and F6/F7 does not work!!

please if you know an url where to fix this issue before i get blind or boot to win7.

BTW I upgraded to today release (apt-get upgrade) but no luck

Thanks in advance
Best REgards

---

