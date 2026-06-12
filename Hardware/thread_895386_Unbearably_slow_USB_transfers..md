---
title: "Unbearably slow USB transfers."
date: 2008-08-20
forum: Hardware
---

### Post by detroit/zero on 2008-08-20
As discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=793688"), I've been having a problem with transferring files *to* USB devices. The problem is only in the write cycle, and copying files *from* a USB device works as it always has.

There's a temporary solution discussed for a kernel boot option that is supposed to help, but it got me out of the 300-800**K**b/s range and into the 1 or 2**M**b/s range, which yes, it's faster than it was, but still unbearably slow. Before this started happening around a month or so ago, I was used to speeds approaching 30Mb/s. Now, moving a 1GB .avi file to a USB external hard disk takes upwards of twenty minutes, where it used to take under two.

The problem has been tracked to gvfs, and has a bugtracker entry, but I can't see where anything's getting done with it until Ibex comes out.

I've noticed that when running off the 8.04 live CD (my new preferred method of file transfers), the problem is far less pronounced. I average speeds of 18 to 24 Mb/s in the live session. Whe I boot into my Vista partition, transfers work as fast as expected.

I've tried to insert the Hardy CD (an official, in-the-mail version from Canonical, not one I burned) and adjust my software sources to grab packages from the CD (i.e., deselecting every source except the CD), it doesn't allow me to re-install gvfs from the version on the CD.

Is there any way for me to "devolve" or un-upgrade this package back to a version that worked properly? Am I trying to install from the CD wrong? Can I use subversion? How can I roll this version back to one that worked?

This problem also effects network transfers and it's killing me to have to wait for hours to move a couple GB worth of files around. I used to use USB memory to bypass wait times for slow network transfers, but that's no longer an option.

Someone? Anyone?

---

### Post by kbrill on 2008-08-20
I added pci=routeirq to the grub boot options and I got my USB and network performance back

Dosn't work for everyone though

Also found help [here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=754659&page=3")

---

### Post by detroit/zero on 2008-08-20
> **kbrill said:**
> I added pci=routeirq to the grub boot options and I got my USB and network performance back

Dosn't work for everyone though

Yeah, I tried that a couple weeks ago, and it does help a little but it's not much.

---

### Post by detroit/zero on 2008-08-21
> **detroit/zero said:**
> Is there any way for me to "devolve" or un-upgrade this package back to a version that worked properly? Am I trying to install from the CD wrong? Can I use subversion? How can I roll this version back to one that worked?

Someone? Anyone?

Bump.

---

### Post by detroit/zero on 2008-08-22
> **detroit/zero said:**
> Is there any way for me to "devolve" or un-upgrade this package back to a version that worked properly? Am I trying to install from the CD wrong? Can I use subversion? How can I roll this version back to one that worked?

Someone? Anyone?

Bump again.

Come on... nobody can tell me how to re-install the gvfs package from the Hardy cd?

Check out this screen shot. I'm dying here, guys!

---

### Post by detroit/zero on 2008-08-23
Bump.

---

### Post by detroit/zero on 2008-08-24
> **detroit/zero said:**
> Is there any way for me to "devolve" or un-upgrade this package back to a version that worked properly? Am I trying to install from the CD wrong? Can I use subversion? How can I roll this version back to one that worked?

Someone? Anyone?
Bump.

---

### Post by pietjanjaap on 2008-08-24
I got the same problem here.(20Gb file in linux)
In windows i get sometime's that copien file just stops, this is the same pc with a large 20Gb file. So i think it's hardware.

On a newer pc in windows never have a problem.

Conclusion i do not know why.

---

### Post by detroit/zero on 2008-09-01
Please, oh please - somebody tell me how to install the original gvfs package from the Hardy CD so I can have a decent file transfer speed back?

Please? 

Moving 6GB of videos to an external disk started out with a 6.2m/s speed and an ETA of 14 minutes. It's already been running 15 minutes and has an ETA of 21 minutes with a current speed of 2.1m/s.

Oh, and did I remember to say "Please"?

---

### Post by ThaRabbit on 2008-09-01
Well the archives are available here:
[http://packages.ubuntu.com/hardy/i386/gvfs-backends/download](http://packages.ubuntu.com/hardy/i386/gvfs-backends/download)

those offer the 2.3.0 versions that came with the stock cd, though I can't imagine what a workaround it must be to do this one manually...

Best bet might be to:
1. boot to terminal
2. use aptitude to remove gvfs (aptitude also removes the dependancies!! apt-get does not do this by default)
3. add the archive repository to your sources.lst as listed on the link
4. uncomment the normal repositories
5. sudo apt-get update
6. now use apt to install gvfs again

reboot and pray?

I'm just offering my unexperienced suggestion as you seem to be without any reply here, please consider my lack of experience with this specific problem.

*edit*

Simpler sollution:
1. uninstall gvfs using synaptic
2. remove the normal repositories in synaptic
3. add the archive repositories in synaptic
4. use synaptic to install the archive version of gvfs

the word backup comes to mind, as I expect this to break a few things. Might want to try this on a second installation before you attempt it on your main one.

---

### Post by nicedude on 2008-09-01
I just looked in synaptic and if he removes gvfs then it will remove Nautilus as well but you may be able to install the other version and still just reinstall nautilus and have it work. I would say you may need to reinstall nautilus from the CD too in case the newer version in the repositories requires the updated gvfs to work.

---

### Post by detroit/zero on 2008-09-01
Well, it doesn't work.

I mean, your method is sound - I was able to download and install the older version of gvfs and the older version of nautilus, but it doesn't have the desired effect.

I guess I'm screwed until the next Ubuntu comes out. I heard Ibex doesn't have this issue with USB file transfers.

---

### Post by detroit/zero on 2008-09-07
Possible explanation for slow transfers and definite fix here:_ [http://ubuntuforums.org/showthread.php?t=911052](http://ubuntuforums.org/showthread.php?t=911052)_

---

### Post by detroit/zero on 2008-10-19
Since the slow USB write problems aren't limited to Ubuntu, and seem to apply to various distros and kernel versions over the last few years, I started [a thread over at Linuxquestions.org]("http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/")
 
 Maybe the people who are having this problem can all get together and find a fix, rather than wait to see what trickles down from on high.
 
 Come over there and chime in with your experiences with the slow USB write speeds.

---

