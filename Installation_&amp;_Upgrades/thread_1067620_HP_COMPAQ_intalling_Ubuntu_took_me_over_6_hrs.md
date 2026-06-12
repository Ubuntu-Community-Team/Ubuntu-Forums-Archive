---
title: "HP COMPAQ intalling Ubuntu took me over 6 hrs"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by m-k-m on 2009-02-12
Hello

I have a HP Compaq laptop, Sempron 3800, 2 GB RAM, 160 GB HDD. When I install Ubuntu 8.10 it takes more then 6 hrs to do so, and when it's installed it works wery slow.

I can install Windows normally, and I can install Ubuntu in VMWare Server normally under Windows, but when I install Ubuntu 8.10 as primary and only OS on the computer - read the first paragraph :D

Can anyone help me??? someone???

thanx and greetings,

matko

p.s.: I have the same problem when I install Centos 5.2. I didn't try to install other distributions.

Does this laptop hate linux !!!??? :D

---

### Post by cb951303 on 2009-02-12
Only thing I can think of is a faulty hard drive.
Almost all harddisk vendors provide diagnostic live cds to see if your harddisk is damaged or not working properly. You might want to try that.

---

### Post by m-k-m on 2009-02-12
Hello

How come, that I can install Windows normaly if the HDD is faulty?

I'm gonna try to check the HDD.

thanx

matko

---

### Post by prshah on 2009-02-12
> **m-k-m said:**
> 
I'm gonna try to check the HDD.


From your (slow) ubuntu, open a terminal (Applications-Accessories-Terminal) and give the command```
dmesg | grep -i drdy
``` if this shows any output, please post the output here; there are a couple of possible solutions if this is the problem.

If this comes back blank, then the HDD is possibly not the problem.

You can try turning off detecting of ACPI features, but this is not a step I recommend.

Post back if you need more information,

---

### Post by jrusso2 on 2009-02-12
> **m-k-m said:**
> Hello

How come, that I can install Windows normaly if the HDD is faulty?

I'm gonna try to check the HDD.

thanx

matko

I don't think it is.  I think its a driver probably video.  What video card do you use?

---

### Post by cb951303 on 2009-02-12
> **m-k-m said:**
> Hello

How come, that I can install Windows normaly if the HDD is faulty?

I'm gonna try to check the HDD.

thanx

matko

it may happen. for example, I had a hdd with S.M.A.R.T messed up. Windows never complained anything about it. it didn't even slow down. But I couldn't install a linux on it because it gave me all sorts of error while installing. And I didn't know that my hdd was messed up until I tried to install linux and run a diagnostic live cd on it :)

---

### Post by cb951303 on 2009-02-12
> **jrusso2 said:**
> I don't think it is.  I think its a driver probably video.  What video card do you use?

video driver has nothing to do with install time?

---

### Post by m-k-m on 2009-02-12
dmesg | grep -i drdy

shows no output.

So what should I do to test the disk or whatever may be tested???

I have Hiren's Boot CD and Microscope v.12, even BIOS has some options to check the disk.

should I enable/disable anything in BIOS???

thanx

matko

---

### Post by cb951303 on 2009-02-12
> **m-k-m said:**
> dmesg | grep -i drdy

shows no output.

So what should I do to test the disk or whatever may be tested???

I have Hiren's Boot CD and Microscope v.12, even BIOS has some options to check the disk.

should I enable/disable anything in BIOS???

thanx

matko

what's your harddisk brand and model?

---

### Post by m-k-m on 2009-02-12
HDD - Toshiba MK1637GSX, Disk Drive HDD2D60 F ZL01 S, 160GB - is this enough?

---

### Post by prshah on 2009-02-12
> **m-k-m said:**
> dmesg | grep -i drdy
shows no output.


Then I doubt that there's anything wrong with the disk. Any disk problems (including errors in logical structure) cause an unexpected break in data flow, generating a DRDY error or emask exception. In fact, you can try the below command for further confirmation (blank output means nothing wrong with your HDD)```
dmesg | grep -i emask
```

Take a look at [this post]("http://ubuntuforums.org/showpost.php?p=5723442&postcount=23") for information on how to use alternative ACPI and related troubleshooting options.

---

### Post by cb951303 on 2009-02-12
Apparently toshiba is the only hard disk manufacturer that doesn't provide a diagnostic tool :)
> 
Toshiba does not provide diagnostic tools for hard drives, currently.

Hard Disk Drives and Optical Disk Drives purchased as part of a complete system are warranted by the system OEM. Please contact your system manufacturer for further details. 2.5" Hard Disk Drive ("HDD") products purchased in the United States and Canada from Toshiba authorized distributors carry a 3-year limited warranty. 1.8" Hard Disk Drive ("HDD") products purchased in the United States and Canada from Toshiba authorized distributors carry a 1-year limited warranty. Optical Disk Drive("ODD") products purchased in the United States and Canada from Toshiba authorized distributors carry a 1-year limited warranty. Toshiba's USB 2.0 Portable External Hard Drive carries a 1-year limited warranty. Click here for additional information.

Luckily, Hitachi DFT works for Toshiba drives. Here is the link: [http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

Unluckily, prshah is probably right and your hdd is fine. no harm in trying the diagnostic though.

---

### Post by |{urse on 2009-02-12
there are so many things this could be, not just hdd. please run this command after a normal boot.

touch log && dmesg | more  > log   

(it's gonna be a LOT of stuff)

please attach the "log" file to a post (with the little paperclip icon) and post it up for us so we can troubleshoot.

---

### Post by m-k-m on 2009-02-19
Hello

OK here's the stuff I got this far. One guy suggested me to do this:
when the CD boots and I press f6 and write following:
NOACPI ACPI=OFF NOAPIC IDE=NODMA
everything goes normal - the whole installation and linux boot and usage.

Any ideas what this stuff do - does it harm the computer HDD etc?

thanx

matko

---

