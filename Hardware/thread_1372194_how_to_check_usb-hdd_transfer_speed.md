---
title: "how to check usb-hdd transfer speed?"
date: 2010-01-04
forum: Hardware
---

### Post by meborc on 2010-01-04
the title says it all...

do you guys know any command that will allow me to monitor file transfer speed from my comp hdd to usb hdd?

i can't find anything on the internet

---

### Post by meborc on 2010-03-19
a very lonely *bump*

---

### Post by BugBuster on 2010-03-19
Hi..

You could use the combination of 'time' & 'cp' commands in linux.

e.g
$time cp /your_comp_hdd/movie.avi /your_usd_hdd/movie.avi

Then as output u will get the time it took to complete the transfer using which and also the amount of data transferred you can calculate the disk speed.

A bit primitive but effective!!

---

### Post by Fafler on 2010-03-19
Remember to include a sync after that, if you measure write speed, otherwise you'll only measure write speed to the buffer, which is effectively only read speed on the internal drive.

You might also consider using iotop for the purpose.

---

### Post by sam.reader on 2010-03-19
I don't understand.Why would we not get such a good feature directly with the OS.
I mean the idea is to make Ubuntu much better than windows by incorporating its good features and make it even better isn't it?
I hope those guys will bring in a better version from now on which satisfies everyone's needs.

---

### Post by Grenage on 2010-03-19
```
rsync --stats --progress LOCATION DESTINATION
```

Would probably do you?

---

### Post by meborc on 2010-03-20
thanks guys! :) I will try your suggestions tomorrow and let you know my results

thanks again!

---

