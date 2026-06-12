---
title: "screen Brightness ste to 0% upon log in in HP G62"
date: 2012-05-03
forum: Hardware
---

### Post by czeem86 on 2012-05-03
[SIZE=2]hello everybody,
i have HP G62 a20SE Notebook with double graphic cards: Intel and ATI
the ATI does not work but this is not a big problem for me now
the main problem is that when the Ubuntu 12.04 starts up and reaches the login screen the brightness goes off and i can feel that everything is just working and i can't see anything anymore!
but when i login to the safe mode settings (recovery mode) it work fine and i notice that the brightness is set to 0% and although i keep changing it it still goes back every time to 0%

could somebody please help me?

thanks in advance
[/SIZE]

---

### Post by czeem86 on 2012-05-04
Solved:


a friend has helped me to solve this

so i want to share the solution with others that might have the same issue:

type in the terminal:

sudo sed "s/\(GRUB_CMDLINE_LINUX=\)\"\"/\1\"acpi_osi=Linux acpi_backlight=vendor\"/" /etc/default/grub -i 
then type:

sudo update-grub

then type:

sudo reboot



hopefully it will work

best wishes

---

### Post by cmcanulty on 2012-05-06
works on HP G72t thank you!!!Can you explain that command I wonder what it does and how

---

### Post by anoopp on 2012-05-12
Thanks a lot. It resolved the same issue with HP 630 and Ubuntu 12.04 :p

---

### Post by vinmar on 2012-07-05
This fixed blank screen at login on my HP G6, thanks for posting back with the solution!

---

### Post by Dunpostin on 2012-07-22
Worked for me also.Had same problem on HP Pavilion G4. I'm also wondering what exactly that command does.

---

### Post by Toz on 2012-07-22
**acpi_osi=Linux** - sometimes a bios will disable functionality if Windows is not detected. This command forces it to use all functionality.

**acpi_backlight=vendor** - tells the kernel to use a vendor specific acpi driver (e.g.. sony_acpi, thinkpad_acpi) instead of the default video module. Helps in fixing backlight issues in some cases.

---

### Post by gerrygprs on 2012-08-30
> **czeem86 said:**
> Solved:


a friend has helped me to solve this

so i want to share the solution with others that might have the same issue:

type in the terminal:

sudo sed "s/\(GRUB_CMDLINE_LINUX=\)\"\"/\1\"acpi_osi=Linux acpi_backlight=vendor\"/" /etc/default/grub -i 
then type:

sudo update-grub

then type:

sudo reboot



hopefully it will work

best wishes



Thank you. This worked for HP 630 laptop. Running Ubuntu 12.04

---

### Post by kevmehv on 2013-02-27
> **czeem86 said:**
> Solved:


a friend has helped me to solve this

so i want to share the solution with others that might have the same issue:

type in the terminal:

sudo sed "s/\(GRUB_CMDLINE_LINUX=\)\"\"/\1\"acpi_osi=Linux acpi_backlight=vendor\"/" /etc/default/grub -i 
then type:

sudo update-grub

then type:

sudo reboot



hopefully it will work

best wishes


I came across this solution and it worked (kinda).  But I do have a problem...

After applying this solution my laptop now loads at what appears to be 50% screen brightness, which is much better than the default of 0% that I was experiencing before.  BUT now I've lost brightness controls all together!  It loads at about 50% brightness but stays there.  When I go into the brightness settings and try to adjust the brightness I'm able to move the slider but the screen does not change brightness levels, but it used to before I applied the solution.

Any ideas??

Ps.  I've spent the last couple of house digging through the web for a solution but none of them worked for me.  So I'm hoping someone here can help :D

Acer One 200 series, Ubuntu 12.04

---

### Post by AshNova on 2013-04-30
> **czeem86 said:**
> Solved:


a friend has helped me to solve this

so i want to share the solution with others that might have the same issue:

type in the terminal:

sudo sed "s/\(GRUB_CMDLINE_LINUX=\)\"\"/\1\"acpi_osi=Linux acpi_backlight=vendor\"/" /etc/default/grub -i 
then type:

sudo update-grub

then type:

sudo reboot



hopefully it will work

best wishes

This worked for me on HP dv6 3032tx running 12.04.2 64 bit with Kernel Linux 3.5.0-27-generic.

Thank you.

But now the brightness keys don't work.

However that doesn't matter as I always use it at max brightness :)

---

### Post by czeem86 on 2013-09-08
Hallo everyone
I'm trying to install the new version of Ubuntu using a boot CD and upod starting the install the screen goes black :((
could somebody please help?

---

### Post by ScumCoder on 2013-12-25
> **czeem86 said:**
> Hallo everyone
I'm trying to install the new version of Ubuntu using a boot CD and upod starting the install the screen goes black :((
could somebody please help?
I had the same issue on my Acer P3-171 with every Linux distro, including Ubuntu. In the end I just connected an external display via HDMI.

---

### Post by cmcanulty on 2013-12-25
i had to set nomodeset on the install, need somebody better to explain it though as I forget

---

