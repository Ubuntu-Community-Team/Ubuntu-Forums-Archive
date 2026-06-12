---
title: "Brightness cant be adjusted on Gateway NV44"
date: 2010-12-21
forum: Hardware
---

### Post by arpanchavdaeng on 2010-12-21
hi....
My problem is that i have Ubuntu 10.10 on my gateway NV44 laptop and also windows 7.
"In UBUNTU 10.10...Brightness of my laptop screen does not decrease by pressing fn+down arrow key and same does not increase.....
my laptop contain an Intel Graphics Media Accelerator
4500M.
I want to say that when i press fn+down arrow key to decrease
brightness of screen...on the top right corner...the bar of brightness displayed and that bar decrease but originally the brightness of screen does not decrease means i cant adjust  brightness of screen by using these key and also not from power manager in Ubuntu....
Plz help...
Thanx a lot in advance .....

---

### Post by kingsley404 on 2010-12-26
i have this same problem if someone could fix this that would be helpful

---

### Post by rlara333 on 2010-12-27
Please let us know the details of your computer; what chipset, cpu, and graphics card you have etc...

---

### Post by arpanchavdaeng on 2011-03-01
RAM : 2 GB
Processor : Intel dual core T4200
HDD : 250 GB
Chipset : Intel mobile chip set series 4
Graphics : Integrated Intel GMA 4500

---

### Post by ceferele on 2011-06-24
Same problem in Gateway NV55C and neither haven't found anybody with the knowledge in the community with interest in solving it.

Saludos desde Perú.

---

### Post by Toz on 2011-06-24
Do you have the same problem where the brightness keys show a change but no actual brightness change is taking place?

Have you tried the kernel parameter **acpi_backlight=vendor**? See [https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot") for instructions on how to test this kernel parameter.

If that doesn't work, what does the following command return?```
cat /sys/class/backlight/acpi_video0/brightness
```(You'll need to run this command from a terminal prompt)

If you get an error message, then try and post back results:```
ls /sys/class/backlight
```

---

### Post by arpanchavdaeng on 2011-06-30
First command gives the levels of brightness...like 8,6,0....but fail to change in original brightness...second command gives " acpi_video0"...Thanx for reply

---

### Post by Toz on 2011-06-30
Did you try booting with the **acpi_backlight=vendor** kernel parameter as suggested in post #6? Does it fix the brightness issue?

---

### Post by arpanchavdaeng on 2011-07-02
" acpi_backlight=vendor " doesnt solve this issue...Plz help..

---

### Post by Toz on 2011-07-02
Try also booting with kernel parameter **acpi_osi=**. 

If that doesn't work, can you try:
1. ```
lspci | grep VGA | cut -d' ' -f1
```

2. Try implementing the script from [http://ubuntuforums.org/showpost.php?p=10926719&postcount=6]("http://ubuntuforums.org/showpost.php?p=10926719&postcount=6"). The only change you may need to make to the script is the **setpci** command towards the end, if the result of the previous command was not **00:02.0**

---

### Post by arpanchavdaeng on 2011-07-05
That script works for me....Thank YOU...VERY...VERY>>>MUCH...):P

---

### Post by Toz on 2011-07-05
Glad to hear and thanks for reporting back. If you don't mind, can you flag this thread as solved using the "Thread Tools" link above?

---

