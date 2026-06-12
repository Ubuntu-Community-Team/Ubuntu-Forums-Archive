---
title: "Battery not found"
date: 2012-12-17
forum: Hardware
---

### Post by Slidescream2013 on 2012-12-17
I am running a dual boot of windows 7 and Ubuntu 12.04 on my toshiba satellite L655. My battery life is normal and I don't have any issues on the windows partition. In Ubuntu, none of the power manager programs recognize the battery. I do not have a battery icon. I have found many threads, but none with a fix that worked for me. 

 How do i get Ubuntu to recognize that my battery is present?

---

### Post by offgridguy on 2012-12-18
> **Slidescream2013 said:**
> I am running a dual boot of windows 7 and Ubuntu 12.04 on my toshiba satellite L655. My battery life is normal and I don't have any issues on the windows partition. In Ubuntu, none of the power manager programs recognize the battery. I do not have a battery icon. I have found many threads, but none with a fix that worked for me. 

 How do i get Ubuntu to recognize that my battery is present?
I am curious, do you have an icon when plugged into AC power?

---

### Post by Slidescream2013 on 2012-12-18
> **offgridguy said:**
> I am curious, do you have an icon when plugged into AC power?



No, I have never had the icon from install, either on battery or AC

---

### Post by offgridguy on 2012-12-19
This puzzles me, i wish i could help more but at the moment i am out of ideas.
Hopefully someone else has something that will help, i am subscribed to this
thread in case i find something that will work.  Sorry i can't be of more help.:)

---

### Post by Slidescream2013 on 2012-12-20
Its quite puzzling, and annoying! I have been looking for months to find a fix to this. I am fairly new to Linux OS and don't dare to do to much digging into the system on my own.

I have seen other postings of people with toshiba laptops having this issue, but I have never seen a fix for it.

---

### Post by Slidescream2013 on 2013-01-10
bump. I have been digging deep into the internet and can still find nothing. I have seen a couple references to similar issues on forums but never any answers. Any ideas?

---

### Post by Toz on 2013-01-10
This might be of interest: [http://techinterplay.com/fix-toshiba-battery-issue-linux.html]("http://techinterplay.com/fix-toshiba-battery-issue-linux.html"). Unfortunately, it involves rebuilding the kernel.

However, from that link:
> The cause of issue is because Toshiba included two sets of boot data that tell the OS what hardware exists in the machine. Windows reads the correct one whereas Linux doesn’t.
I wonder whether telling the BIOS to support a different OS might work. Maybe you could try the following kernel parameters to see if they help (one at a time):
- acpi_osi=
- acpi_osi=Linux
- acpi_osi="Windows 2006"

See the "Temporarily Add a Kernel Boot Parameter for Testing" section [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters")

---

### Post by Slidescream2013 on 2013-01-22
I dual boot with windows 8, Would altering the BIOS in that manner affect my other partition?

---

### Post by Toz on 2013-01-23
> **Slidescream2013 said:**
> I dual boot with windows 8, Would altering the BIOS in that manner affect my other partition?

You are not altering the BIOS at all, you are just telling the BIOS that you are a different OS and it is providing you with a different set of "boot data" (acpi tables). It shouldn't affect the Windows 8 install.

This may or may not work. The article indicates that you need to compile a custom kernel. In lieu of going through that complicated process, I'm wondering if you could "fool" the BIOS into thinking that a Windows-based OS is booting, thus having it generate this other set of "boot data".

Just a thought.

---

