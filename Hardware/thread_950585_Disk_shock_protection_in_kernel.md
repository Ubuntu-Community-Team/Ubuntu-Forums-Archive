---
title: "Disk shock protection in kernel?"
date: 2008-10-17
forum: Hardware
---

### Post by niknik on 2008-10-17
Hey guys,

I just found that Elias Oltmann's disk shock protection patches have made it into 2.6.28.(see [http://www.heise.de/open/Kernel-Log-Was-2-6-28-bringt-1-ATA-Unterstuetzung-und-Block-Layer--/news/meldung/117494](http://www.heise.de/open/Kernel-Log-Was-2-6-28-bringt-1-ATA-Unterstuetzung-und-Block-Layer--/news/meldung/117494))

Does anyone know when we can expect to see a kernel in Ubuntu that supports hdaps on IBM/Lenovo machines without patching?

Cheers,
Nik :)

---

### Post by sdjcwcba on 2008-11-07
Bump! :)

---

### Post by n0manarmy on 2008-11-08
I'm also interested in this. I've got a T400 and have been using it with 8.10 for a few weeks now. The only thing I miss from going to Vista to Ubuntu is the Lenovo utilities, especially the hard drive shock protection monitor. I'm constantly moving and shifting with my laptop.

EDIT:
with a little more googling with the respective acronyms I did find this reference and these packages available.
[https://blueprints.launchpad.net/ubuntu/+spec/hard-disk-shock-protection]("https://blueprints.launchpad.net/ubuntu/+spec/hard-disk-shock-protection")

And through Synaptic look for hdapsd

Double EDIT:

After installing and attempting to run on my Lenovo, it spits out an error

[I]WARNING: Cannot open hdaps position input file /dev/input/hdaps/accelerometer-event (No such file or directory). You may be using an incompatible version of the hdaps module, or missing the required udev rule. Falling back to reading the position from sysfs (uses more power). Use '-y' to silence this warning.
protect_file: /sys/block/sda1/queue/protect
threshold: 15
read_method: poll-sysfs
open(protect_file): No such file or directory
[/I]

---

### Post by sdjcwcba on 2008-11-08
I had hard drive protection working on 8.04 thanks to:

[http://suchaxplore.blogspot.com/2008/08/active-protection-system-in-ubuntu-8041.html]("http://suchaxplore.blogspot.com/2008/08/active-protection-system-in-ubuntu-8041.html")

But 8.10 uses 2.6.27, and so a new patch is needed. They have instructions for 2.6.27.2 here:

[http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS]("http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS")

But I think Ubuntu uses 2.6.27.4 (if that makes a difference?)

Instead of constantly applying patches (which often turn up with errors) - I was hoping 2.6.28 would be released soon - which supposedly has it already. Anyways, if you are willing to use 8.04, the above link should hopefully help.

---

