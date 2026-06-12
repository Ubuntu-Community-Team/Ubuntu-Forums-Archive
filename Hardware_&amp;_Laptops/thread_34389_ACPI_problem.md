---
title: "ACPI problem"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by caecus on 2005-05-14
I have ubuntu runninng and up to date on my dell XPS gen2 laptop.  I went ahead and enabled ACPI suspend, however when i put my laptop in to suspend it wakes up to a black screen and I cant do anything but turn it off.  The same thing happens with suspend to disk also...

Is there something I might need to add to the resume script or am i missing something else obvious?

Thanks,
-Charles

---

### Post by caecus on 2005-05-20
Hate to reply to my own post, but can anyone point me in the right direction?

-Charles

---

### Post by Strife on 2005-05-20
Unfortunately, I too am having similar problems with my Inspiron 6000. I read in some post that having vga=normal at boot solves the issue, but I haven't tried it yet because when I installed, I had to have vga=771 or else I had screen problems.

I am planning on trying it out soon, though.

---

### Post by caecus on 2005-05-21
ah, well its always reassuring to hear your not alone...

I'll look into that and try it as well.

---

### Post by Strife on 2005-05-26
Still no solutions to this problem?

I've been doing quite a bit of Googling, and I still have yet to find any suggestions that have done anything.

---

### Post by Skyes on 2005-05-27
[QUOTE=caecus]I have ubuntu runninng and up to date on my dell XPS gen2 laptop.  I went ahead and enabled ACPI suspend, however when i put my laptop in to suspend it wakes up to a black screen and I cant do anything but turn it off.  The same thing happens with suspend to disk also...

Is there something I might need to add to the resume script or am i missing something else obvious?

Thanks,
-Charles[/QUOTE]
 Hi caecus,

I had the same symptoms on my HP nx7010 Laptop. Now suspend and suspend-to-disk works. I changed my graphics card driver back form fglrx(?) to ati which solved the problem. However, my USB-Mouse needs a "/hotplug restart".
Give it a try if you have an ati-card, too.

---

### Post by hod139 on 2005-07-27
It has been a while since anyone has posted to this thread, but I am also having this same problem on a Dell Inspiron 6000 with a pci express ATI RADEON x300 128MB video card.  I am also using the fglrx driver.

I couldn't find much on the subject, but I did find [this link](http://http://lkml.org/lkml/2005/6/6/121)  on the linux kernel mailing list of someone with the same problem and he was asking the question "Is this a kernel issue or an X issue."

Another annoyance with the acpi scripts is that for some reason /dev/hda is hard coded, where on my laptop it is /dev/sda.

Will any of these issues be fixed in breezy and is there anything I can do now?

---

### Post by c0rderr0y on 2005-08-23
i am in the same boat as hod139.... would be great if i could put my lappy to suspend or sleep

---

### Post by tarball on 2005-09-29
I have noticed that when my machine returns from sleep (IIRC both hibernation and suspend) it doesn't automatically switch to the correct VT and I have to press **<ALT>**+**<CTRL>**+**<F7>** to get back to X.

---

### Post by grinchy on 2005-09-29
If that doesn't work try pressing <CTRL>+D

---

### Post by Arkainium on 2005-09-29
If you're using the fglrx driver, waking from suspend won't work.  It's a known issue for a while now.  [See ATI release notes.]("http://www2.ati.com/drivers/linux/linux_8.16.20.html#176878")

---

