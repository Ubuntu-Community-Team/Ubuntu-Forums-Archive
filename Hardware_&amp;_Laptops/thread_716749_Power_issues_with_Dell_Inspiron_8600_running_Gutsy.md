---
title: "Power issues with Dell Inspiron 8600 running Gutsy"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by nikiu on 2008-03-06
I have a Dell Inspiron 8600, running Triple Boot (Ubuntu, Vista and XP). I had and still have problems with the power functions. I cannot start Ubuntu if I am on battery power. I have to put the power line. Also, I have to Shut Down every time that I want to leave my Laptop. I cannot Stand by or Hibernate because it hangs up.

Any suggestion please?

---

### Post by kaurman on 2008-03-06
Hi!

Could you describe your problem in detail? What happens if you try to start Ubuntu on battery?

You could also check [this link.]("http://ubuntuforums.org/showthread.php?t=471855")

---

### Post by nikiu on 2008-03-06
When I start my laptop on battery and I choose to work on Windows (XP or Vista) it works normally. When I choose Ubuntu, it starts normally then the screen goes black and I hear the Hard Disk working. After 3-4 minutes it stops and then nothing happens. No blinking lights, no sound from the hard disk.

When I choose Ubuntu and I am on power line, the screen goes black and after 5 minutes (why so long???) it loads up and it shows the log in windows and everything works fine.

However, in both cases, Stand By or Hibernate or when I close the laptop lid, the laptop hangs up and I have to hard reset it.

Thanks.

---

### Post by kaurman on 2008-03-06
Hi!

I am definitely not an expert on the subject but I think you should first check what the log files have to say.

Boot to ubuntu (on AC power). Once it is working go to Applications -> Accessories -> Terminal and type dmesg. Paste the output here so someone can have a look at the log.

Kaur

---

### Post by nikiu on 2008-04-28
Well, I installed Hardy and all the problems with the power are almost resolved. The only problem is that sometimes, it hangs up when the laptop Stands By. Anyways, this is not a problem to me so thanx anyways.

Nick.

---

