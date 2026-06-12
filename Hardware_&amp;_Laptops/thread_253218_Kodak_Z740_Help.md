---
title: "Kodak Z740 Help"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by POKETNRJSH on 2006-09-08
I tried connecting my camera for the first time, and it was detected as a USB imaging device, but it led to one folder over and over. It was recognized in Digikam, but I couldn't copy pictures from it. A google search returned some vague answers, with no real instructions on how to get it working in Kubuntu. Can anyone help?

---

### Post by vidak on 2006-09-14
I just got a Z612, and have the same problem. However, I found a workaround: using gphotofs like:
sudo gphotofs /mnt/camera -o allow_other

and then telling digikam to search for an USB mass storage device at the mount point. Maybe not the best solution, but it works...

Any more ideas?

---

