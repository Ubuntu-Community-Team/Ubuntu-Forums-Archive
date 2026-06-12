---
title: "installing ubuntu on acer aspire5330"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by monkeybritt on 2009-03-05
i am trying very hard to get hardy on my newer laptop and for some reason cant figure it out other acer types have not been helpful.
i cant boot into live mode only busybox safe mode doesnt really work i was able to get installed through alternate but was uable to run it because any program  that required video or audio to be played crashed the session. i have tried 7.10 same issues although i did have better luck with the install i was going to do the upgrade method to get to hardy. but couldn't get things to work.please someone help.

---

### Post by martrn on 2009-03-05
The Acer Aspire 5330 has very different makes and models.  There is an intel graphics chipset model, and ATI graphics model and an NVidia graphics model. I do therefore not know any specs to your laptop.

The Alternate is the best way to install ubuntu linux on any hardware where they might be a difficulty.

Whithout an error message, I cant' say much else other than don't give up trying.

---

### Post by monkeybritt on 2009-03-05
i believe it is the intel grapghics as there is no graphics card it is the integrated type. intel celeron 2 ghz 2 gig ram and a hitachi hdd it has wifi which was the issue with 7.10 i really dant want anything newer becasue of the avi playback issues in intrepid i had this same issue with hardy on my hp desktop until the .2 updated version was released. initramfs puts out errors about ata stuff not being found thats as far as it will go i could do the alternate install if someone knows how to fix the graphics issue after the install.

---

### Post by martrn on 2009-03-05
To install the Intel graphics drivers on an already installed recent version of ubuntu, I think you can :
```
sudo apt-get install xserver-xorg-video-intel
```

The failure or success of this is unknown to me, as I do not have an Intel Graphics Media Accelerator.  I find Nvidias better if having to install binary drivers.

There have been problems/issues with Intels graphics drivers in the past:

[Here]("http://www.ubuntuforums.org/showthread.php?t=209996"), [Here]("http://www.ubuntuforums.org/showthread.php?t=244628"), [Here]("http://www.ubuntuforums.org/showthread.php?t=189086"), 
and [Here]("http://ubuntuforums.org/showthread.php?t=239389") !

If you visit the Manafacture of the chipset you can see, it appears to work.. [intellinuxgraphics.org]("http://intellinuxgraphics.org/") and [Intel G FAQ]("http://support.intel.com/design/intarch/swsup/graphics_faq.htm?iid=ipp_rhc+graphics_faq"), although how you would ensure the graphics driver stayed working while correcting the kernel modules/drivers I wouldn't know.  You would be immediately plunged in the dark if there was any problem.

You are always going to have such problem on a integrated chipset no matter what version of ubuntu, but you are not going to know what problem you may have until you try upgrading.

The first versions of Ubuntu 8.04 (LTS) had timing issues with some chipsets, but there have been three upgrades of the ubuntu 8.04 kernel since is release, so sholdn't be so much of an issue.

Saying 'about ata stuff not being found' could be a timing issue, but could also be something else, its not so descriptive.  Saying 'couldn't get things to work' isn't so descriptive either.

Ubuntu Linux 8.04 is supposed to be a long term service edition and should be more stable. 

If video or audio being played is crashing the session, you should have some files at /var/log particularly of the xorg/Xorg.0.log/dmesg type logs that should provide some clue as to why the session crashed. 

Check there and check your BIOS for settings related to the onboard graphics card to see if you can change anything there.

---

### Post by monkeybritt on 2009-03-05
ok then i will try to be more descriptive. i dont really understand why ubuntu should require a higher end graphics card when windows doesnt. dont take me wrong i love ubuntu i have run it on my desktop for awhile now and see the advantages the desktop has integrated also. i didnt realize i needed a quad core with ati raedon and a million gigs of ram to run it. sorry for being a smart *** but this shouldnt be an issue for a linux distro. i thought the point of linux was to have a kernel and os that just worked and functioned with less resources. how can anyone say that is true when i can install xp and vista on any machine as long as i know where to find drivers, and there is always  a proper driver to use. this has me very angry as i hate windows. i hate that the world is addicted to it like crack. 
i have tried xubuntu and get the same issues.
here are my errors that initramfs puts out...

[  72.630852]  ata2.00 : revalidation failed (errno= -5)
[  72.637414]  ata2: COMRESET failed (errno= -16)
[  72.665274]  ata2: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[  72.665309]  ata2: irq-stat 0x40000008

oh and by the by what is with the attitudes people have in these forums. its like we are all trying to size up each others computer knowledge *!@#$ i dont get it we are here to help each other not make ourselves feel  superior to those in need. if you know one person that has run ubuntu on every architecture out there and i will put my foot in my mouth gladly. again it has been a long week. i appologize.

---

### Post by monkeybritt on 2009-03-05
ok and like a dumb i just now decide to check dev. manager and found my chipset to be mobile intel 4 which i can seem to find any support for in the linux driver list on intel site. hmmmmm.

---

### Post by monkeybritt on 2009-03-05
ok did more reasearch and have come to the horrible realization that this laptop will just not work. broadcom wireless. no nvidia blah blah blah. maybe just maybe the next lts will have support for these bare bones dirt cheap machines. i guess saving a few wasnt a great idea. oh well i will just patiently wait until some distro supports it. this sucks. well one day when i am out of school i might be able to afford a comp expensive enough to put a free linux distro on properly.:(

---

### Post by martrn on 2009-03-05
> **monkeybritt said:**
> ok then i will try to be more descriptive. i dont really understand why ubuntu should require a higher end graphics card when windows doesnt. dont take me wrong i love ubuntu i have run it on my desktop for awhile now and see the advantages the desktop has integrated also. i didnt realize i needed a quad core with ati raedon and a million gigs of ram to run it. sorry for being a smart *** but this shouldnt be an issue for a linux distro. i thought the point of linux was to have a kernel and os that just worked and functioned with less resources. how can anyone say that is true when i can install xp and vista on any machine as long as i know where to find drivers, and there is always  a proper driver to use. this has me very angry as i hate windows. i hate that the world is addicted to it like crack. 
i have tried xubuntu and get the same issues.
here are my errors that initramfs puts out...

[  72.630852]  ata2.00 : revalidation failed (errno= -5)
[  72.637414]  ata2: COMRESET failed (errno= -16)
[  72.665274]  ata2: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[  72.665309]  ata2: irq-stat 0x40000008

oh and by the by what is with the attitudes people have in these forums. its like we are all trying to size up each others computer knowledge *!@#$ i dont get it we are here to help each other not make ourselves feel  superior to those in need. if you know one person that has run ubuntu on every architecture out there and i will put my foot in my mouth gladly. again it has been a long week. i appologize.

There is a bug in launchpad describing this kernel error. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202938]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202938").  Changing to  xubuntu isn't going to help as its ATA (chipset) issue, where ubuntu cycles endlessly with ata messages.

Sometimes changing the settings in your BIOS will help, thats like causing your chip-set to 'behave differently'.  Different kernels work well differently changing to a different kernel may help, depending on which version of ubuntu you are running.

Integrated graphics cards do cause a problem, and its not about the expense or cost of your hardware.  Integrated graphics cards expect some of the memory installed normaly for your computers use to be used by the graphics card.  At first outset this looks ok, most modern processors should be able to cope with the extra overhead.  However with the linux kernel at first it will see that the kernel will have xxMB/xxGB of memory available to it.  At a later stage it should take note that some of this memory is not the memory it is able to use, because part of that memory will be required for use by the graphics card or the graphics chipset.  

Its surprising (to me). this feat of engineering works at all, even on a windows system.  Some chip set manufactures have errata sprawl over a few pages long, which doesn't matter because it can be fixed to work with windows.  If it works with windows it is theoretical that it should or can work with linux.  But how is hard for me to find out, I simply do not know.

Linux in the past has worked better on older hardware (because device drivers have been written for it), than on newer machines.  Its not about affording a workstation expensive enough.

Sorry I couldn't help further.

---

### Post by monkeybritt on 2009-03-06
ok with some persistance i was able to fix this i just installed 7.10 and then upgraded and for some reason it did everything flawlessly even the video issues are fixed.

---

