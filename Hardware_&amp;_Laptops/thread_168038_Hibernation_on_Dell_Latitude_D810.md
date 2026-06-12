---
title: "Hibernation on Dell Latitude D810"
date: 2006-04-29
forum: Hardware &amp; Laptops
---

### Post by hermit on 2006-04-29
Friends,
It's probably been discussed a thousand times, but I can't get my D810
to hibernate (suspend to disk) under Breezy no matter what I do. I've been over
the forums and Google'd endlessly, tried every configuration step and
advice I've found but nothing has worked for me.

Actually, hibernation seems to work but the machine invariably freezes coming out of it on restore.

Can someone either tell me what the required steps are or point me to a
working How-To or writeup ? It'd be best if I can get it working with the ATI binary drivers, but would be willing to try the xorg ATI drivers if they now work for hibernation. I DO NOT need 3D acceleration but having hibernation is VERY important for the way I use my machine.

My video card is the Ati Radeon x600 Mobility w/128 MB memory and this screen is the WUXGA with a 1920 x 1200 res.

Thanks for all input and advice ...

hermit

---

### Post by snipe122 on 2006-04-29
try kernel-options:

resume=/dev/hdaX nolapic noapic

X=your swap partition


I recently fixed hibernation on my satellite after a long time :) now Im happy! lots of probs with hibernating come because of wrong implimentation of acpi in the bioses... like in my satellite...

hope it works!

greets
snipe

---

### Post by hermit on 2006-04-29
Thank you for your suggestion, Snipe. I tried it but unfortunately it didn't work on this machine.
I then read even more on past trials and tried one that was similar, adding to that same line:
'reboot=h'
Strange! this actually worked ONE time but then didn't work on successive attempts.

If anyone has any further ideas, advice or suggestion I will gladly try them. For certain some people have been able to get hibernation working on similar D810 machines with the Ati x600 Radeon card and the same generic driver.

Advance thanks to anyone willing to help,

hermit

---

### Post by snipe122 on 2006-04-30
how do you try to send your comp to hibernation?

echo 4 > /proc/acpi/sleep (which I used)

echo disk > /sys/power/state

hibernate (the hibernate script)


Did you try to patch suspend2 into your kernel? I tried but I had no success cause Im not so common with kernel-things... maybe you are...

---

### Post by hermit on 2006-04-30
I have just attempted to utilize the suggestions made by Snipe. None of them worked on my setup. I am running Breezy Badger with the Gnome desktop. Here is what I got at the terminal (note that yd is my name, Clearsky is the computer and in these cases, when I used sudo, I was not even asked for my password) Neither "which" nor "whereis" yielded any knowledge of a 'hibernate' command:
~~~~~~~~~~~~~~~~
yd@Clearsky:~$ echo 4 > /proc/acpi/sleep
bash: /proc/acpi/sleep: Permission denied
yd@Clearsky:~$ sudo echo 4 > /proc/acpi/sleep
bash: /proc/acpi/sleep: Permission denied
yd@Clearsky:~$ sudo echo 4 > /proc/acpi/sleep
bash: /proc/acpi/sleep: Permission denied
yd@Clearsky:~$ ls /proc/acpi/sleep
/proc/acpi/sleep
yd@Clearsky:~$ cat /proc/acpi/sleep
S0 S3 S4 S4bios S5
yd@Clearsky:~$ sudo echo disk > /sys/power/state
bash: /sys/power/state: Permission denied
yd@Clearsky:~$ which hibernate
yd@Clearsky:~$ whereis hibernate
hibernate:
yd@Clearsky:~$

~~~~~~~~~~~~~~~~~
You asked how I attempt hibernation (suspend to disk). I use the GUI to log out and have the options to Log Out; Shut Down; Reboot; Suspend (i.e. to ram); and Hibernate.
I would chose Hibernate, which the computer seems to do successfully. It is when I attempt to boot that it hangs. I then shut off the machine and reboot normally.

Advanced thanks from this newbie to anyone willing to offer any suggestions that might help,

hermit

---

### Post by snipe122 on 2006-04-30
try to logout from your session. In the login screen, press ctrl + F1.

Now youll see a non graphical interface.

login as root with you root password.

type /etc/init.d/gdm stop (to stop gnome)

then type echo 4 > /proc/acpi/sleep.

I dont think this works with sudo, I think you have to be root.


greets
snipe

---

### Post by hermit on 2006-04-30
I just the suggestion from Snipe. First logged in to the terminal (Ctrl + Alt + F1) and stopped the Gnome interface successfully.

When I typed:
'echo 4 > /proc/acpi/sleep'
I got exactly the same as from the terminal after having logged in via Gnome. It once again read:
'bash: /proc/acpi/sleep: Permission denied'

Could there be something wrong, either with the command or with my setup?

sadly,
hermit

---

### Post by snipe122 on 2006-04-30
thats really strange to get a permission denied as root ... its like impossible :) someone a suggestion? maybe thats why it doesnt work on your machine cause the graphical "hibernate-button" does not print out failure messages... so you cant see whats wrong... maybe now you have a hint... you have to get around the rights-problem... dont know why that is on your comp, I can do without probs...

g'night
snipe

---

