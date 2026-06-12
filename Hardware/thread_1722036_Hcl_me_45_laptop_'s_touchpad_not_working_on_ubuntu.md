---
title: "Hcl me 45 laptop 's touchpad not working on ubuntu 10.10"
date: 2011-04-05
forum: Hardware
---

### Post by Anirwan on 2011-04-05
I have HCL ME 45 LAPTOP with multi gesture touchpad. Earlier i was using only windows 7 ultimate. Four days earlier, i installed ubuntu 10.10. On and after installing ubuntu 10.10, i found that my touchpad is not working. From four days i was struggling with this problem, but cannot succeded in solving the problem. I would be very thankfull to the person for helping me solving this problem. Also, i would like to know how to use webcam in ubuntu 10.10.

---

### Post by soni_nidhi on 2011-05-24
> **Anirwan said:**
> I have HCL ME 45 LAPTOP with multi gesture touchpad. Earlier i was using only windows 7 ultimate. Four days earlier, i installed ubuntu 10.10. On and after installing ubuntu 10.10, i found that my touchpad is not working. From four days i was struggling with this problem, but cannot succeded in solving the problem. I would be very thankfull to the person for helping me solving this problem. Also, i would like to know how to use webcam in ubuntu 10.10.
 
 
I m also struggling with the same problem. can u please tell me the solution.

---

### Post by Anirwan on 2012-07-09
[SIZE=3]Finally, i got the solution of my[/SIZE] [SIZE=3]touchpad not working problem in Ubuntu 12.04. I found this on [http://ubuntuforums.org/showthread.php?t=1976313](http://ubuntuforums.org/showthread.php?t=1976313). Also, this [http://ubuntuforums.org/showpost.php?p=5290024&postcount=1](http://ubuntuforums.org/showpost.php?p=5290024&postcount=1) helped me a lot. The solution is:-[/SIZE]
[SIZE=3]
[/SIZE]First, open the terminal (Shortcut: Ctrl+Alt+T) 
Then, type:
```
 gksudo gedit /etc/default/grub 
```and change the line 
from: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux=1 i8042.noloop=1"  
Then, save the file.
Close the file. 
Then in the terminal type :
```
 sudo update-grub 
``` 
Lastly, Reboot.

---

