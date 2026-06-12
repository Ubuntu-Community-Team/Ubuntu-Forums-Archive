---
title: "Sunbird freezing on 8.04 AMD64"
date: 2008-08-04
forum: General Help
---

### Post by kavoura on 2008-08-04
I am using Sunbird on Ubuntu 8.04 64-bit version. Until now it was working perfectly. I had previously used it on Ubuntu 7.10 on another PC, and then set up this new PC and transferred all the profile files over to the new PC and it loaded all the events, etc., from the old installation.

But then today, the program froze. And since then I cannot get it to work properly. I have closed it by forcing it to quit, when open it is totally unresponsive and goes completely grey. When I reopen the program it is the same. I have tried rebooting to the PC to remove all trace it from RAM before starting the program again, but still the same problem. I have tried uninstalling and reinstalling Sunbird, but it is still the same -- it just hangs after opening.

This is a great program, when it works, but nothing has changed recently, no updates to the program were installed prior to these problems. I have no idea what is causing this.

What could be causing this problem and how do I fix it?

---

### Post by kavoura on 2008-08-04
I managed to fix the problem.

I looked through the files in the profile settings for Sunbird in my home directory under .mozilla/Sunbird

there were various files there, and I renamed the extensions 1 at a time and opened the program to see which would allow it to work by not being loaded. It was the file storage.sdb that when renamed, allowed Sunbird to open by not being loaded. But that file contains all the events data. So I had to manually edit the file, by installing the SQLite database browser from the repositories, and then use that to open the storage.sbd file, and remove various recent entries all of which had reminders. Once they were removed I went back into Sunbird and recreated the entries that I wanted, but this time without reminders. I did try with a reminder and the program hung straight away, but without reminders it all works. So I guess there is a bug in the reminders part of the program.

---

