---
title: "Laptop runs faster on batteries"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by abgesq on 2007-04-01
I am running Feisty on a Vaio laptop and have noticed a significant difference in performance when plugged in vs. on battery.  My pc runs much faster (i.e. boot up, program load time, cpu speed, etc.) when on battery and is sluggish when plugged in.  Any ideas? 

Thanks in advance for the help!

---

### Post by niobiumboy on 2007-04-02
Yeah, well, tha'ts boind to happen if you are copying the servelets and opticating with C++, or I thought it did when I ran my laptop.  I'm always thinking before I turn it on.

---

### Post by jjordan on 2007-04-02
Most likely your CPU frequency profile is set more conservatively for battery operation.  Take a look at the power manager you are using.  Many laptops are set to run at maximum CPU speed when on AC power and run at a lower speed on battery to conserve power.  Depending on the setting and how well it works on your laptop the frequency scaling should speed up the CPU when it is needed.  I am pretty prejudiced against Soney so I am afraid I don't have a lot of direct experiance with the Vaio.  I believe that there is an ACPI helper for Sony, search in Aptitude or Synaptic for Soney and look at the descriptions.  After you install that you may have better control.

-j

---

### Post by abgesq on 2007-04-02
Thanks for the assist...I'll check into it and see if it helps! (shame I found Linux after I had my Vaio....)

---

### Post by BungaMan on 2007-04-13
jjordan, you're talking about the reverse of what he's saying!

abgesq, did you fix your problem?  how did you do it?  I'm having the same issue.

---

### Post by mikuton on 2007-05-10
Which kernel version are you running? At least in my case this problem was caused by the 2.6.20-15-generic kernel that was installed with Feisty. Installing the 386 kernel "corrected" the problem (although it would be nice to know what subsystem of the generic kernel causes this problem). My laptop is Asus A6VM, by the way.

---

