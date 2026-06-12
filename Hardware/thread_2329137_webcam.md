---
title: "webcam"
date: 2016-06-28
forum: Hardware
---

### Post by hbw1770 on 2016-06-28
Have installed xenial on my MSI GT72 laptop and I'm very happy with it, but I don't know how to activate its built in camera so I can use it with skype and other programs that can use a camera. Any help would be much appreciated.

---

### Post by coldraven on 2016-06-28
First off, try installing Cheese from the Software Centre and see if you get a result.

---

### Post by hbw1770 on 2016-06-28
Thank you Coldraven, both cheese and skype say ""no device detected", however the webcam was working fine under win 10 before.

---

### Post by papibe on 2016-06-28
Hi hbw1770.

Could you open a terminal, run these commands and paste back the results (you can copy/paste the text)?
```
grep -i cam /var/log/syslog

dmesg | grep -i cam

lsusb

lspci -nnk | grep -i cam
```
Regards

---

### Post by hbw1770 on 2016-06-29
Sorry everyone, I have wasted your time. Have just downloaded the MSI GT72 user manual (which I should have done in the first place) and found that to activate the webcam you press Fn-F6, (F6 even has a little design on the key, which with a rather long stretch of imagination, could be interpreted as a camera) which I did and it now works fine in both cheese and skype. Thank you papibe, there is now no need for me to run the commands you posted.

---

