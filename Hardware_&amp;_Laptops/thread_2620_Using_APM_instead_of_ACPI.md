---
title: "Using APM instead of ACPI?"
date: 2004-10-29
forum: Hardware &amp; Laptops
---

### Post by Bob Collins on 2004-10-29
How do I uninstall ACPI and run APM instead?

I am trying to run Ubunto on an older Dell Latitude laptop (CPiA) which has a broken ACPI implementation. The laptop has worked with other distributions fine with APM as the power manager.

I tried to uninstall ACPI and install APM but the ACPI package is depended on by "ubuntu-desktop". This is bad. Does anyone have any ideas?

Looking at the planned changes for the spring release shows that they know of this problem. How do I fix it for now?

Thanks,

Bob Collins
Sunnyvale CA USA

---

### Post by enro2002 on 2004-10-30
I had a similar problem on my old Asus laptop.
Unfortunately ACPI Support is staticly compiled into the Ubuntu Kernel. So I'm afraid you have to recompile the Kernel. At least it worked for me. This is what i did:
First Install the Kernel sources and Develpment Tools.
Also install "kernel-package" 
use the root terminal for the rest
go to the kernel sources (cd /usr/src/linux-source-2.6.8.1)
do make menuconfig
load the conf file from /boot
swith off ACPI
save
do make-kpkg --initrd install_image
wait
the debian package should be in your /usr/src directory
install the package dpkg -i 
reboot your new kernel it should appear in your grub menu.

I did a lot of round trips in finding out how to recompile the kernel but I think this should be about it.

---

### Post by bsherman on 2004-11-01
ACPI is also somewhat broken on my IBM Thinkpad T23, well, APM seems to work much better anyway.

Here is a much simpler way to switch to using APM.

Edit your boot config using this command:
*sudo nano /boot/grub/menu.lst* 

You'll want to change the kernel line to add the items in red.
```
kernel   /vmlinuz-2.6.8.1-3-386 root=/dev/hda4 ro quiet splash [COLOR=Red]acpi=off noacpi[/COLOR]

```
In order to make sure this change propegates to future kernel upgrades, you'll also want to edit the default lines:
```
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash [COLOR=Red]acpi=off noacpi[/COLOR]

```

CTRL-X to save, and your boot config is updated.
One last thing, ensure you load the apm module.

*sudo nano /etc/modules* 

Simple add a new line with the module name "apm":
```

psmouse
mousedev
ide-cd
ide-disk
ide-generic
[COLOR=Red]apm[/COLOR]

```


Reboot, and you're running APM, not ACPI.

---

### Post by elempoimen on 2004-11-04
You know, I tried that on my T23. I ended up with a PCI error:

*Address space collision on region 7 of bridge*

Additionally, the hotplug system errored out, not loading at all, just giving me an error with every initialization. After a little troubleshooting, it was the *acpi=off* entry that did it. *noacpi* seemed to have no effect on the system--and my suspend mode still didn't work. Grr.

---

### Post by ben s on 2005-01-07
[QUOTE=elempoimen]You know, I tried that on my T23. I ended up with a PCI error:

*Address space collision on region 7 of bridge*

Additionally, the hotplug system errored out, not loading at all, just giving me an error with every initialization. After a little troubleshooting, it was the *acpi=off* entry that did it. *noacpi* seemed to have no effect on the system--and my suspend mode still didn't work. Grr.[/QUOTE]

The advice here: 
[http://www.ubuntulinux.org/wiki/SuspendHowto](http://www.ubuntulinux.org/wiki/SuspendHowto)

worked for me on a T30.  Quoting the pertinent part...

> 
To enable APM on a system, edit your /etc/modules file and add apm to the list of modules. Also, edit the #kopt line of your /boot/grub/menu.lst file so that it ends with apm=on, and then run sudo update-grub to update the GRUB configuration. Finally, add the modules shpchp and pciehp to the end of the /etc/hotplug/blacklist file (they don't work w/APM)


Note that the bit about running update-grub is unnecessary.  The key to stopping the failing modules from loading is the blacklist.

---

### Post by Andrew_H on 2005-08-02
Wanted to say that this worked great for my HP Omnibook 4150 -- ACPI wouldn't hibernate, whereas APM works great to hibernate when the lid closes.

Thanks for this post!

:A!

---

### Post by esj on 2005-08-31
ths suggestions here work sort of ok on my dell inspiron 5000.  main problems being the ati video garbarge on startup.  what I *really* want to do is shutdown video and backlight when the lid is closed but otherwise keep running[1] and suspend  when I push the power button once.

any suggestions?

-- eric

[1]  I use speech recognition on windows so I run apps on linux, display on windows, and all works fine untill my cat walks on the keyboard (must be genetic thing.  all of my cats have had an affinity for keyboards)

---

### Post by 1Ank1 on 2006-12-05
Hi, this thread was a godsend for me, i have been tearing my hair out looking for the solution that bsherman has provided here.

My problem was i had installed every version of ubuntu i could lay my hands on and every time i had a problem with my network connectivity. The operating system was recognising my nic and i could ping it but get no further. I couldnt ping my nic from the outside either, it was as if it was there but it wasnt??!! anyway to cut a long story short, after applying bsherman's solution in this thread all was 'Happy penguins' for me once again.

Thanks bsherman u r a guru ;)

---

### Post by TubaTodd on 2007-03-05
I followed the instructions in this thread and I was able to replace acpi with apm. One thing I noticed immediately is that my CPU scaling is no longer in effect (this was the desired effect). Now, my machine runs at top speed ALL of the time. This has been a very nice speed boost.

My question is as follows, I noticed that when the kernel boots it flashes about 10 lines of messages after initializing the kernel. It happens so fast that I can't read everything that it says. The lines may be errors, but I can't tell. The rest of the boot sequence is fine and the machine runs great. Should I be concerned with the 10 lines of stuff at the beginning? Thanks! :)

---

### Post by tedrogers on 2007-03-06
When I tried this APM thing...it was generally all ok but when shutting down my laptop wouldn't turn off...it just sticks at the end of the shutdown screen. So I'm back on ACPI now with my "ACPI: Fatal Opcode Executed" message...but at least it shuts down!

---

### Post by TubaTodd on 2007-03-06
I had the same thing happen to me. My laptop won't automatically shutdown after halt either. I don't want to go back to ACPI. What can I do?

---

### Post by tedrogers on 2007-03-07
Not much in my experience...just go back to ACPI by removing the ACPI=off command from the menu.lst file.

Tough love here for you and me!

---

### Post by TubaTodd on 2007-03-07
Ok, I just got the best of both worlds. I went to Gnomefiles.com and downloaded the 1.0Beta2 version of the GFreqlet applet. It allows you to change your processor speed with a couple clicks. VERY VERY nice!!! :) I selected "performance" and my machine is running at maximum warp. W00t!

---

### Post by bryonak on 2007-04-27
For those of you who can't shutdown with apm, try adding the following line to /etc/modules:
```

apm power_off=1

```
Did the trick for me.

---

### Post by Michl on 2007-09-27
I'm looking for a solution to the problem that my laptop always
shutsdown when I close my lid and one suggestion I ran into is
messing with the kernel settings for APM and ACPI.  But it looks
like this isn't a sure-fire thing and can send you to computer hell
trying to get back to where you were before you started fixing
things.  I've had ubuntu for 8 months now on several machines
and this is a familiar story.  Better not touch the house of cards.

Michl

---

### Post by BigBananaMan on 2008-05-17
I had a problem with my old dell c600 that appears to have been caused by acpi.  Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=366274&highlight=ubuntu+boot+freeze+dell+c600") I solved my problem in 2 minutes plus restart time.

---

