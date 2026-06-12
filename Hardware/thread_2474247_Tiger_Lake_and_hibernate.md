---
title: "Tiger Lake and hibernate"
date: 2022-04-24
forum: Hardware
---

### Post by starkruzr2 on 2022-04-24
[COLOR=#1A1A1B][FONT=&quot]hi folks,[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]I have a GPD Pocket 3 which is a Tiger Lake mini-laptop running 22.04. as some of you probably know, there is no support for ACPI "deep" sleep on this architecture. this leaves you with s2idle (which is terrible and eats power) or hibernation to swap as suspend options.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]so, I have a swap partition active for this purpose. it is slightly larger than my full amount of RAM (18GB vs. 16GB). I have followed these instructions with the addition of updating grub and editing and updating initrd so it knows what UUID my swap partition is: [https://www.linuxandubuntu.com/home/how-to-enable-hibernate-in-ubuntu-linux#:~:text=Hibernate%20saves%20all%20of%20your,once%20you%20fulfill%20the%20requirements](https://www.linuxandubuntu.com/home/how-to-enable-hibernate-in-ubuntu-linux#:~:text=Hibernate%20saves%20all%20of%20your,once%20you%20fulfill%20the%20requirements).[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]`sudo systemctl hibernate` or `sudo pm-hibernate` will both cause the machine to appear to do a few things (not clear what, moves too fast) and then power off. sounds good so far. but when you power back on, the session is never restored.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]does anyone know how to troubleshoot this? I don't see anything useful in syslog or dmesg but can provide whatever might be helpful.

thanks![/FONT][/COLOR]

---

### Post by starkruzr2 on 2022-04-28
just bumping this in the hope someone can help.

---

