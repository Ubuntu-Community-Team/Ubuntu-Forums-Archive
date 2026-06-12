---
title: "laptop reboots after after suspend."
date: 2010-08-20
forum: Hardware
---

### Post by ppp0 on 2010-08-20
Hello ubuntu guys!
So what is my problem:
When i close lid of my sony vaio fw31e it suspends.
But when i open lid - it boots like i turned it off.
And when it is in suspend mode info led is blinking.
Where should i dig to fix this problem?
Ah, my ubuntu is LucidLynx 10.04.

---

### Post by thongstele on 2010-11-13
I have the same problem with my Vaio FW190E in Ubuntu 10.10. Though in Ubuntu 10.4, it works good, no problem with suspend or hibernate mode. 

When i close lid (or choose suspend menu) the latop turns to suspend mode completely (as normal), but when I open lid and press any key (or press any key in case of choosing suspend menu), Ubuntu reboots (of course existing programs disappear). 

I search via a lots websites but there isn't any solution to end problem.
Anyboby know the good way, please tell me.

Thx in advance!

---

### Post by ppp0 on 2010-11-13
> **thongstele said:**
> I have the same problem with my Vaio FW190E in Ubuntu 10.10. Though in Ubuntu 10.4, it works good, no problem with suspend or hibernate mode. 

When i close lid (or choose suspend menu) the latop turns to suspend mode completely (as normal), but when I open lid and press any key (or press any key in case of choosing suspend menu), Ubuntu reboots (of course existing programs disappear). 

I search via a lots websites but there isn't any solution to end problem.
Anyboby know the good way, please tell me.

Thx in advance!

yeah yeah! same thing i've searched too but with no result and in 10.04 it ok with suspend. I think we need to write this story to launchpad.

---

### Post by salamanderjoe on 2010-12-02
Hi everyone,

I found a solution for that exact same problem that works perfectly on my Vaio VGN-FW-54J

The source is in German, but I'll explain it in English in here as well:
[http://forum.ubuntuusers.de/topic/ubuntu-10-10-reboot-nach-dem-verlassen-der-ber/#post-2648317](http://forum.ubuntuusers.de/topic/ubuntu-10-10-reboot-nach-dem-verlassen-der-ber/#post-2648317)

You just have to edit the /etc/grub/default file as root (for example by entering ```
sudo gedit /etc/grub/default 
```
)
and after that look up the line where it says:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Change that to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs"
```

After that, save the file and close it.

Then, you have to tell GRUB (the bootloader) to update to the new configuration. You can do that by entering
```
sudo update-grub
```

After that, reboot and enjoy!

---

### Post by ppp0 on 2010-12-04
> **salamanderjoe said:**
> Hi everyone,

I found a solution for that exact same problem that works perfectly on my Vaio VGN-FW-54J

The source is in German, but I'll explain it in English in here as well:
[http://forum.ubuntuusers.de/topic/ubuntu-10-10-reboot-nach-dem-verlassen-der-ber/#post-2648317](http://forum.ubuntuusers.de/topic/ubuntu-10-10-reboot-nach-dem-verlassen-der-ber/#post-2648317)

You just have to edit the /etc/grub/default file as root (for example by entering ```
sudo gedit /etc/grub/default 
```
)
and after that look up the line where it says:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Change that to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs"
```

After that, save the file and close it.

Then, you have to tell GRUB (the bootloader) to update to the new configuration. You can do that by entering
```
sudo update-grub
```

After that, reboot and enjoy!

Yeash man it works fro VGN-FW31E works! WORKS!!

---

### Post by XProflmfao on 2011-03-19
> **salamanderjoe said:**
> Hi everyone,

I found a solution for that exact same problem that works perfectly on my Vaio VGN-FW-54J

The source is in German, but I'll explain it in English in here as well:
[http://forum.ubuntuusers.de/topic/ubuntu-10-10-reboot-nach-dem-verlassen-der-ber/#post-2648317](http://forum.ubuntuusers.de/topic/ubuntu-10-10-reboot-nach-dem-verlassen-der-ber/#post-2648317)

You just have to edit the /etc/grub/default file as root (for example by entering ```
sudo gedit /etc/grub/default 
```
)
and after that look up the line where it says:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Change that to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs"
```

After that, save the file and close it.

Then, you have to tell GRUB (the bootloader) to update to the new configuration. You can do that by entering
```
sudo update-grub
```

After that, reboot and enjoy!

Oh my gosh! I have had this problem for a while, only today did I actually have time to search for a solution, and so far only your solution has worked for my Sony VGN-NS140E!! Thank you so much. :o:D:P

---

### Post by moranjk on 2011-05-15
> **salamanderjoe said:**
> Hi everyone,

I found a solution for that exact same problem that works perfectly on my Vaio VGN-FW-54J

The source is in German, but I'll explain it in English in here as well:
[http://forum.ubuntuusers.de/topic/ubuntu-10-10-reboot-nach-dem-verlassen-der-ber/#post-2648317](http://forum.ubuntuusers.de/topic/ubuntu-10-10-reboot-nach-dem-verlassen-der-ber/#post-2648317)

You just have to edit the /etc/grub/default file as root (for example by entering ```
sudo gedit /etc/grub/default 
```
)
and after that look up the line where it says:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Change that to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs"
```

After that, save the file and close it.

Then, you have to tell GRUB (the bootloader) to update to the new configuration. You can do that by entering
```
sudo update-grub
```

After that, reboot and enjoy!

Works great on my Vaio VGN-FW530J with Natty!! One slight difference though, the file was /etc/default/grub 
**Example:**
```
sudo gedit /etc/default/grub
```

---

### Post by andycastille on 2012-03-04
Thanks! I also had this problem and it fixed it perfectly! :)

---

