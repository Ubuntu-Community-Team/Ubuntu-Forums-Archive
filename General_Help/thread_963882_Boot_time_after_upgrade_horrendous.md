---
title: "Boot time after upgrade horrendous"
date: 2008-10-30
forum: General Help
---

### Post by Jdm111 on 2008-10-30
Wow, I takes about 2 minutes to get to the login screen from usplash, Please help

---

### Post by Jdm111 on 2008-10-30
> **Jdm111 said:**
> Wow, I takes about 2 minutes to get to the login screen from usplash, Please help

Please please help.

---

### Post by shane19174 on 2008-10-30
That's not a lot of information to go on. How about installing "bootchart" (via apt-get or synaptic)? Then, after you reboot, you can look under /var/log/bootchart and find a nice graphical representation of the entire boot process as a .png file. If you post it here, someone might be able to help.

---

### Post by GuitarRocker2562 on 2008-10-30
Hmm......... that's not good. Reboot, and at grub, when you see the choices, go to Intrepid, and hit "e" then got to the second line, and at the end of the line, type a space, and then "profile" without the quotes, then get out of edit mode, a press b to boot. That boot will be slow, but the boot after that should be quicker.

---

### Post by Jdm111 on 2008-10-30
> **shane19174 said:**
> That's not a lot of information to go on. How about installing "bootchart" (via apt-get or synaptic)? Then, after you reboot, you can look under /var/log/bootchart and find a nice graphical representation of the entire boot process as a .png file. If you post it here, someone might be able to help.
Thanks, Installing now

---

### Post by Jdm111 on 2008-10-30
> **GuitarRocker2562 said:**
> Hmm......... that's not good. Reboot, and at grub, when you see the choices, go to Intrepid, and hit "e" then got to the second line, and at the end of the line, type a space, and then "profile" without the quotes, then get out of edit mode, a press b to boot. That boot will be slow, but the boot after that should be quicker.

Argh! It was very very slow the first boot after but now back to normal slow

---

### Post by Yellow Pasque on 2008-10-30
Boot without the quiet and splash options (edit the boot line in GRUB as instructed previously), so you can see everything that is happening. It sounds like your boot is hanging somewhere.

---

### Post by Jdm111 on 2008-10-30
> **Temüjin said:**
> Boot without the quiet and splash options (edit the boot line in GRUB as instructed previously), so you can see everything that is happening. It sounds like your boot is hanging somewhere.

Ah! It takes ages at "configuring network devices"

---

### Post by Jdm111 on 2008-10-30
> **Jdm111 said:**
> Ah! It takes ages at "configuring network devices"

Anyone no the problem?

---

### Post by Jdm111 on 2008-10-30
Please please help, This is very irratating as it is

---

### Post by Jdm111 on 2008-10-30
In the end i fixed my problem with sudo update-rc.d -f networking remove

---

### Post by matbroadbent on 2008-11-01
Thank you Jdm111.  :)  I had the same problem as you described and it was driving me up the wall!

sudo update-rc.d -f networking remove

worked for me too.

---

