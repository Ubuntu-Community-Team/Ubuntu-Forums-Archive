---
title: "pcspkr module on laptop"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by irsic on 2006-11-25
Hi,
I have a bit of a problem with my pc speaker. I use ubuntu dapper linux.
When I have in bash script written
echo -e "\a"
there is no sound just new line.
also for
echo -e $'\a'
I also tried a C program with
printf("\a");
and still there is no sound.
But when I type command
lsmod | grep 'pcspkr'
I get
pcspkr                  2180  0
In my terminal on Gnome I have Terminal bell checked.
then I also repeated all tests for beep in console (Ctrl-Alt-F2)
and still nothing.
Does anybody have any clue what might have I done wrong?
Thanks

---

### Post by Jason Quinn on 2007-10-25
Same problem (Dell Inspiron 1720) on 64bit Kubuntu 7.10

---

