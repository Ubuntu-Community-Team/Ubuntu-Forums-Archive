---
title: "Utilizing hard drive spin down"
date: 2010-04-13
forum: Hardware
---

### Post by WA1DH on 2010-04-13
I have a WD Caviar Green 1TB (WD10EARS) HDD installed in an old Pentium III 500 MHz I'm using as a home file server. I have Ubuntu 9.10 Desktop on it. I've read extensively about the issues with these drives and their head parking feature. Currently I'm seeing ~15 load/unload cycles per hour, and I've had it running about 60 hrs so far.

I know I can disable the head parking feature with WD's firmware update, but I'd prefer to keep it enabled and instead have the drive completely spin down when not in use. I only access the server every few hours to synchronize files between different machines. It would be nice if I could make the HDD spin down say after 30 minutes of inactivity. If I only access it ~10 times a day, that would save power and wear and tear on the drive. I've tried to figure out how to do this, but haven't found an answer. I checked the 'Spin down drives' tab under gnome-power-preferences but that doesn't seem to do anything. Even with the system idle, the drive seems to be accessed every 5 or so minutes for some odd reason. I checked my system log and the only thing I saw running was what seemed to be a check for cron jobs that runs once every hour (perhaps this can be disabled/lengthened too?). Any ideas as far as how to make the drive spin down when idle?

Thanks.

---

