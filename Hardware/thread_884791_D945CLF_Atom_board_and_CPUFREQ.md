---
title: "D945CLF Atom board and CPUFREQ"
date: 2008-08-09
forum: Hardware
---

### Post by maartsen on 2008-08-09
Hi all,

Does anybody have a working setup with the Atom chip and CPUFREQ? The problem is I cannot load any modules that are normally used to startup the cpufreqd or powernowd.

If you've got a working setup then I very interested in the kernel version, cpufreqd/powernowd version and the modules that you have loaded.

Thanks in advance,
Michel

---

### Post by anontrol on 2008-08-10
I've been working with an Intel D945GCLF board trying to get a general feeling for how well Ubuntu works with it.  I'm running 2GB of RAM and 32GB transcend SSD with an Aterhos based PCI wireless card (not using the wireless for general network access).

My initial assesment was that Ubuntu + firefox = unusable.  I would get grey "I'm busy go away" screens that seemed to be associated with disk writes.  I went through the standard disk activity minimization tweeks with no improvment.  In addition the wireless card was not recognized.  I moved to Opera to continue my assesment, but still ran in to frequent grey screens because of disk activity.

On a whim, I decided to upgrade the BIOS (looks like Intel has gotten smart and is distributing their BIOS upgrade as bootable .iso images... nice).  Anyway, that help a little (boot up was faster and certain types of disk access no longer produce grey screens) and my wireless hardware was finally recognized; however, I still get occassional grey screens every couple of minutes when there seems to be a huge block of disk activity (file system journaling?).  Firefox is still pretty much unusable.

My recomendation would be to first upgrade the BIOS, then try some disk access tweeks:  [http://www.kaobear.com/2008/07/30/reduce-disk-activity-in-ubuntu/](http://www.kaobear.com/2008/07/30/reduce-disk-activity-in-ubuntu/) .  If that doesn't get the system usable, then I'd recomend looking at moving away from a journaling filesystem (but I haven't tried that yet as my system is now relatively usable under Opera).

You'd think Intel/Ubuntu would get more involved, but it's obvious that they're not particularly serious about making sure their lower end stuff is super usable.  In 12 to 18 months, these Atom based systems are going to be everywhere...

---

### Post by maartsen on 2008-08-11
Hi anontrol,

Sorry I don't have got your problems with the board. Only the network card and CPUFreq don't seam to work. Although I use the PC as a small server. So I don't have any experience with the X configuration.

But if you do an "[FONT="Courier New"]sudo lsmod | grep cpufreq[/FONT]" is there an acpi-cpufreq loaded?

Best regards,
Michel

---

