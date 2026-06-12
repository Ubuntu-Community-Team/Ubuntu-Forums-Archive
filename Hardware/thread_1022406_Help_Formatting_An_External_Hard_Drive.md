---
title: "Help Formatting An External Hard Drive"
date: 2008-12-26
forum: Hardware
---

### Post by DocHolliday2006 on 2008-12-26
So I just bought a Western Digital USB external hard drive. I plugged it in, and it appears on the desktop, but I think I have to format it for use. 

1) I was told to use Gparted, but it says I need root privileges to execute this. How do I get root privileges? 

2) What's the best file format to use?

3) Anything else I need to know?

Thanks for your time
-Andrew

---

### Post by taurus on 2008-12-26
First, you need to unmount that external harddrive first before you can format it.

Then, you can run gparted from System -> Administration or from a terminal with

```
gksudo gparted
```

Do you plan to share that external harddrive with another OS (windows or mac)?  If you only use that drive for Ubuntu, then format it as ext3.  Otherwise, format it as ntfs if you want to share that drive with windows system although windows can access ext3 with fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

