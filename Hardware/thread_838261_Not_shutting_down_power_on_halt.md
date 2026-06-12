---
title: "Not shutting down power on halt"
date: 2008-06-23
forum: Hardware
---

### Post by domingo@domingo.dk on 2008-06-23
Hi

I'm running Hardy Heron on my MZ915-M XC Cube PC from Aopen. All is good except when shutting down where it doesn't cut the power, just hanging like in limbo. I can hear the fans are still running but all seams to be shutdown. This a problem because I've attached a usb-powerplug that kills all attached devices when the power turns off on the system. This doesn't happens when the machine isn't "killed" properly. 

The same issue also occurred running Gutsy Gibbon. 

The funny thing is that before I turned to Ubuntu I was running opensuse and it had no problems killing the power when shutting down. Also opensuse 11 which is installed at the moment powers down the machine correctly.

I've tried fiddling around with acpi parameters in grub but that didn't do the trick either.

The hardware specifications can be found here: [http://global.aopen.com/products_detail.aspx?Auno=55](http://global.aopen.com/products_detail.aspx?Auno=55)

---

### Post by domingo@domingo.dk on 2008-09-26
With the kernel coming with Intrepid (2.6.27) it now shuts down nicely cutting the power as it should.

---

### Post by domingo@domingo.dk on 2008-11-04
Hmm the problem lied somewhere completely differently. It was the sound driver which caused all the fuzz.

Just add the line:
```
/sbin/rmmod snd_hda_intel
```

to /etc/default/halt and you're good to go (or shutdown should I say :p)

---

### Post by Fizzdan on 2008-11-27
I'm seeing a very similar problem on my system with Intrepid installed
see [http://ubuntuforums.org/showthread.php?t=994588](http://ubuntuforums.org/showthread.php?t=994588)

But I don't have an hda intel sound card but a C-Media. 

How did you determine it was the sound card driver causing the power problems?

---

### Post by ravi14 on 2008-11-28
Thanks a lot! Adding this line **/sbin/rmmod snd_hda_intel** actualy worked for me. Wow! Finally I was able to solve with [email]domingo@domingo.dk[/email] help. 
Clicked Applicatons/Accessories/Terminal gave the command **sudo gedit /etc/default/halt** entered password and the below is the final version of how this files looks.
```

# Default behaviour of shutdown -h / halt. Set to "halt" or "poweroff".
/sbin/rmmod snd_hda_intel
HALT=poweroff
```

Did a man on rmmod to know.

 rmmod &#8212; simple program to remove a module from the Linux Kernel

So before shutting down the poweroff, you are also removing the snb_hda_intel module which will should be powered off aswell.

---

### Post by aaronyyz on 2008-12-10
I'd be interested to know how **domingo@domingo.dk** determined the sound card was causing the issue. After many hours of frustration, this was also the cause of my shutdown issue on my new Ubuntu box with the same sound card.

---

