---
title: "How do you get Wlan to work?"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by jincast90 on 2006-11-03
I have got my acer laptop to run ubuntu without any errors what so ever. I installed beryl with out a problem also. I am running edgy, and I would like to know how I can get my wireless lan card in my laptop to work now.

---

### Post by doobit on 2006-11-03
> **jincast90 said:**
> I have got my acer laptop to run ubuntu without any errors what so ever. I installed beryl with out a problem also. I am running edgy, and I would like to know how I can get my wireless lan card in my laptop to work now.

That depends on what the wireless chipset is in your laptop. Many can use ndiswrapper, others have linux drivers. Do you know what chipset yours has? 
You can usually find out with the command lspci in a terminal, (or dmesg will work too, but give you a lot more info).

---

### Post by jincast90 on 2006-11-03
> **doobit said:**
> That depends on what the wireless chipset is in your laptop. Many can use ndiswrapper, others have linux drivers. Do you know what chipset yours has? 
You can usually find out with the command lspci in a terminal, (or dmesg will work too, but give you a lot more info).

Ok I used the lscpi command I got a lot of stuff which I dont know what means. What should I be looking fore? Could my chipset be intel 915? Or is that my gfx card?

---

### Post by jincast90 on 2006-11-04
Bump..

---

### Post by Shaye on 2006-11-04
> **jincast90 said:**
> Ok I used the lscpi command I got a lot of stuff which I dont know what means. What should I be looking fore? Could my chipset be intel 915? Or is that my gfx card?

Intel 915 is your chipset Indeed.

---

### Post by jincast90 on 2006-11-09
Ok so intel 915 is my chipset. What do I do know?

---

### Post by jincast90 on 2006-11-10
Bump

---

