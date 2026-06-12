---
title: "I Incresed my laptops battery life twice!"
date: 2010-10-28
forum: Hardware
---

### Post by ario on 2010-10-28
I'm a Linux lover. I used to use Ubuntu for many years. Recently I bought a laptop and noticed that the battery life is less that what it must to be. In my laptops manual the working time on battery was about 2.5 hours to 3.5 hours. But it was obviously 1:30' for me. I tried several ways to increase this time but have no success until I handle it by installing the propriety graphic driver. I will describe it below.
    These are technical specifications:
```
ACER Aspire 5536-5563 laptop
AMD Ati Radeon HD3200 Graphic chip-set
Microsoft Windows 7 and Ubuntu 10.04 installed on dual boot.

```
    After trying some painful tests (I even completely removed hard drive and DVD drive and brought up my laptop with a fresh install of Ubuntu 10.04 on a SD memory card!) have no success increasing the life of my battery. Once a day I decided to dual boot my laptop to Windows 7 and see if it effects on battery life. Now look at this, battery life which was 1 hour and 30 minutes on Ubuntu, was exactly 2 hours and 40 minutes on Windows 7! Windows used about half power than Linux did! Is it because of some different settings on my Linux which causes this difference battery life time?
    Actually no! I tried same settings on both environments. Turned of wireless and networking, dimmed screen to lowest level on both operating systems, and just read a PDF file all the time and prevented both systems to go sleep or turn off screen. It causes a lot of pain in my as*! I felt like one of my friends used to steal from my pocket for a long time! So I decided to find a practical and effective way this time.
    I did not follow those HOWTOs for modifying some configuration files to have no swap, no real log and tmp directories and some other settings to decrease hard disk usage. Because as mentioned above, I tried completely removing my drive and had no success reducing power usage on Ubuntu. Hard drive is responsible for only about 2 Watts of energy on my laptop, But I estimated windows must use about 10 Watts lower energy than Linux. So I touched back of my laptop and distinguished the difference in heat of laptop case when it was on Windows or on Linux. The result was that windows reduces power usage of graphic chip-set and that is the cause of lower power consumption.
    This is the How To: **I downloaded *ati-driver-installer-10-10-x86.x86_64.run* from AMD website and installed it.** On Ubuntu 10.04 not only power consumption reduced 10 Watts just as it was on windows, but also Alpha Blur effect of Compize Fusion is now working like a charm! Which wasn't before.
    It is very important to install the propriety driver. Because it is clear for me after all that Ubuntu's built-in open-source driver is not able to use some special features of my laptops graphic card like Alpha Blur effect and reducing power consumption. By installing propriety driver, power consumption on Ubuntu 10.04 reduced about 45%, and relatively increase battery life. Also heat of laptop case and CPU temperature (Which is near GPU on my laptop) decrease as well.

---

### Post by KayeNg on 2013-01-03
Thanks for sharing this. Do I have to uninstall the pre-installed driver first? If so, how do I do it?

---

### Post by ibjsb4 on 2013-01-03
Good tip

---

### Post by howefield on 2013-01-03
Old thread closed.

---

