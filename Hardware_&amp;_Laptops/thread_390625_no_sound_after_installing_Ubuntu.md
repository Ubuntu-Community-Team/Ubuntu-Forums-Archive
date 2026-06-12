---
title: "no sound after installing Ubuntu"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by Alexcon on 2007-03-22
After having installed ubuntu on a lenovo C3000 laptop [dual boot with windows], I cannot hear any sound!
computer does recognize soundcard, [realtek audio onboard with intel motherboard]
How do I solve this problem?
please help
alex:confused:

---

### Post by renzokuken on 2007-03-22
i had this problem with a realtek chipset on my laptop too.

it boils down to the fact that the version of alsa-driver that comes with ubuntu doesnt support newer realtek chipsets very well. i solved my problem by installing (compiling) the latest alsa-driver from source off the alsaproject website.

if you need help doing this just let me know

---

### Post by Alexcon on 2007-03-22
reply to renzokuken:

thank you for info, but I need a little help here on how to corrct this problem

---

### Post by renzokuken on 2007-03-22
go to the alsa website ( [www.alsa-project.org](www.alsa-project.org) ) and download the latest stable version of the "alsa-driver", i think its version 1.0.13.

save this file to your Desktop.

install the tools necessary for compiling by running the following command

```
sudo apt-get install build-essential
```

now extract the alsa-driver file and enter the new folder by running

```

cd Desktop
tar xjf alsa*
cd alsa*

```

now to compile and install the driver you need to run three simple commands as follows

```

./configure
make
sudo make install

```

and thats it. reboot and see if it works.

i personally used the latest unstable release (1.0.14rc2) to get mine working and havent had any problems with it. so if 1.0.13 (stable) doesnt work, you could try it with 1.0.14rc2 (unstable)

good luck

---

### Post by yj09 on 2007-03-26
I already upgrade latest alsa driver. 1.0.14rc3 but still no sound on internal speaker.
i'm using feisty on Fujitsu C1410.

---

### Post by quick_dudley on 2007-03-26
> **renzokuken said:**
> go to the alsa website ( [www.alsa-project.org](www.alsa-project.org) ) and download the latest stable version of the "alsa-driver", i think its version 1.0.13.

save this file to your Desktop.

install the tools necessary for compiling by running the following command

```
sudo apt-get install build-essential
```

now extract the alsa-driver file and enter the new folder by running

```

cd Desktop
tar xjf alsa*
cd alsa*

```

now to compile and install the driver you need to run three simple commands as follows

```

./configure
make
sudo make install

```

and thats it. reboot and see if it works.

i personally used the latest unstable release (1.0.14rc2) to get mine working and havent had any problems with it. so if 1.0.13 (stable) doesnt work, you could try it with 1.0.14rc2 (unstable)

good luck

My father has the same problem on the same model laptop (I personally use ubuntu on a compaq presario with no such problems)
However, when I tried something like this all that happened was a kernel panic when I tried rebooting.

---

### Post by julian67 on 2007-03-31
This might help, it worked for me on a Lenovo Y400 which is an Asian market model based on the 3000 series and uses the Intel ich7 (82801g controller) sound controller. 

add ```
options snd-hda-intel model=laptop-eapd
``` to the end of /etc/modprobe.d/alsa-base

You'll need to reboot. This worked without any updating of the ALSA driver. I tried the driver upgrade method on a previous install and had no success, it seems the problem is not entirely the driver but the default configuration.

There is a thread on these forums about it [http://www.ubuntuforums.org/showthread.php?t=314383]("http://www.ubuntuforums.org/showthread.php?t=314383")

---

### Post by quick_dudley on 2007-04-01
solved on my father's computer
in /boot/grub/menu.lst
add acpi=hd to the end of the "kernel" line
There are two trade-offs: doesn't completely power down when you shut down, but only requires a light tap on the power button once everything's unloaded and processor halted, and the battery monitor no longer works.

---

### Post by peesemould on 2007-04-04
> **renzokuken said:**
> go to the alsa website ( [www.alsa-project.org](www.alsa-project.org) ) and download the latest stable version of the "alsa-driver", i think its version 1.0.13.

save this file to your Desktop.

install the tools necessary for compiling by running the following command



I've just done this to my Dad's laptop and after I restarted the computer it gets to the status bar and just sits there for about 5 minutes and then gives me this.

```
udevd-event[2639]: run_program: '/sbin/modprobe' adnormal exit
```

What can I do? :(

---

### Post by Some_ux on 2007-08-22
Thanks, solution worked for my Lenovo 3000 N100

---

### Post by netron on 2007-08-22
> **quick_dudley said:**
> solved on my father's computer
in /boot/grub/menu.lst
add acpi=hd to the end of the "kernel" line
There are two trade-offs: doesn't completely power down when you shut down, but only requires a light tap on the power button once everything's unloaded and processor halted, and the battery monitor no longer works.

how would that solve an alsa sound problem?  that seems to be completly unrelated.
anyone have an explanation?

---

