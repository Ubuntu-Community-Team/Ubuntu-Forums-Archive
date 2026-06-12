---
title: "CPU fan on 20.04 running high when the laptop is plugged in but running normal on ba"
date: 2022-01-03
forum: Hardware
---

### Post by arunkumar413 on 2022-01-03
Hello Ubuntu,

My running ubuntu 20.04 on AMD Ryzen 5 processor. The is running high when connected to the mains supply but it's working normally on battery power. Seems like this is happening since the new updates. Is the fan's speed control handled by OS or is it something that I have to control via BIOS?

Thanks
Arun

---

### Post by schragge on 2022-01-04
It's usually controlled via BIOS/ACPI, but there exists [fancontrol]("https://manpages.debian.org/unstable/fancontrol/fancontrol.8.en.html") as well. To configure the latter, use [pwmconfig(8)]("http://pwmconfig(8)").

---

