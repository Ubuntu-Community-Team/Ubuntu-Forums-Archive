---
title: "acpi power_off called"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by Jst on 2006-01-12
Actually I have problems with my Debian, but I was hoping someone here could help me. Well the thing goes like this, when I want to shut down my computer it doesnt't power off automatically, it just says *acpi power_off called* and nothing else happens. Then I have to push the power off button. But it works with ubuntu. It says *acpi power_off called* and then shuts down. Why is it that it works with Ubuntu, but it wont in Debian.

---

### Post by _Phil on 2006-12-06
Same problem here. But my pc doesnt power off shutting down Ubuntu but in Debian it works for me. On my Laptop also running ubuntu (dapper both) it powers off without problems.

Any suggestions? Thx

---

### Post by Jst on 2006-12-12
It's not working in Ubuntu anymore for me either. It did with dapper but it won't with Edgy.

Now here's what I did. I basically dumped acpi and use apm instead. I still miss acpi because now I can't just press the power button and wait for the computer to shut down. If I do that now the computer just shuts down instantly(no logging off, no stopping daemons, no nothing)so I have to tell it to shut down from the program. But at least it shuts down properly.
This however worked in dapper just fine. You pressed the power button and waited for the computer to power down.

Anyhow here's what you do.

in */boot/grub/menu.lst* find the section that looks something like this

```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=38fcf910-dcd9-43e8-983c-dc62adfee781 ro
# kopt_2_6=root=/dev/hda2 ro
```

now add "*acpi=off*"(no quotation marks) to the last line so it looks somethin like:

```
# kopt_2_6=root=/dev/hda2 ro acpi=off
```

Note: Don't edit anything else, just add *acpi=off*. Your lines are probably a bit different from mine.
Note 2: Leave *#* there, it's supposed to be there


And add a line "*apm power_off=1*" in */etc/modules*



Hope it helps.

---

### Post by Jst on 2006-12-14
OK forgot one thing. After u edit */boot/grub/menu.lst* run "*sudo update-grub*" so the changes have effect.

---

