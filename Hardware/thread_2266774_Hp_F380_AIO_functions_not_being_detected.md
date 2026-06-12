---
title: "Hp F380 AIO functions not being detected"
date: 2015-02-25
forum: Hardware
---

### Post by mandarpowale on 2015-02-25
Hello friends,

I have an old HP F-380 USB printer that I purchased in 2006-2008. The printer does get detected but I don't know how to scan documents using that printer in my UBUNTU Linux 14.04 LTS. I am unemployed and unable to purchase cartriges to print currently. The scanner works just fine in my Windows Partition where the developer has given software and drivers for Windows.

I have a feeling that being such an old printer it might just not be Linux friendly. 

Can you please confirm this.

Many thanks,

Mandar.

---

### Post by ajgreeny on 2015-02-25
According to [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f300_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f300_series.html) it is supported and should work fine with Ubuntu.
Check that you have hplip and hplip-gui installed and then go to HP-toolbox form your menu or just run it from terminal with command **hp-toolbox** from where you can add the AIO printer and check the configuration.

Check that you also have you also have **simple-scan** or **xsane** installed; they both should find it with no problem.

---

### Post by mandarpowale on 2015-02-25
How do I install hplip and hplip-gui from command line ?


W.R.T simple-scan or xsane :- Ok, I will do so. Thanks for your effort and time.

---

### Post by ajgreeny on 2015-02-25
You don't **need** to use the command line as you can install it the usual way with software-center or synaptic, but if you want to use command-line, just use the terminal and run command ```
sudo apt-get install hplip hplip-gui
```

---

### Post by mandarpowale on 2015-02-28
Hi 

I am unable to locate xsane from dash (unless it is a driver rather than a utility)

Hoping to hear from you soon

Mandar.

---

### Post by howefield on 2015-02-28
> **mandarpowale said:**
> I am unable to locate xsane from dash (unless it is a driver rather than a utility)

You should find Simple Scan.

---

### Post by mandarpowale on 2015-02-28
Ok Installed xsane. Found it. It blacks-out while finding the device.

Simple scan worked.

ADD : Rebooted and xsane worked.

TY.

Admin may close the thread, I don't know how to mark solved.

---

