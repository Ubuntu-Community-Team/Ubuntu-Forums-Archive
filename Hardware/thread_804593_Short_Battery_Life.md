---
title: "Short Battery Life"
date: 2008-05-23
forum: Hardware
---

### Post by LeDieu on 2008-05-23
Hello,

I have a question about the battery use in (K)Ubuntu.
I have a acer 5720 an my problem is that my battery has a life time of max 1 hour and 15 minutes. But i have 2 class mates who have an other laptop than i do have about 2 sometimes 2.5 hours of battery life. And they have the same version of (K)Ubuntu i have. Does someone know what the cause of this problem could be and what i can do to increase my battery life?

Thanks,
LeDieu.

ps: I have already enabled laptop-mode

---

### Post by sdennie on 2008-05-23
When the battery icon appears in the panel (I think only when it's on battery by default), click it and select "Laptop Battery".  You should see a detailed information dialog about your laptop battery.  If "Capacity" is low, it probably just means that your battery is suffering from normal wear and tear faster than your friends machines are (probably due to different usage patterns).

Edit:
I read your post more closely and you didn't say if your friends have the same laptop.  Laptop battery usage can vary widely between different laptops (my current laptop for example gets nearly 7 hours of battery life after configuring it well, my old one got around 45 minutes).

---

### Post by LeDieu on 2008-05-23
> **vor said:**
> When the battery icon appears in the panel (I think only when it's on battery by default), click it and select "Laptop Battery".  You should see a detailed information dialog about your laptop battery.  If "Capacity" is low, it probably just means that your battery is suffering from normal wear and tear faster than your friends machines are (probably due to different usage patterns).

Edit:
I read your post more closely and you didn't say if your friends have the same laptop.  Laptop battery usage can vary widely between different laptops (my current laptop for example gets nearly 7 hours of battery life after configuring it well, my old one got around 45 minutes).

I think you have an other battery manager because i don't have the information dialog in KDE's "Power Manager".
And i have also edited my post. 
And your right. My class mates have complete other laptop's. But isn't it strange that i have 1 hour less battery time.

---

### Post by sdennie on 2008-05-23
> **LeDieu said:**
> I think you have an other battery manager because i don't have the information dialog in KDE's "Power Manager".


I didn't pay close enough attention to the fact that you are running Kubuntu (even though it's clearly stated in the title and several times throughout the thread).  You can probably get the information I was describing by typing following in a terminal:

```

cat /proc/acpi/battery/BAT0/info

```

If there is a huge difference between "design capacity" and "last full capacity" it means your battery is just getting old and no longer able to charge to it's maximum capacity.

> 
And your right. My class mates have complete other laptop's. But isn't it strange that i have 1 hour less battery time.

It's not strange at all.  As I said before, my current laptop lasts nearly 7 hours on battery and my previous laptop lasted about 45 minutes.

---

