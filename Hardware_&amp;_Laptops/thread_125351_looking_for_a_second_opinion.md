---
title: "looking for a second opinion"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by sal on 2006-02-03
I'm recently having a lot of crashes and application lock ups and system lockups and i think (well i'm sure) it's the ram, but i'm looking to see what someone els might think. here is a recent entry from the syslog.0
{ Feb  3 05:11:51 localhost kdm_greet[7004]: Internal error: memory corruption detected }

i am sure its bad ram what do you guys think?
thanks.

---

### Post by BenTyreman on 2006-02-03
Reboot the computer. There should be an option in GRUB for running metest86. This should confirm/rule out the RAM.

If that fails, there is definitely memtest86 on the installation CD.

---

### Post by Horndog on 2006-02-03
All you have to do to check your ram is start your computer and at the grub screen enter and choose memtest86 and let it run for at least 1 full cycle or longer. If there are error you have a ram problem.

---

### Post by gooner on 2006-02-03
Slightly unrelated but i've had ubuntu 5.10 installed (whole hard drive) for a while now and i have never noticed anything in GRUB that allows you to boot in any other way. I'm guessing this is because there are no other partions to boot so the loader quickly skips past everything. so my question is how would i go about running this metest86?

---

### Post by BenTyreman on 2006-02-03
It's definitely installed by default in the automagic section, so if you remove it, it will automatically be re-entered when you install a new kernel.

Hidden menu is enabled by default. Try pressing escape as the system boots up.

---

### Post by Horndog on 2006-02-03
Just go to [this]("http://www.memtest86.com/") site and download the ISO and burn an image to a CD (that way you are platform independent). Boot the computer with the cdrom as first boot device and let the test run.

---

