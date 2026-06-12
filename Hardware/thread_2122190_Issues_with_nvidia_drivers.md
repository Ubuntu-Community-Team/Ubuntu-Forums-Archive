---
title: "Issues with nvidia drivers"
date: 2013-03-04
forum: Hardware
---

### Post by Hairo C on 2013-03-04
i went using the gui at first (software sources -> additional  drivers), it installed without any problem, but when restarting and  running  "sudo lshw -C display" i still get this:

```

*-display               
   descripción: VGA compatible controller
   producto: G96 [GeForce 9500 GT]
   fabricante: NVIDIA Corporation
   id físico: 0
   información del bus: pci@0000:01:00.0
   versión: a1
   anchura: 64 bits
   reloj: 33MHz
   capacidades: pm msi pciexpress vga_controller bus_master cap_list rom
   configuración: driver=nouveau latency=0
   recursos: irq:16 memoria:a2000000-a2ffffff memoria:80000000-9fffffff memoria:a0000000-a1ffffff iop
```

Notice the "driver=nouveau" part, i tried uninstalling the nvidia driver and reinstalling it on the console (using "sudo apt-get install nvidia-experimental-310") and it installed sucessfull, i had the kernel headers installed too, so i got no errors... but again after rebooting and checking the nouveau drivers keeps coming...

  after some thinkering i managed to install them properly... but then after rebooting i  got stuck at 640x680 res, unity was glitchy and got a black bar at the  left of the screen... i tried with nvidia-experimental-310,  nvidia-experimental-304, nvidia-current and nvidia-current-updates with  the same result... any help?

---

### Post by deadflowr on 2013-03-04
Did you run:
```
sudo nvidia-xconfig
```

After the driver was installed?

---

### Post by stinkeye on 2013-03-04
For 12.10 I had to install linux-headers-generic before installing the nvidia driver.

```
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by ManamiVixen on 2013-03-04
On 12.10, with your card, only nvidia-current works. Anything newer will cause issues.

---

### Post by Hairo C on 2013-03-04
> **deadflowr said:**
> Did you run:
```
sudo nvidia-xconfig
```

After the driver was installed?

I did it after rebooting after launching nvidia-settings and getting the typical "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." and got the "sudo: nvidia-xconfig: command not found" error when trying to run it, IIRC xorg.conf is not currently being used. 

i'll try running it just after installing the drivers (before rebooting) when i get home.

Thanks for the answer.

> **stinkeye said:**
> For 12.10 I had to install linux-headers-generic before installing the nvidia driver.

```
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings
```

As you can see in the first post i had it installed before installing the drivers, but i'll try this when i get home... who knows, it might work.

Thanks for the answer.

> **ManamiVixen said:**
> On 12.10, with your card, only nvidia-current works. Anything newer will cause issues.

As you can see in the first post, i tried with nvidia-current too and got the same issues.

Thanks for the answer.

---

### Post by Hairo C on 2013-03-04
My issues persisted... seems like i'm stuck with nouveau then, any other suggestion?

---

### Post by stinkeye on 2013-03-04
Does nouveau run ok?
I actually reverted because I found nouveau to run just as well for normal desktop stuff.

---

### Post by Hairo C on 2013-03-05
They run fine for basic desktop usage... the problem comes when i try to play a game that runs fine on windows... i will try using Precise.

---

