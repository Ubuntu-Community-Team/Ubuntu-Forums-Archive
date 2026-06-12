---
title: "Headphone and Microphone Jack slots not working"
date: 2011-06-03
forum: Hardware
---

### Post by tsagi on 2011-06-03
I have a custom notebook (Ubuntu 11.04 dual boot with windows 7) and my problem is that when i connect my headphone/earphone jack in the slot, nothing happens. My built-in headphones continue working and I hear no sound from the headphone/earphone. The same thing happens with the microphone slot and the built in microphone. Some help please??

---

### Post by sectshun8 on 2011-06-03
Youre not alone, check out these threads (search is your friend)

[Thread 1]("http://ubuntuforums.org/showthread.php?t=1598229&highlight=headphone+jack")
[Thread 2]("http://ubuntuforums.org/showthread.php?t=1751483&highlight=headphone+jack")

---

### Post by lidex on 2011-06-04
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Sander001 on 2011-10-25
Hello!
I am having this exact issue. Here's my link 
[http://www.alsa-project.org/db/?f=30af5eba9479f4554c31999a71cb2eb08b785140](http://www.alsa-project.org/db/?f=30af5eba9479f4554c31999a71cb2eb08b785140)

Any help is appreciated, thank you.

---

### Post by Sander001 on 2011-10-26
Somebody?

---

