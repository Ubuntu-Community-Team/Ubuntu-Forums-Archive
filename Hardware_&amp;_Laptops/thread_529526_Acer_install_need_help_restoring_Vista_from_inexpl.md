---
title: "Acer install: need help restoring Vista from inexplicably large PQSERVICE partition"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by s.i.m.o.n.d on 2007-08-19
I bought an Aspire 5103WLMI in June, my first Vista machine. Turns out, I don't like Vista much... so it was finally the right moment to try a proper installation of Ubuntu. Unfortunately, whilst Ubuntu installed just fine, the partitioning process wiped the existing Vista Home Premium setup. And whilst I probably prefer Ubuntu so far, I paid for Vista and I want it back.

So here's where I am. If I boot into Ubuntu, and look at the hard drive's partitions, I see:
[LIST]
[*]**/dev/sda1 ntfs 59.97GB (PQSERVICE)**
[*]/dev/sda3 ext3 47.26GB
[*]/dev/sda2 extended 4.57GB (boot)
[LIST]
[*]/dev/sda6 linux-swap 2.06GB
[*]/dev/sda5 linux-swap 2.50GB
[/LIST]
[/LIST]

In other words, it looks Ubuntu has given me one *huge* PQSERVICE partition (the partition provided by Acer for crisis recovery). It looks like PQSERVICE should be about 6GB maximum.

*Can I access PQSERVICE?* Sort of. When the laptop boots, the grub boot menu gives me several Ubuntu options, and one 'Windows NT/2000/XP' option. (Note: not Vista!) If I choose the Windows option, I see 'starting Acer eRecovery Management Environment', followed by the XP boot screen. I then see the Acer screen, which offers me the options of 'Restore system to factory default' or 'Restore system from CD/DVD'.

I don't have any CD/DVDs, so I choose 'restore to factory default'. After entering a password and OK'ing a warning message, I see a progress screen *very* briefly: just quick enough to see it identify a 'source' of D0E0-something; and a destination of /HardDisk0/Partition2. Then it tells me: 'Restore failed - reason 0xd0000017. Click OK to restart computer.' So eRecovery is clearly working OK within itself, but can't do the actual recovery.

**My guess is: it's looking for a suitable partition in which to reinstall the 'C drive', and can't find one. I'm hoping that, if I go into Ubuntu and reduce PQSERVICE down to a few GB (not sure how many?), and I create a new NTFS partition, then the eRecovery process will see the new partition, and will reinstall Vista into it.**

Does anyone have any experience of this? And if not... can anyone advise me on how to repartition the hard drive to let eRecovery do its thing?

I'd like to end up with a reasonably-sized C drive for Vista apps; a similarly sized partition for the Ubuntu OS and apps; and a large partition for OS-neutral files like OpenOffice docs or MP3s. FYI, I'm quite happy to wipe the existing Ubuntu installation as part of the process; I haven't done anything to it which I can't re-do very quickly.

---

### Post by ozgurcakmak on 2007-08-20
Great... my laptop did that and broke my heart too. Problem is those boot-to-life images don't have any partitioner on board. So you have to manually define a C: partition and set it to active - maybe it will work that way. 

My story however ended with me returning the laptop to its service. I didn't paid any cash for it was still in its warranty. And I think they changed whole Hard disk.

A word for those who read and thinking to buy a laptop, avoid this preloaded scheme like plague. It'll come out and bite you in the *** in the end. Try to get a real copy of OS install cd - you are paying for that when you are buying your laptop. If sellers don't want to give you one; then don't buy it or don't buy from there.

---

