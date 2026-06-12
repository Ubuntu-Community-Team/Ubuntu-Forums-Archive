---
title: "Samsung Hybrid Hard Drive support"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by vav on 2006-10-20
Is HHD support coming to Edgy/Dapper soon? Or will it be worked on only after  Samsung puts these hard drives into market (i.e. after reverse engineering them)? It seems to be an important technology for laptops.

[http://www.tfot.info/content/view/83/59/](http://www.tfot.info/content/view/83/59/)

--vav

---

### Post by Kateikyoushi on 2006-10-20
I would like to know as well but I guess it takes a while till we have the tools to use it. Slashdot asked the same question half a year ago. [LINK]("http://ask.slashdot.org/article.pl?sid=06/03/03/2247246")

---

### Post by cb474 on 2007-03-09
Now that the Samsung Hybrid drive has been released, is there any update on weather this will be supported in Linux/Ubuntu? I would love to benefit from the battery life saving potential.

---

### Post by bodycoach2 on 2007-03-14
I'm surprised this thread isn't getting more attention. Hybrid hard drives will certainly help with battery life. This might be a question for the Linux kernel people.

---

### Post by cb474 on 2007-03-17
Somewhere, in the Ubuntu wiki or something, I saw that the official Ubuntu position about spinning down hard drives is that they don't draw enough power for it to make a significant difference. Only about 1 watt/hr would be saved. Perhaps this is why the hybrid drives aren't drawing more attention? Hard drives have already been written off as not important for power saving?

I don't really buy the position on hard drives spinning down though. There's nothing that really in itself would save that much power. The way, I've found, to get better battery life is to tweak everything possible. Each watt ends up adding up.

It also seems like for the vast majority of people, battery life is worse in Linux than Windows, so the problem clearly needs to be addressed. I definitely think hard drives spinning down and hybrid drives should be taken seriously. (By the way, I don't think laptop-mode's way of dealing with hard drives is very elegant or easy to use. So I think this could be improved upon.)

---

### Post by vav on 2007-03-20
Hybrid drives are not just about power - they're about fast boot times. So it's not a simple matter of writing a driver for the drive. Someone has to figure out what files should be saved on the flash portion of the drive to allow for fast boot and application startup times!

---

### Post by cb474 on 2007-03-22
> **vav said:**
> Hybrid drives are not just about power - they're about fast boot times. So it's not a simple matter of writing a driver for the drive. Someone has to figure out what files should be saved on the flash portion of the drive to allow for fast boot and application startup times!

All the more reason it would be great to see support for these in Ubuntu!!:guitar:

---

### Post by ajrobb on 2007-12-17
I run a low-power Linux server on a VIA EPIA micro-itx system. The main duty is to receive my e-mail. Most of the time it just sits there logging a small amount data to /var. This logging prevents the disc from spinning down. I would like to use a hybrid hard drive as a write cache - I'd expect the disc to spin up only every few DAYS.

Being on 24x7 means there is no point in having fast boot time. It never sleeps, so no point in fast recovery time. I vote that no file is pinned into flash.

---

