---
title: "unable to hibernate but ubuntu seems to hibernate automatically after timeout"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by robamler on 2006-01-08
Hello,

I'm trying to hibernate (suspend-to-disk) my Samsung X20 laptop running Kubuntu Breezy. The system seems to hibernate correctly, but when I wake it up again, it simply hangs after reading the memory dump from the swap partition.

However, today I had my laptop running without doing anything and after some half an hour it seemed to hibernate automatically. I turned the machine on again and expected it to hang after reading the memory dump from the swap partition, but this time it resumed without a problem.

Thus, it seems that my system whith its current configuration is able to do hibernate/resume, only, I don't know how. I already tried "echo 4 > /proc/acpi/sleep", "/etc/acpi/hibernate.sh", and "echo disk >/sys/power/state". All these things work, but when trying to resume the laptop, it hangs.

Is there a log-file where I can see what my system does when I leave it unused for some half an hour? The command that is executed automatically after this timeout seems to work.

Thanks in advance,
Robert

---

