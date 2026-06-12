---
title: "Touchpad Not Working on Toshiba Satellite Laptop"
date: 2016-06-12
forum: Hardware
---

### Post by johnsonk062 on 2016-06-12
Hello everyone,

I have recently installed Ubuntu 16.04 LTS on a Toshiba Satellite L355 laptop. Currently the touchpad on the laptop does not function at all, however a USB mouse does work. 

Here is my output for xinput. 

```
user@ubuntu-laptop:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; CNF7051                                     id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=14    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=15    [slave  keyboard (3)]
user@ubuntu-laptop:~$ 
```

Please let me know what other information would be useful in helping to solve this problem.

Thank you!

---

### Post by johnsonk062 on 2016-06-17
I hate to bump threads, but I really am in need of help with this. :(

Please let me know if there is any other information you need to help with troubleshooting. Even a confirmation that this problem is a known bug waiting to be fixed, or is unsolvable, would be helpful.

Thank you.

---

### Post by howefield on 2016-06-18
First off, don't feel bad about bumping your thread, once a day is good. Sometimes that it is all it takes to catch the eye of someone with the answer.

Second, sorry I can't give you a better answer but I'd suggest searching launchpad for your issue and if no current bug is found, file one with..

```
ubuntu-bug linux
```

---

### Post by johnsonk062 on 2016-06-19
Thanks for your response howefield! :) I will look into launchpad and submit a bug if I don't find anything.

---

### Post by jeremy31 on 2016-06-19
See if ```
xinput list-props 12 | grep Enabled; synclient | grep -i touch
``` reveals anything useful

---

### Post by tareq.mhd on 2016-06-21
You can edit the grub, need to execute following commands on terminal:

> sudo gedit etc/default/grub 

Find following line in the file:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Change it as follows:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.notimeout i8042.nomux"

Now update the grub:

> sudo update-grub

Finally, reboot the system:

> reboot

Let me know the result.

---

### Post by johnsonk062 on 2016-06-21
Hi jeremy31 and tareq.mhd,

I will have access to the laptop again later this week (it belongs to belongs to my father). When I get it, I will answer both your posts. 

Thanks!

---

### Post by johnsonk062 on 2016-06-22
tareq.mhd: I followed the steps you gave to edit & update the grub, and then I rebooted, but there is still no touchpad functionality.

jeremy31: Here is my output for xinput list-props 12 | grep Enabled; synclient | grep -i touch

```
user@ubuntu-laptop:~$ xinput list-props 12 | grep Enabled; synclient | grep -i touch
    Device Enabled (153):    1
    libinput Send Events Mode Enabled (272):    0, 0
    libinput Send Events Mode Enabled Default (273):    0, 0
    libinput Horizonal Scroll Enabled (276):    0
Couldn't find synaptics properties. No synaptics driver loaded?
user@ubuntu-laptop:~$ 
```

Looks like I might be missing the synaptics driver for the touchpad?

---

### Post by johnsonk062 on 2016-06-26
Bumping to see if anyone knows what the next step should be for me from here. :)

---

### Post by johnsonk062 on 2016-07-17
Bump. Does anyone have any suggestions on what I should try next?

---

### Post by johnsonk062 on 2016-08-13
Bump. Is there anyone available to assist me with this issue?

---

### Post by jeremy31 on 2016-08-13
You may want to reverse Tarek's commands and then reboot then maybe synclient will show a result

---

### Post by irvine_himself2 on 2016-08-14
I also run Xenial Xerus on a Toshiba Satellite, and, (happily,) have no problems with my Touch pad. However, you may find these two pages useful

[http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/precise/man4/synaptics.4.html)
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Good luck 
Irvine

---

### Post by johnsonk062 on 2016-09-10
jeremy31,

I tried reversing Tarek's commands but I still get the same output from the xinput list-props 12 | grep Enabled; synclient | grep -i touch command:

```
user@ubuntu-laptop:~/Downloads/xf86-input-synaptics-1.8.2$ xinput list-props 12 | grep Enabled; synclient | grep -i touch
    Device Enabled (153):    1
    libinput Send Events Mode Enabled (272):    0, 0
    libinput Send Events Mode Enabled Default (273):    0, 0
    libinput Horizonal Scroll Enabled (276):    0
Couldn't find synaptics properties. No synaptics driver loaded?
user@ubuntu-laptop:~/Downloads/xf86-input-synaptics-1.8.2$ 
```

irvine_himself2,

Thank you for the links! I will read through them. I'm glad to hear that you are able to run Xenial Xerus without any touch pad problems on your Toshiba Satellite! It gives me hope that this problem can be fixed.

I apologize for taking so long to get back to you both. I did not receive an e-mail that this thread had been updated for some reason. :( Thank you for your responses!

---

