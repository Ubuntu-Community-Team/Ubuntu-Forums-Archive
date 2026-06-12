---
title: "Compaq Laptop Freezing/Overheating"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by blkish on 2006-06-14
hi

i'm running Ubuntu 6.06 on my compaq evo n410c laptop, which has been working great :)

however recently it has started to 'freeze' - ie whole machine locks up, mouse doesn't move, can't ssh in remotely. i suspect that it may be overheating.

is there a way i can either monitor the system to see what might be causing these crashes, or make the system run the fan constantly/more frequently? i remember using the hw.acpi.thermal sysctls on FreeBSD for this sort of thing - is there an equivalent for Ubuntu?

thanks

blkish

---

### Post by 23meg on 2006-06-14
Run the "top" command to see if any processes are maxing out your CPU, and check your temperatures listed in /proc/acpi/thermal_zone/ to see if there's overheating.

---

### Post by David Gerard on 2006-09-07
I have this problem with my N410c. I blame the W200 wifi driver, because I blame everything on it ;-)

I've started using ktemperature, which is a KDE doc app that just sits there displaying your CPU temperature. If it hits 80 deg C, you're in trouble. At 90 deg C, the laptop powers off immediately.

I blame the wifi because the problem is some sort of ACPI weirdness - after coming back from suspend or hibernate, it doesn't seem to switch on enough of the three fans.

(I'm seriously considering writing a monitoring script of my own to switch on fans as needed when it goes over 70 degrees, as the kernel stuff just isn't behaving properly whatever the reason. Or perhaps just a manual interface where I can switch fans on by hand or something. I'll post if I ever get around to this.)

---

### Post by sovin on 2006-09-07
is there a similiar app you could recommend for the gnome environment--

i've been experiencing random freezes as well and can't attribute them to anything but overheating as i generally use my notebook for movies.

---

