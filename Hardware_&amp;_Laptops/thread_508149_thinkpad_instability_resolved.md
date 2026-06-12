---
title: "thinkpad instability resolved"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by teripittman on 2007-07-23
I think I finally found the instability issue with my thinkpad t23. It's a bad script in imagemagick. I had problems with using update manager to upgrade imagemagick, thought that something was causing instability with the machine and decided to reinstall ubuntu. Lo and behold, I had the same issue start up. This weekend I couldn't get Scribus to load. It acted like a script in the program was stuck in a loop. When I tried update manager today, it had me run dpkg --configure -a and actually told me that imagemagick was in an unstable state and that I needed to reinstall. That wasn't an option so I tried to remove it. Couldn't get that to work either. I decided to upgrade and that's where I saw that there was a problem in the script that did not work in the old version. The upgraded version was able to install and I believe that has resolved the issue. Posting this here in case someone else finds update manager hanging on these updates.

---

