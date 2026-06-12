---
title: "lenovo G580 brightness control not working in ubuntu 12.04"
date: 2012-09-23
forum: Hardware
---

### Post by debashisgho on 2012-09-23
I recently purchased a lenovo G580 laptop. It does not have a separate graphics card. 
I also installed ubuntu and windows 7 64 bit . Lenovo provided a driver cd for windows 7. I installed all the drivers. The lenovo FN+up and down brightness control works fine in windows 7.  But it does not work in Ubuntu. When I press the key combination, the brightness control appears and it shows the brightness is decreasing or increasing, but actually nothing happens. As i am new to linux, I did some search in the forums and found out two solution. 
 1. changing the etc/default/grub file to modify the entry
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=video" 
2. changing the XOrg.conf file (which does not even exist in ubuntu 12.04)

None of these worked for me. If you experts have any known solution, please share it with me. 

Thanks.

---

### Post by Toz on 2012-09-28
Hello and welcome to the forums.

What kind of video card do you have? Try opening a terminal, running this command and posting back the results:
```
lspci  | grep VGA
```

You may want to try the following kernel parameters instead of "acpi_backlight=video":

- acpi_backlight=vendor
- acpi_osi=
- acpi_osi=Linux
(Try them one at a time)

And remember, that after everytime you change /etc/default/grub, you need to run:
```
sudo update-grub
```

---

### Post by Berundo on 2012-10-03
I also had the same problem with my G580. Here's the method to make brightness work:
Add ```
acpi_backlight=vendor
``` to the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and then **reboot**.

---

### Post by Toz on 2012-10-03
> **Berundo said:**
> I also had the same problem with my G580. Here's the method to make brightness work:
Add ```
acpi_backlight=vendor
``` to the ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and then **reboot**.

Hello Berundo and welcome to the forums. If I may make one addition to your solution, you also need to run:
```
sudo update-grub
```
...to make it work.

---

### Post by Berundo on 2012-10-05
> **Toz said:**
> Hello Berundo and welcome to the forums. If I may make one addition to your solution, you also need to run:
```
sudo update-grub
```...to make it work.
Yes, of course. I forgot to mention about it :). Thanks.

---

### Post by Rifester on 2012-12-29
Sorry to re-open an older thread, but I just purchased this laptop and have been working to get everything functional.   I couldn't get the brightness control to work.    

GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor"s followed by a grub update fixed this!

Fixed the problem for me!   Thank you very much!   Since the OP didn't mark this thread as solved, I will state this is the fix.

Thank you!


00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)

---

### Post by amon2 on 2013-10-10
[COLOR=#000000]Awesome,
After huge hassle, finally.... This solution was life saver. (almost lost brightness sensor of my EYES.... :)
Step 1 : Edit [/COLOR][COLOR=#000000]/etc/default/grub to update with following,[/COLOR][COLOR=#000000]
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor" 
Step 2: Hit this command form terminal 
[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo update-grub
[/FONT][/COLOR][COLOR=#000000]
and voilaa! its fixed!
[/COLOR]
P.S: I am using Mint 15 64 bit and Lenovo G580

[COLOR=#000000]Fixed the problem for me! Thank you very much! 
[/COLOR]
-Amon

[COLOR=#000000]Thank you![/COLOR]

---

