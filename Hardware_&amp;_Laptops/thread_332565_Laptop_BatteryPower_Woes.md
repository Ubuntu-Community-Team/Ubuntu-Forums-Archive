---
title: "Laptop Battery/Power Woes"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by DocMSK on 2007-01-06
Hello,

I know much has been written about this subject on these forums but as someone new to Linux I am finding all the information a little overwhelming. So, what I am looking for is an explanation/solution to my question that even I could understand.

My setup:

Acer TM803LMi Laptop
Ubuntu 6.10

My Question/Problem:

I used to run WinXP on this laptop and get battery life in excess of 4 hours. Now with Ubuntu I get about an hour. Some things I have tried to increase battery life:

- Installed EmiFreq 0.18 to enable me to scale my processor down to 600MHz when running on battery;

- Installed the ATI video drivers and set the video card to a lower power rating;

- Set the wireless to power saving when running on battery; and

- Turned on Laptop-mode (i think thats what it was called).

I have heard and read about DSDT (Differentiated System Description Table), not sure what this is or what it does. I found this [link]("https://help.ubuntu.com/community/ACPIBattery") but it looks a little daunting. Would this help with my problems? 

Also, the Gnome Power Manager seems to report battery percentage but not time remaining. A bubble periodically pops up telling me that I have x% battery left and y mins remaining even when the battery is fully charged and it tells me "Power critically low".


So, can anyone help me sort these problems out? Apart from these Ubuntu works great on this laptop and I am slowly migrating away from WinXP.

Any help appreciated!

Thanks
Doc

---

### Post by teaker1s on 2007-01-06
battery monitor is buggy mine alternates between three states-fully charged and sod all time left,about right and then days of charge left in hours. I've found it seems to work better if you start fully charged,let it run low and then while running let it completely charge. if you charge it turned off it throws a headfit on battery charge and time remaining

---

### Post by DocMSK on 2007-01-08
BUMP, any other info would be appreciated, particularly about the DSDT (Differentiated System Description Table) (see original post above).

Thanks
Doc

---

### Post by Sha-baz on 2007-01-08
Same problem here, Sony VAIO laptop. 
I'm on AC most of the time, so it's not really a big personal problem but if something can be done about it, I sure'd like to hear it.

---

### Post by tweedledee on 2007-01-09
> **Sha-baz said:**
> Same problem here, Sony VAIO laptop. 
I'm on AC most of the time, so it's not really a big personal problem but if something can be done about it, I sure'd like to hear it.

If you've enabled laptop mode in /etc/default/acpi-support, you can edit /etc/laptop-mode/laptop-mode.conf to regulate a number of settings.  As for the gnome battery indicator, I've found it be quite reliable, once I figured out that "40%" means "you can 30 seconds left before I go to 1%" and a couple of other quirks.  It's not terribly accurate, but at least it's consistent!

---

