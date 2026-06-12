---
title: "Lenovo Trackpoint - speed &amp; sensitivity"
date: 2010-03-05
forum: Hardware
---

### Post by Boeby on 2010-03-05
Hi@all,
I hope somebody can help me. Its not very important, but annoying...
I work and use privat Lenovo Thinkpads with a trackpoint... That's perfect for me.. but it's very slow..
I made this every reboot: 
sudo su; 
echo -n 180 > /sys/devices/platform/i8042/serio1/speed 
echo -n 250 > /sys/devices/platform/i8042/serio1/sensitivity
(that works only with the &quot;full&quot; sudo su, not with &quot;normal&quot; sudo) 

Can I automate this at every reboot, or does anybody know a better solution to speedup my trackpoint ?  
(I copied this two lines also in the rc.local, but that wasnt work..)    

Thank you all

---

### Post by Fafler on 2010-03-05
sudo nano /etc/rc.local and add your commands before the exit 0

---

### Post by Boeby on 2010-03-05
thx for your reply..
i did this, but it doesnt work..
(nothing happens)

The strange thing is that i cannot send this command with a sudo. = Permission denied
When I send this commands with root (sudo su) = accepted

rc.local
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo -n 180 > /sys/devices/platform/i8042/serio1/speed
echo -n 250 > /sys/devices/platform/i8042/serio1/sensitivity
exit 0
that does not work.. i dont know why.. probably its my fault, but i dont know how i can correct this..

---

### Post by iponeverything on 2010-03-05
what do you see when you:

```
cat /sys/devices/platform/i8042/serio1/speed /sys/devices/platform/i8042/serio1/sensitivity

```

---

### Post by Boeby on 2010-03-05
> 
fc019032@fc019032-laptop:~$ cat /sys/devices/platform/i8042/serio1/speed /sys/devices/platform/i8042/serio1/sensitivity
180
250
fc019032@fc019032-laptop:~$ 
That works well.. But i cannot write into these files with sudo..
And from my point, it seems that also the user which start rc.local cannot write into these files.. could that be true ?

---

### Post by iponeverything on 2010-03-05
> **Boeby said:**
> That works well.. But i cannot write into these files with sudo..
And from my point, it seems that also the user which start rc.local cannot write into these files.. could that be true ?

rc.local is ran as root. 

Run the cat to see what the values are after fresh boot, so that cat see if the values were changed by the rc.local command and not by your doing it from the command line. The cat is not changing the values, it is just showing you what they are.

---

### Post by Boeby on 2010-03-05
i dont know exactly how to describe it.

it works on my thinkpad in the office, but not at home..

the path to write the numbers is also different. but both devices are Thinkpad T400..

something must be different..
On my private thinkpad the path is:

This works with sudo su:
> 
echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 180 > /sys/devices/platform/i8042/serio1/serio2/speed


And here my rc.local:
> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo -n 250 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 180 > /sys/devices/platform/i8042/serio1/serio2/speed


exit 0


Permissions on the rc.local
> -rwxr-xr-x 1 root root 438 2010-03-05 21:57 /etc/rc.local


any ideas ?

thank you

---

### Post by Boeby on 2010-03-07
thank you all,
the problem is solved..
it was my fault and the hint with rc.local was correct..

---

