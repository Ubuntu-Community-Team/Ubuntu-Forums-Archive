---
title: "Resuming from Suspend problems in Ubuntu 11.04"
date: 2011-06-18
forum: Hardware
---

### Post by videoclocknet on 2011-06-18
Hey guys!

I've been hearing that there are a lot of people who have problems in resume from suspend in Ubuntu 11.04. I've got to solve it!

This post is for you if:
You use Ubuntu 11.04. You suspend correctly, but when you press a key or the shutdown button to resume, the screen remains blank and the fan "on".


What I've done:

1.- Boot from Ubuntu 11.04 LIVE CD.
2.- copy recursively the /etc/acpi folder (of the LIVE CD) into a pendrive.
3.- Shutdown your computer
4.- Boot from your usual Ubuntu 11.04
5.- rename your /etc/acpi of your hard drive to /etc/acpi-old
6.- copy recursively your /etc/acpi folder of your pendrive to your /etc of your hard drive
7.- Change permissions recursively of all /etc/acpi files and folders of your hard drive to be read and executed by an usual user
8.- Shutdown your computer
9.- Boot your usual Ubuntu 11.04 and then you can already suspend and resume from suspend!

Do these steps at your own risk! I'm not responsible of any damage it can cause to you!
If after following these steps it doesn't work for you:
1.- Boot from the Ubuntu 11.04 LIVE CD
2.- remove the /etc/acpi folder of your hard drive
3.- rename /etc/acpi-old to /etc/acpi
4.- Shutdown your computer
5.- Boot your usual Ubuntu 11.04

It works for me. I don't know if it will for you. Anyway, opinions are welcome!

Bye bye!

---

