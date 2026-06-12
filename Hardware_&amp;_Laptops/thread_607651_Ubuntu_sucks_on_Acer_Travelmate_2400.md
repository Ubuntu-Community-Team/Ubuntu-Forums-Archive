---
title: "Ubuntu sucks on Acer Travelmate 2400"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by pbhat on 2007-11-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/161137](https://bugs.launchpad.net/bugs/161137) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am running Ubuntu 7.10/Kubuntu 7.10/suse 10.3 on Acer Travelmate 2400 with
Processor - Celeron1.5 GHz
RAM - 256 MB
Video - Intel 915GM
Wireless - broadcom 4000?(bcm44xx)
Modem - Intel Ich
 
I work in (K)ubuntu 7.10 on it,but it has suse 10.3 and Windows XP as
well.With  version everything works though  Modem,Wireless require a
firmware download. But this Laptop has an inherent problem with all
Linux distors.I can see the harddisk LED lit or flickering almost always
and programs load slow and general response of the whole OS is too too
slow.(I earlier had suse 10.2 on  it for six months,but quit that for
same problems)
 
An example is,if I have OOo2.3 and FF both running,switching between
them takes a tangibly long time.Switching between FF tabs is slow as
well.OOo takes about 1 1/2 min to load and the menu is not ready to be
clicked when it is open.Menu takes about 5 secs.Once it is activated,it
is active till some time.But if you are not using for sometime,again it
takes longer or that long anyway.Right clicking in filemanger to get
menu is also slow and takes 2-3 secs again.
 
I have tried Suse 10.3 & (K)Ubuntu on desktop PCs with Piii 800 MHz and
256 MB RAM.I run Fedora4 regualrly,and suse 10.1 occassionally on my
Home PC with Celeron 450 Mhz and 256 MB RAM,even there,linux response is
normal enough not to bother me,inspite of slower processors.I can feel a
great difference between the performance of all Linux distros I have
tried on this laptop and slower desktop computers with same amount of
RAM( better)
 
On the same machine,Windows XP is a beuuty to work in and OOo in WinXP
works almost as fast as MSOffice.The one distro which was smoother was
PCLinuxOS.
 
Anybody has clues as to what could be the problem?I have tried turning off apm on harddisk(suspecting excessive power management),booting with [apm=off acpi=off] without any visible effect.The questions I have are why most linux(all except PCLinuxOS) OSes have problem with this laptop whereas PCLinuxOS is much better?What is the setting that makes the difference?Where should I look for the problem?

---

### Post by kerry_s on 2007-11-09
the problem is 256ram and the memory hungry applications your trying to run. kde and gnome really need at least 512ram to run perfectly. with 256ram there's going to be alot of swapping, so yes there will be alot of disk activity. with that much ram you really need to go lighter, make sure you use the right vid driver.

---

### Post by pbhat on 2007-11-09
Thanks kerry_s,

I cannot disagree more. I have explained in the posting that I have tried suse10.3/Kubuntu on slower desktop machines(PIII) with just as much memory where they are more responsive,faster and disk activity is much less.Also,please keep in mind my observations about PCLinuxOS on the same laptop.

---

### Post by kerry_s on 2007-11-09
i have no idea of your perception of speed is, i use to get the exact same slowness on a acer 3500, then i moved that up to 512ram and it could run anything after that. now a days i build my setup from scratch on a debian base install, only installing what is needed.

you say pclinuxos runs the best, why don't you go with there light version for low resource setups.-> [http://junauza.blogspot.com/2007/11/tinyme-little-pclinuxos-that-could.html](http://junauza.blogspot.com/2007/11/tinyme-little-pclinuxos-that-could.html)

---

### Post by pbhat on 2007-11-10
Hi,

My sense of speed is responsiveness of OS.For the last four years I have worked only in Linux Desktop (various distros) in PCs of different configuration and I easily sense the difference.

In this case, I am comparing the performance of Ubuntu(suse also) on my laptop and on my desktops which are pIII and pII.They are more responsive in Piii and Pii with just 256MB RAM.I am sure increasing RAM is a quick solution,but only a bypass. Please read mu submission to bug-report.(partially quoted below)

"But as this occurs across distributions and one distribution is rather free from it,can this have something to do with BIOS/ACPI/APM or the harddisk itself?Is there a way to read bios info or firmaware info to figure out?I suspect some foulplay by Acer.Before this series,it used to load it's systems with Suse Linux,but this series comes with a chinese linux and the cd has drivers only for windows XP and in the advertisements there is a smallprint saying full specifications can be realised only in another right OS".

---

