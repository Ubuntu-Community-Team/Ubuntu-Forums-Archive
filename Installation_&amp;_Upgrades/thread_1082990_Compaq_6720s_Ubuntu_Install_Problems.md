---
title: "Compaq 6720s Ubuntu Install Problems"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by mykz- on 2009-02-28
Hey All

I’m new to ubuntu and I’m trying to install version 8.10 on my Compaq 6720s

My machine boots from disk I press enter for languages and then select install Ubuntu then Ubuntu tries to perform the install and sits on the minus (-) sign for about 2 seconds then the screen flickers green and I get a black screen.

I've tried the alternative disk and still the same problem.

I’ve also Googled loads and have tried what people have suggested but still the same problem Ubuntu won’t install.

Thanks for any help in advance.

---

### Post by Kevbert on 2009-02-28
Welcome to Ubuntu.
How much memory does your Compaq have ? I believe the display uses shared memory.
Have you burnt the CD yourself ?  Hash checked the downloaded ISO file ? Run the CD check from the boot menu ? Run memtest from the boot menu (Windows will still work with dodgy memory, but may crash occasionally) ?

---

### Post by mykz- on 2009-02-28
Hey Kevbert

thanks for getting back to me.

The laptop hold 1 Gig Ram

I can't check the cd for errors because when i do that it does the same as the install just black screens.
i've also run a memtest.

i have tryed acpi=off from boot options someone told me to try it but still have the same problem.

---

### Post by Kevbert on 2009-02-28
At what speed did you burn the CD ? (x2 best for minimal errors). Regarding boot options you may want to take a look at [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/BootOptions"). The option you want is pci=noacpi.
Another thing you may want to take a look at is [[COLOR="Red"]this[/COLOR]]("http://marcin.af.gliwice.pl/if-then-else-20071022085850") article as it suggests you need to use the Alternate CD.

---

### Post by khelben1979 on 2009-02-28
Try [Debian]("http://en.wikipedia.org/wiki/Debian") instead? :popcorn:

---

### Post by mykz- on 2009-02-28
Hey Kevbert

I burnt at the lowest i could x2.

i've also tried pci=noacpi and it got past where it failed last and then died again i did try it again and it failed where it normaly fails.

i am using the Alternate CD to install i have tried both.

Any more ideas?

---

### Post by Kevbert on 2009-03-01
Try vga=771 along with pci=noacpi at the same time. I'm just wondering whether you're leaving the boot long enough as the CD puts all programs into memory prior to installation and that can take a few minutes.
I doubt that Debian would resolve the problem as Ubuntu is based on Debian linux.
What OS have (had) you on the PC prior to attempting to install Ubuntu ?
Take a look at [COLOR="Red"][this]("http://ubuntuforums.org/showthread.php?t=781966")[/COLOR] and [[COLOR="Red"]this[/COLOR]]("https://wiki.ubuntu.com/LaptopTestingTeam/HPCompaq6720s"). It looks like Hardy Heron 8.04 may be a better option. The CD drive might be a problem (see below) and take a look at [COLOR="Red"][this]("https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD")[/COLOR].

---

### Post by codejammer on 2009-03-01
I had simillar probelms trying to install a HP Omnibook.  I came to the conclusion that it was because the CD drive could not read the recordable CD.  There is a provision to check the install CD.  On my newer Dell it ran without errors however on the Omnibook it reported that the packages were corrupted.  I was considering using a USB stick to perform the installation instead.

---

### Post by mykz- on 2009-03-01
Thanks Kevbert

i'll try vga=771 now with pci=noacpi

The laptop currently runs windows xp when installing win xp i had to create a custom windows xp disk as the default windows xp disk didn't have my HD drivers

I have tried Hardy Heron 8.04 but not with the boot options.

I'll also try the other methods you have provided.

I have also tried an install with pen stick and still ran into the same problems.

---

### Post by Kevbert on 2009-03-01
Assuming you still have XP you may need to temporarily remove the paging file (which is used to speed up XP, similar to linux swap). This is likely to be at the end of the partition. But this isn't part of your problem (but could be another problem if you decide to dual boot).
When you performed a memtest did you run it for at least two passes ?
I haven't found anything else regarding install problems of Ubuntu on Compaq 6720s PCs.

---

### Post by mykz- on 2009-03-01
Hey Kevbert

The vga=771 and pci=noacpi has done the trick Ubuntu 8.10 is now install.

Install went really well with no problems.

Big Thanks kevbert for all your help.

---

### Post by Kevbert on 2009-03-01
No problem. If you get any problems feel free to ask on the forums as everyone likes to help.

---

### Post by 1999 on 2010-05-16
it seems like this trick does not work on Ubuntu Lucid
after adding this options (pci=noacpi vga=771) to the end of the line, something starts but after 2 seconds a get this screen with a brown stripe in the upper part of the screen:
[http://img189.imageshack.us/img189/5967/dsc09730l.jpg](http://img189.imageshack.us/img189/5967/dsc09730l.jpg)

btw - i added these options after everything, that was in this string, so it became smth like this:
menu=..... xxx=.... quiet -- pci=noacpi vga=771
is this right?

---

### Post by 1999 on 2010-05-16
seems like i chose the wrong franebuffer. "vga=773" option helped me
btw - still the installation from alternate CD didn't find cdrom-drivers :(

---

### Post by frenkx on 2010-08-29
Neither one of the mentioned options worked for me. What finally did the trick and let me finish installing ubuntu lucid lynx 10.04 from the alternate 10.04.1 cd was to attach an external CRT monitor, start the installation and switch the monitor via <fn>-<F4>. Pushing <fn>-<f4> trice would let me finish the installation on the built in LCD without an attached CRT. It would not work without an attached monitor.

---

