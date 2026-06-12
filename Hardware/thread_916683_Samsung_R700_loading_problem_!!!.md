---
title: "Samsung R700 loading problem !!!"
date: 2008-09-11
forum: Hardware
---

### Post by orik on 2008-09-11
Hi all

My laptop is Samsung R700:
Intel Core2 Duo T5550 1.83GH
3GB RAM
HDD - WDC WD3200BEVT-22ZCT0
Mobile Intel 965 Express Chipset Family
Intel Pro/Wireless 3945BG
Marvell Yukon 88E8055 PCI-E Gigabit Ethernet Controler
Agere Systems HDA Modem

I've got the last ubuntu from the website.I installed and reinstalled ubuntu few times but every time, after the installation when I try to log in - the ubuntu is not loading.when i try recovery to see what is going on - it stop loading after : "Detecting Wirelees connection" or similar.
Then I plug the network cable into the laptop(RJ45 thing is the name) to avoid the wirelless to be my active network connection - and still the same. Dont know what to do now.Please help.

Thanks in advance.

---

### Post by Bucky Ball on 2008-09-11
You might try posting this in 'Networking and Wireless' forum. You could also try this.

When you get to your grub menu list, choose regular kernel, not recovery, and hit 'e' to edit. Find the kernel line and at the end add:

noacpi

Then boot (hit return and 'b' I think but the instructions are at the bottom of the screen) and see what happens. If nothing, try:

acpi

... at the end of that line. If you could post that kernel line here or in the other forum, that will help to find a fix. There are a variety of commands you can try to get you up before you dig deeper. As mentioned, you will get more specific help in the other forum but let us know your results. This is guesswork but may help. :)

On further investigation, looks like this card can be a little tricky, but odd that it is causing your problems before login. There is a lot of info out there though. One example:

[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

---

### Post by orik on 2008-09-11
Hi there

Just done what you told me and still nothing.Also when i checked the line after the first restart "noacpi" was not there, after the secon restart "acpi" was not there.the kernel line is :

kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=0599d216-8e06-451e-bf45-c4241aa1e362 ro quiet splash

---

