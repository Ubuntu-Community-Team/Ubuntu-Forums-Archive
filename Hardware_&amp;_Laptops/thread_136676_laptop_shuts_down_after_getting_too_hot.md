---
title: "laptop shuts down after getting too hot"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by kybishop on 2006-02-26
I have a compaq armada 1750 (old i know) and it will shut down randomly

I get something like the following message

The system is shutting down NOW
blah blah critical temperature 97 C


So, is it getting too hot and shutting down?
If so, how can I stop it from getting so hot.

I've even cut off the grates near the fans to see if it would help, no luck.

---

### Post by localzuk on 2006-02-26
The usual cause of laptop overheating is fluff in the exhaust vent fans. Try removing any fans and giving them a clean.

---

### Post by kybishop on 2006-02-26
Found out the cause of the problem with some research. The fan doesn't stay on as much as required with ACPI enabled on my model laptop.

Solution: turn on APM

How-to: basically no idea

So here's where i need some serious help.

I've heard I need to rebuild my own custom kernel (i hope not)

Well, if i do have to rebuild my own kernel, could someone show me how, in an idiot proof way (type this, now this, now this, now this).

If I go through with all this, and get my own kernel, will I be stuck with not being able to update it if a new kernel comes out?

---

### Post by kybishop on 2006-02-26
okay so i got apm to work through the grub boot loader, now i have a new problem.


when the computer starts up, i get an error message that says

FATAL: Error inserting thermal (/lib/modules/2.6.12-9 default/kernel/drivers/acpi/thermal.ko): No such device
FATAL: Error inserting fan (/lib/modules/2.6.12-9 default/kernel/drivers/acpi/fan.ko): No such device

soooooo . . . what the heck does that mean
also it sounds like my fan isn't on, which isn't good

---

### Post by Proleter on 2006-02-26
Hey how did you managed doing that. I had the same problem with medion Athlon XP-m. But I thought that the problem is with my computer. It doesn't writes any message but my computer shuts down imediately. Specialy when the processor usage is high for long time(10-15minutes).
I have 32 MB S3 Graphic Card.

---

### Post by Vorian on 2006-02-26
Ubuntu lite may be a better fit for your machine.

---

### Post by kybishop on 2006-02-26
first, make sure acpi is turned off in your BIOS

after that, when GRUB loads up and asks you to choose a kernel, press e on the one you usually boot with

then go to the command that starts with kernel

press e

add to the end of the command:
acpi=off apm=on

press escape

press b, you have to do it every time you boot your computer, im sure there is a way to set it as default, but i don't know how

---

### Post by kybishop on 2006-02-26
is ubuntu lite more laptop orientated?

does it have more apm support?

tell me about this ubuntu-lite :-D

---

### Post by Vorian on 2006-02-26
check this thread...

[http://www.ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu+lite](http://www.ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu+lite)

---

### Post by kybishop on 2006-02-26
ubuntu lite's just a bunch of packages, i allready have a bare minimum install (server with xubuntu on the laptop)

i updated the kernel and trying it out, it seems as though the fan is working every once in a while, so maybe everything's fine.

one question, now that i did apt-get dist-upgrade, there is a colorful log in thing with a progress before, where before there was just text, now i can't see if im getting those same error messages, is there a log anywhere that i could look in?

---

### Post by Proleter on 2006-02-26
I don't think my computer is low mhz low ram configuration.(1700 mhz and 512 ram). I have to have 3000 Mhz and 2000 GB ram to bi right mhz right ram configuration?
There is got to be other solution. I don't have this kind of problem under Windows. 
Don't tell me to go back to windows becouse I just started to like Ubuntu :)

edit: UIn the Device Manager under processor I get the value 'processor'.. and value 'Unknown' for most of the parts.

---

### Post by Jackal82 on 2006-02-27
[QUOTE=kybishop]first, make sure acpi is turned off in your BIOS

after that, when GRUB loads up and asks you to choose a kernel, press e on the one you usually boot with

then go to the command that starts with kernel

press e

add to the end of the command:
acpi=off apm=on

press escape

press b, you have to do it every time you boot your computer, im sure there is a way to set it as default, but i don't know how[/QUOTE]



sudo gedit /boot/grub/menu.lst
and add these to your kernel before the "ro quiet splash" -text: acpi=off apm=on

---

### Post by localzuk on 2006-02-27
All messages are logged to /var/log/messages

You should, IIRC, be able to press escape in order to view the log in text. However, you should not need to, as the graphical boot turns off as soon as there is an error.

---

### Post by jimrz on 2006-03-01
you can get rid of the splash screen and return to text only from terminal by:

```
sudo cp /boot/grub/menu.list /boot/grub/menu.list-backup
``` (always a good idea)...then
```

sudo nano /boot/grub/menu.list
```

scroll down to the KERNEL section and remove each intance of the word "splash" to make it look like this:

kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet

save and close your file...no more splash @ boot up.

---

### Post by tbrminsanity on 2006-08-22
My solution for my 1750 was to keep the laptop unplugged till the desktop booted, then I plugged it in.  Works everytime but I can't explain it.  I plan to hardwire my fan directly to my powersource so that the fan always runs.  The other thing I had to do was take out my floppy drive when I was not using it.  This gave me a direct airflow path over 25% of the motherboard and dropped my running temp by 5C.  It isn't a solution but it is a treatment.

---

