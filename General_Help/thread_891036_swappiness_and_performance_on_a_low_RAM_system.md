---
title: "swappiness and performance on a low RAM system?"
date: 2008-08-15
forum: General Help
---

### Post by teddmeister2 on 2008-08-15
I'm wondering if people out their will agree with me on this one: on a system at the low end of the system requirements for ubuntu (256 MB/RAM), will increasing the swappiness give a performance boost?  My reasoning goes something like this: Most of the slow down results from memory filling up and being forced to swap out inactive pieces to free up memory, right?  So if I increase the swappiness, the computer will have to do this less often overall, since it seems as though it would probably free up more memory by swapping out more than it would otherwise, right? Or am i completely missing something?

P.S., what's the default swappiness for hardy?

---

### Post by DagMan on 2008-08-15
You can look at your current swappiness value
```
cat /proc/sys/vm/swappiness
```
however I don't know if there is a default or if it is adjusted on the fly as it can be.  Mine is at 60 and I don't even have a swap partition. I should set it to 0 now that I've looked.  I think it was 40 on previous releases of Ubuntu.

As for the rest of the question, I'm just speculating, but the behaviour I had a while ago when I only had that much ram on a machine is that memory filled up with active programs as soon as I had a terminal and firefox open, and I'm guessing it was better to have things that I was currently running in ram than on the hard drive.  You can play with your swappiness value by changing it on the fly like this
sudo su root -c "echo NUMBER > /proc/sys/vm/swappiness"
where NUMBER is what you want to set it to.
It's trial and error after that.  Just don't set it to 0 with the small amount of ram you have or it will freeze.  I wouldn't go below 10, which will probably slow the system way down after some use anyway.

---

### Post by kerry_s on 2008-08-15
> **teddmeister2 said:**
> I'm wondering if people out their will agree with me on this one: on a system at the low end of the system requirements for ubuntu (256 MB/RAM), will increasing the swappiness give a performance boost?  My reasoning goes something like this: Most of the slow down results from memory filling up and being forced to swap out inactive pieces to free up memory, right?  So if I increase the swappiness, the computer will have to do this less often overall, since it seems as though it would probably free up more memory by swapping out more than it would otherwise, right? Or am i completely missing something?

P.S., what's the default swappiness for hardy?


i run on 256mb ram and i leave the swappiness at it's default, which is what works best, i tune else where, the thing i've learned about swap is it works best when you don't mess with it. for example that's say you lower swappiness to the usual 10, which keeps more programs in ram and uses swap less, all of a sudden you use a big program, say open office for example, so now it starts swapping to make room, so get you the slow down while it does it's thing.
now flip, that's say we increase swappiness to say 100, now you get these little pockets of wait time cause it's retrieving from the swap on the hard drive which is slower than ram, because you've asked it to put as much there as it can.

the best way to get performance is to fine tune the setup, for example turning on reduced resources in metacity, changing the programs to lighter alternatives, example swap gedit for leafpad, use simple themes, turn off any animations, don't use truetype fonts, use bitmap fonts(times, helvetica, courier), turn off smoothing and hinting, etc...

there's more you can tweak on the ui end that will give you faster, better results than trying to tweak how the hardware is used.

just my 2 cents, hope that's understandable i'm kind of tired. :lolflag:

---

### Post by oldos2er on 2008-08-15
> **teddmeister2 said:**
> I'm wondering if people out their will agree with me on this one: on a system at the low end of the system requirements for ubuntu (256 MB/RAM), will increasing the swappiness give a performance boost?  
P.S., what's the default swappiness for hardy?

 The only thing that will give a performance boost is to increase actual RAM.

 I think the default swappiness is 60.

---

### Post by donwait on 2009-04-23
hmm good post

---

### Post by kerry_s on 2009-04-23
i've actually changed since then. i use this now:

```
vm.overcommit_memory = 1
vm.overcommit_ratio = 95
vm.dirty_ratio = 5
vm.swappiness = 1

```

now i hardly use swap at all unless i open a huge *.doc or *.ppt, which are few and far between.

---

### Post by Francewhoa on 2009-08-03
Swap recommendations & FAQ aimed at Linux novices at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by msat on 2010-11-22
> **kerry_s said:**
> i run on 256mb ram and i leave the swappiness at it's default, which is what works best, i tune else where, the thing i've learned about swap is it works best when you don't mess with it. for example that's say you lower swappiness to the usual 10, which keeps more programs in ram and uses swap less, all of a sudden you use a big program, say open office for example, so now it starts swapping to make room, so get you the slow down while it does it's thing.
now flip, that's say we increase swappiness to say 100, now you get these little pockets of wait time cause it's retrieving from the swap on the hard drive which is slower than ram, because you've asked it to put as much there as it can.

the best way to get performance is to fine tune the setup, for example turning on reduced resources in metacity, changing the programs to lighter alternatives, example swap gedit for leafpad, use simple themes, turn off any animations, don't use truetype fonts, use bitmap fonts(times, helvetica, courier), turn off smoothing and hinting, etc...

there's more you can tweak on the ui end that will give you faster, better results than trying to tweak how the hardware is used.

just my 2 cents, hope that's understandable i'm kind of tired. :lolflag:


Interesting.  I run Ubuntu 10.x on a netbook with SSD hard drive.  With swappiness set to normal, the system was just crawling.  I reduced swappiness to 10 and the system runs well.  

I did try Windows XP on the system, but it was unusable.

The issue with this particular Atom/SSD based netbook is write speed.  It has 1GB RAM and fast read speeds.

--Mark

[http://www.marksatterfield.com](http://www.marksatterfield.com)

---

### Post by dmcdow on 2011-01-17
> **Onopoc said:**
> Swap recommendations & FAQ aimed at Linux novices at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Thanks Onopoc for your suggestion... very informative.

---

### Post by ceref on 2011-01-17
> **teddmeister2 said:**
> I'm wondering if people out their will agree with me on this one: on a system at the low end of the system requirements for ubuntu (256 MB/RAM), will increasing the swappiness give a performance boost?  My reasoning goes something like this: Most of the slow down results from memory filling up and being forced to swap out inactive pieces to free up memory, right?  So if I increase the swappiness, the computer will have to do this less often overall, since it seems as though it would probably free up more memory by swapping out more than it would otherwise, right? Or am i completely missing something?

P.S., what's the default swappiness for hardy?
I have an old and low 256 laptop which I stopped using when I blindly used Windows. I "booted out" Windows and installed Ubuntu 10.04 Lts (sanity at last). My machine eventually began to get slower but still a great OS until I down loaded 10.10 .... it nearly killed off my machine. 

I tried all the cleaners but no change I took all my files off and little used progs. Still lots of grey screens and near freezing all the time. 

SOLUTION for me came from the repository by the name of BLEACH BITS. I had heard it was harsh likes its name however it is programmable in what it does. I got it clear the usual stuff and all the caches including system cache all the logs and lists. I included "rotated logs" which are logs of older versions and upgrades.

I have reduced RAM demand by 30% and gained 2.3 MB of disc space.  That was a few days ago and my old machine is fast, bright and great as it once was. I am keeping Bleached Bits on and will use the config on a regular basis. 

Hope this helps you as it has done for me.

---

### Post by lithopsian on 2011-01-17
Default swappiness is currently 60 for Ubuntu 10.10 and for any versions that people are still likely to be using.  It has been different in the past.

The current setting is shown in /proc/sys/vm/swappiness and you can edit it as a file to change the value for your current session.  At reboot it is reset from the value in /etc/sysctl.conf, or potentially from files in /etc/sysctl.d.

60 is actually fairly aggressive about swapping out unused pages.  Whether this leads to "better" performance depends entirely on whether what gets swapped out is needed by you or not.  The space gained by swapping out pages thought the be unused is then used for maintaining more disk cache.

The disk cache can be useful for improving the responsiveness of your system.  Or it may be useless if you do something that fills the disk cache with pages you'll never need again.  The application pages swapped out are also a free gain if you never need them again, but if you do need them then your application will slow to a crawl.  So there is a balance and swappiness 60 is found to be that balance for most people in most cases.

Consider setting up compcache/ramzswap so that your system will behave a little more gracefully as useful pages start to be swapped out.   Swap pages equal to 25% of your RAM size (configurable) will be compressed and stored in (about 10%) of you RAM.  You will obviously have a few more swapped pages as they take some RAM, but reading them will be almost unnoticeable because they aren't on disk.  If nothing else, rzscontrol then lets you see how many of those swapped pages are then read again.  If this number is very low then perhaps a higher swappiness would work for you.  If the number of read swap pages is more than a fraction of the number of written swap pages then you would seem to be swapping out too many useful pages and perhaps should try lowering your swappiness.

More RAM is always a gain.  Remember that Linux will always use all your RAM after a time.  Some utilities will report that you have no free memory, but don't worry about it.  Others will subtract the disk cache, since it is quickly discarded if an application needs new memory, and those utilities may report a lot of free memory at the same time as showing swap usage.  These things are normal.

---

### Post by indigocat on 2012-01-23
On my Asus netbook with 2Gb of ram, I actually **INCREASED** vm.swappiness to **70**. Running Chrome, webapps & java software works much smoother now.
I previously tried setting vm.swappiness to 10, as suggested in pretty much every forum on the internet, but truth is, while it works well for 10 minutes, once Linux has to write back, the hard drive activity is so intense, it actually slows the system down, even to a halt in some cases. Flash performance was actually poorer with vm.swappiness set to 10 (contradicting the hypothesis that all should be dealt with in RAM).

In a nutshell: vm.swappiness=70 improved netbook performance, writebacks are done a bit more frequently but in much shorter bursts, so hard drive activity is, in average, less frequent, which has improved battery performance by a bit (I get about 20 extra minutes).

Haven't done any benchmarks yet, as I don't have much time, but I clocked the bang-for-charge, and 70 did a better job at both overall system performance & battery life.

Your mileage may vary, but stats & figures are welcome :popcorn:

(I'm on Ubuntu 11.10 Oneiric amd64, btw)

---

### Post by oldos2er on 2012-01-23
Closed. A better place to post your insights would be Testimonials & Experiences.

---

