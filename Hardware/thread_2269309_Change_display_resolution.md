---
title: "Change display resolution"
date: 2015-03-14
forum: Hardware
---

### Post by michele-baravelli on 2015-03-14
I've installed Lubuntu 14 (last version) and now i've problem with display resolution: only 640x480!!
How could I change it? I've tried any kind of advice but nothing

---

### Post by TheBestDownloader on 2015-03-14
Same question here

---

### Post by sudodus on 2015-03-14
*Edit*: If your problem is the same as described in this link: [how to increase screen resolution on laptop]("http://ubuntuforums.org/showthread.php?t=2260082") ...
[HR][/HR]
Another easy (and cheaper) solution, that often works, is to 'uncomment' (that is remove the # character from) the line

**#GRUB_TERMINAL=console**

in the file **/etc/default/grub**

You can do it manually with an editor or with the command

```
sudo sed -i 's/#GRUB_TERMINAL=console/GRUB_TERMINAL=console/' /etc/default/grub
```

and then run the command

```
sudo update-grub
```

and reboot.

There is a more elegant way described in this sticky thread
[URL="http://ubuntuforums.org/showthread.php?t=1743535"]
Graphics Resolution- Upgrade /Blank Screen after reboot[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
[/URL]

---

### Post by michele-baravelli on 2015-03-17
Sorry for late.
Btw; it didn't work :(
alain@Dodo:~$ sudo sed -i 's/#GRUB_TERMINAL=console/GRUB_TERMINAL=console/' /etc/default/grub
[sudo] password for alain: 
alain@Dodo:~$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-31-generic
Found initrd image: /boot/initrd.img-3.16.0-31-generic
Found linux image: /boot/vmlinuz-3.16.0-23-generic
Found initrd image: /boot/initrd.img-3.16.0-23-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
alain@Dodo:~$

---

### Post by sudodus on 2015-03-18
Did you reboot? And it did not work. Then you have another problem ... Maybe you can read the following thread carefully and try
[URL="http://ubuntuforums.org/showthread.php?t=1743535"]
Graphics Resolution- Upgrade /Blank Screen after reboot[/URL]

or try according to the following wiki page

[https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens#Sometimes_it_takes_real_tweaking_to_solve_the_problem](https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens#Sometimes_it_takes_real_tweaking_to_solve_the_problem)
[URL="https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens"]


[/URL]

---

### Post by michele-baravelli on 2015-03-19
Thx a lot for helping, it's solved!!

---

### Post by sudodus on 2015-03-19
Congratulations :KS

***Please tell us which solution works for you***, and please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

---

