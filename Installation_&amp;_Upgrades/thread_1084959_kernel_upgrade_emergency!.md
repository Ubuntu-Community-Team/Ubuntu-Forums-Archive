---
title: "kernel upgrade emergency!"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by davbren on 2009-03-02
Hey all! I have a slight emergency. I just upgraded the kernel via the update manager and on reboot i get a blank screen after the usplash. I've left it for about 2 hours and still nothing...

What could it be?

---

### Post by taurus on 2009-03-02
Can you still boot with the old kernel from GRUB menu?  If you don't see the menu when you turn on your machine, press Esc key to bring it up.

---

### Post by davbren on 2009-03-02
Its not listed. I used the start up manager to take out hte other entries! *won't* be doing that again haha.

---

### Post by taurus on 2009-03-02
Boot into recovery mode and pick the xfix.  See if that fixes your X server.

---

### Post by davbren on 2009-03-02
Yh this allowed me to login but when i try and use the nvidia drivers, i get the same problem...

---

### Post by taurus on 2009-03-02
Which nvidia card do you have and which driver did you install?

```
lspci | grep VGA
```

---

### Post by davbren on 2009-03-02
I have this: -

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)

I tried to install the nvidia 177 driver. The one that says (recommended) on it.

---

### Post by davbren on 2009-03-02
I'm currently using kernel .27-12 it seems to be working ok, so I'll carry on for the mean time.

---

### Post by elvisd on 2009-03-03
+1.
Same problem here. My VGA is:
VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

---

### Post by elvisd on 2009-03-03
+1
same problem here.
I can still boot with old kernel...;)

my nVidia card is
lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

Hope this helps someone fix the problem.

---

### Post by Xianath on 2009-03-03
Worked for me with the 180 drivers. I booted using the old kernel and installed the nvidia-glx-180 package. Hope this helps you folks too.

Cheers,
Peter

---

### Post by q5651331 on 2009-03-03
nvidia-glx-180 also need this package:nvidia-180-kernel-source
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180)
go here to download!

---

### Post by elvisd on 2009-03-03
Ok. oroblem solved. now running latest kernel and nvidia 180.
Thanks guys!

Long live to Ubuntu and community!

---

### Post by newbie2 on 2009-03-03
+1 
same problem here...blank screen with flickering horizontal stripes...i am back to older kernel now... :confused:

---

### Post by elehayyme on 2009-03-03
Just finished doing the kernel upgrade on my lappy and ended up with the same problem as you all.

I'll ask for some help here at home to try and get my lappy back in working order with the new drivers, etc.

---

### Post by martinm1000 on 2009-03-03
I'm also having that problem; I just posted this :

[http://ubuntuforums.org/showthread.php?p=6833265#post6833265](http://ubuntuforums.org/showthread.php?p=6833265#post6833265)

How to install and activate this driver (180 ?)

I installed it but I don't see it under Hardware Drivers...

Edit: Ok, It activated while rebooting...

Did anyone reported the bug ?

---

### Post by bdoe on 2009-03-03
+1 on my laptop as well. Nothing in system logs to indicate any failures. Rebooting with .12 kernel works fine.

GPU: nVidia 8600M-GS

Question: Will updating to the 180 driver mess up my ability to boot into older (pre- .13) kernels?

I'm not going to mess with it right now. I need some time to get my heartbeat back down to normal. :eek:

---

### Post by imnotashinobi on 2009-03-04
ok, after installing/uninstalling 180.11[intrepid] and 180.35[for jaunty?], [compiz-check]("http://forum.compiz-fusion.org/showthread.php?t=8383") opened up the "Hardware Drivers" app for me and... 180 is now there[and "recommended", whereas 177 was recommened before].

i think i had 180.35 installed[for the second time] while i did the compiz-check. i'll be back if anything else needs to be mentioned...

---

### Post by mike173 on 2009-03-04
I have the same problem after upgrading my ubuntu-8.10 from 2.6.27-12 to 2.6.27-13.  I can see small differences in /var/log/messages.  For example, both kernels have these lines:

input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/
device:02/input/input10
ACPI: Video Device [NVID] (multi-head: yes  rom: no  post: no)

But only older kernel has the following lines after lines above:

input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input11
ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)

I have not updated NVidia driver yet.

---

### Post by bdoe on 2009-03-04
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/337019](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/337019)

---

### Post by blde99 on 2009-03-04
Installing 180.11 from Synaptic worked for me.
Installed the following:
nvidia-glx-180-dev
nvidia-180-kernel-source
nvidia-180-modaliases
nvidia-glx-180
nvidia-settings (think this was already installed).

Booting with.13 kernel a treat.

Edit:  This was after xfix from recovery mode.

---

### Post by lordlukas on 2009-03-04
same problem ++

---

### Post by brunods on 2009-03-04
Same problem here

---

### Post by dugh on 2009-03-04
Same issue with a Dell D820.  Completely black screen.

---

### Post by dei on 2009-03-04
can confirm this problem, but it's fixed with the 180 driver..

thx for the hint!

---

### Post by Carlos Sevcik on 2009-03-04
I posted this earlier this morning, its an update glich. Hopefully it wil be solved soon, but in while its solved, just boot your old kernel. You can set this as default by editing as root /boot/grub/menu.lst and modify:

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

to 

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		2

You may do this using

sudo gedit /boot/grub/menu.lst

This will make the kernel installed before the last version to be your boot default kernel. Remember to change default back to 0 when they fix the bug to make the newest kernel your default.

---

### Post by ddastoor on 2009-03-06
Thanks, I installed nvidia 180 and I got into kernel -13.

However, I went to System -> Preferrences -> Appearence -> Visual Effects -> Normal

and it tells me "nvidia 173 is required."

If I install this, will it create problems? What about the newly installed 180 ?

Thanks, Dinshaw

Ubuntu 8.10 on Dell Inspiron 6400 Laptop.

---

### Post by davbren on 2009-03-08
I broke xserver and it won't come back :( I tried to install the latest driver for nvidia and it broke the graphics. I don't know what to do. I tried uninstalling and reinstalling but it doesn't work, it tells me to reconfigure each time...

---

### Post by cgfoz on 2009-03-09
Just tried the two options suggested.

Upgrading the nvidia drivers to 180 meant I could boot 27-13, but I get a big 'beta' sign on the nvidia bootup screen, and indeed there were a few wierd things in gnome with this driver.

So for me booting tot he older kernel is the peferred option for now

---

