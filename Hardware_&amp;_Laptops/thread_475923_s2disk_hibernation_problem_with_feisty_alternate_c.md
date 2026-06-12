---
title: "s2disk /hibernation problem with feisty alternate cd - uswusp"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by szymon_g on 2007-06-16
hi.
i've got acer aspire 5685.
i've installed ubuntu feisty fawn, from alternate cd and i've installed xfce4.
i've downloaded and installed uswsusp program. i've got no idea how can i setup suspend-to-disk ; when i'm typing 

sudo s2disk 

i get

szymon@linugrat:~$ sudo s2disk -f
suspend: Could not stat the resume device file
szymon@linugrat:~$ 

all the time.

when i've installed it, i made sudo s2disk -f and it saved an image into my swap partitnion. 
but when i've turn computer on, i get only a blank screen.
when i restarted computer, it had no swap partition, so i re-create it (by editing /etc/fstab and putting 'true' /dev addres instead of uuid-something in swaps line)

i've readed this thread

[http://ubuntuforums.org/showthread.php?t=194426&page=2](http://ubuntuforums.org/showthread.php?t=194426&page=2)

in answer nr 19 is explained how to solve this problem, but... i have no /etc/acpi/sleep.sh (i've got only /events folder and powerbt.sh script)

it also didn't helped me

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

my kernel is 2.6.20-15-generic

---

