---
title: "Battery Duration with Asus U30JC"
date: 2011-01-12
forum: Hardware
---

### Post by pep_dj on 2011-01-12
Hello and sorry for my bad english (I'm from Spain)

I'm using an ASUS U30JC laptop and I noticed that battery life is longer when I'm working with MS Windows, and is shorter when I'm using Ubuntu. I would like to increase my battery life under Ubuntu. Anybody can help me?

Thanks

---

### Post by bananafeller on 2011-02-11
BUMP i am having the same issue ... 7-8 hours with win 7 and only 4-5 with 10.10.

---

### Post by edcrumly on 2011-02-11
Here's a great place to start ,[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement).
Also copy and paste sudo apt-get install laptop-mode-tools into your terminal, it's great. Also install the packages acpi-support,  pm-utils, and there is a program that I cannot remember or find right now, but it looks at all programs or events that use power, and advises possible fixes. Google any additional help, there's probably lot's more out there. I use asus 1001P , and it routinely pulls 7+ hours, but I turn off almost anything that isn't needed, ( Bluetooth, cups, touchpad, etc.) and have installed the program Juptiter , which allows slight overclocking and a great underclocking feature for off AC plug.

---

### Post by Arkanus on 2011-02-11
laptop-mode-tools conflicts with pm-utils and acpi depends on it... laptop mode was great, it allowed many config options, but idk why it has conflicts with acpi now

---

### Post by bananafeller on 2011-02-13
hey thanks for the advice once i've installed laptop-moode-tools how do i get into the options?

---

### Post by tet21tet on 2011-08-17
It is because the nvidia card is running but the optimus is not.
In windows, optimus turns off nvidia when not in use, therefore saving power,
but this does not work in ubuntu.

I am trying to find a way to turn off nvidia.:P

---

