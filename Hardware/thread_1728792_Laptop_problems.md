---
title: "Laptop problems"
date: 2011-04-14
forum: Hardware
---

### Post by Culinax on 2011-04-14
Hello everybody,

I have some problems here with using Ubuntu on my laptop.

First of all, my laptop's fan doesn't work anymore at times. I've tried a lot of things but it still doesn't work. It's an Acer TravelMate 7730. Is there a setting to make it work again, or to make it work at a lower temperature?

Secondly, I've changed some settings in Power Management, but they don't work when my laptop's not adapted to that cable to charge it (don't know the name of it... my English isn't that good). It always suspend when I close the lid, but I want it to just show a blank screen and also lock the screen if possible and when there's just 5% energy left it has to shut down by itself. Is this possible?


Thank you in advance,

Culinax

---

### Post by Hedgehog1 on 2011-04-15
To improve the function of the laptop fan using 'current' grub options:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

**And reboot. The operation of this will keep your computer running cooler.**

In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by Culinax on 2011-04-15
I'm not using my laptop right now, but thank you very much. I'll try it as soon as I'm using my laptop.

Is there also someone who can tell me how to change the behavior when my laptop's lid is closed? I did some research yesterday and I found that most people with a laptop have an extra tab in Power Management where you can change these settings. I haven't, so maybe Ubuntu doesn't recognize my system as a laptop. Or is there a special Ubuntu version for laptops?

Culinax

---

### Post by chotamunda10 on 2011-04-15
We can't upgreade on its.

---

### Post by Culinax on 2011-04-15
I've just tested it on my laptop and it works :D
My laptop didn't get warmer than 80°C so far, normally it was close to 100°C.
Thank you very much!

Now the only thing I need to know is this:

> **Culinax said:**
> 
Is there also someone who can tell me how to change the behavior when my laptop's lid is closed? I did some research yesterday and I found that most people with a laptop have an extra tab in Power Management where you can change these settings. I haven't, so maybe Ubuntu doesn't recognize my system as a laptop. Or is there a special Ubuntu version for laptops?


---

### Post by Hedgehog1 on 2011-04-15
> **chotamunda10 said:**
> We can't upgreade on its.

**chotamunda10** - I think you are saying: 'We cannot upgrade to the current grub because we are on 10.04 LTS'.

***If that is what you re saying***, the command for 10.04 looks like this:

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi_osi='Linux'**"
```

```
sudo update-grub
```

***The Hedge***

:KS

---

### Post by Culinax on 2011-04-16
I'm sorry but I just realized that I asked my question wrong.
What I want to say is how I change the behavior of my laptop when it's on battery power.
And I don't have the "On Battery Power" tab in Power Management.

[IMG]http://www.techotopia.com/images/2/2f/Ubuntu_10.10_laptop_power_management.jpg[/IMG]

So it's that tab on this image above that I don't have on my laptop. It's just "On AC Power" and "General".
Is that caused because Ubuntu doesn't recognize this as a laptop or is there a special Ubuntu version for laptops?

---

