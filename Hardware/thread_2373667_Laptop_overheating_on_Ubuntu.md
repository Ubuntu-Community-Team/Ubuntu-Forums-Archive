---
title: "Laptop overheating on Ubuntu"
date: 2017-10-08
forum: Hardware
---

### Post by tea-tm on 2017-10-08
Hi everyone, 
I switched my old alienware laptop to ubuntu a while back and ever since it's battery lasts for an hour at most and it overheats like crazy and shuts down if I don't keep it up on a stand and in a cool area. This isn't caused by gaming or anything, even netflix will make it overheat. The laptop is older and second hand so I recognize that that may be part of it, but I opened it and cleaned out all the dust, etc and it hasn't helped, and this didn't happen when it was running windows. If anyone has advice I'd greatly appreciate it, 90% of my university's lecture halls are so old they don't have power outlets and laptop burns/losing all your work when your computer randomly shuts down are not fun. 
Thanks!

---

### Post by mörgæs on 2017-10-09
Let's see the hardware details. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post lshw.txt in CODE tags.

---

### Post by tea-tm on 2017-10-09
It just says "USB".

---

### Post by mörgæs on 2017-10-11
Something's wrong. Please tell exactly what you did.

---

### Post by tea-tm on 2017-10-12
I opened my terminal, copy/pasted the line you provided, and typed in my password when prompted. The only output was "USB".

---

### Post by mörgæs on 2017-10-13
My post mentioned lshw.txt, didn't it?

---

### Post by tea-tm on 2017-10-14
Yes-- that was part of what I input

---

### Post by mörgæs on 2017-10-16
Lshw.txt is a file created on your hard disk.

> **mörgæs said:**
> ...and post lshw.txt in CODE tags.

---

### Post by tea-tm on 2017-10-17
I'm not sure what you mean-- I input the code you gave me and the readout was just USB

---

### Post by Kanfused on 2017-10-17
> **tea-tm said:**
> I'm not sure what you mean-- I input the code you gave me and the readout was just USB

Hi, please read again. Open the file manager (Nautilus) and browse to the home folder. There is a text file called lshw.txt created there by the command. Open that text file and copy the contents here inside a [code] [ /code] format so as someone can help you.

---

