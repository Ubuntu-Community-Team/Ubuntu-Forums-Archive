---
title: "kernel edit"
date: 2010-02-03
forum: Hardware
---

### Post by hippickles on 2010-02-03
I recently modified the fan settings on my acer aspire one zg5 110-1295 using the directions found here: [http://piie.net/files/acerhdf_README.txt](http://piie.net/files/acerhdf_README.txt)

I downloaded acerhdf_kmod-0.5.22.tar.gz to my firefox download folder and used archive manager to extract it to the same folder. I then compiled (cd /home/user_name/Downloads/acerhdf_kmod && make), installed (sudo make install), and then loaded into the kernel (modprobe acerhdf). I am wondering if I still need those files in the downloads folder or if they can be deleted or moved to where they belong.

---

