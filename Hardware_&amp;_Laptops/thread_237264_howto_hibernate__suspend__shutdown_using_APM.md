---
title: "howto: hibernate / suspend / shutdown using APM"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by derekbei on 2006-08-15
It took a long time combing and combining many posts to successfully get my IBM T22 laptop under Dapper Drake 6.06 to hibernate / suspend / and fully shutdown. Basically when the system bios is too old to support the newer ACPI power management, enabling the older APM power management will give you much better functionality. Here's how I did it. 

1) Add 'noacpi acpi=off apm=on nolapic' to your kernel options in /boot/grub/menu.lst
i.e. Code:
sudo gedit /boot/grub/menu.lst
Search for the line that looks like 'kernel  /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash' 
(exact entry can vary)
Just add 'noacpi acpi=off' (no quotes) to the end of that line.
Save.

2) Add 'apm' to /etc/modules
i.e. Code:
sudo gedit /etc/modules
Add 'apm' (no quotes) 
Save.

3) Create a file in /etc/modprobe.d (such as /etc/modprobe.d/power) and add the following:
options apm power_off=1 realmode_power_off=1
Save.

4) Reboot

note: Suspend and Hibernate work fully only when running on battery power. So unplug your AC adapter. 
Both the function key shortcuts and the menu based suspend/hibernate work for me. They should for you too. 
Tested under Dapper Drake v.6.06

Hope this helps and is clear enough for all newbies. 
Ubuntu gave and even shipped their product to me for free. This is the least that I can do. Should also work with all older thinkpads incl. T20/T21 and quite possibly other brands as well. Try it out, there is nothing irreversible or complicated about it. Good luck to newbies all the same!

---

### Post by meng on 2006-08-15
Thanks. I'm going to try this with my Dell Inspiron 8200, which is having some issues with suspend.

---

### Post by Jaxilian on 2006-08-27
> **derekbei said:**
> It took a long time combing and combining many posts to successfully get my IBM T22 laptop under Dapper Drake 6.06 to hibernate / suspend / and fully shutdown. Basically when the system bios is too old to support the newer ACPI power management, enabling the older APM power management will give you much better functionality. Here's how I did it. 

1) Add 'noacpi acpi=off apm=on nolapic' to your kernel options in /boot/grub/menu.lst
i.e. Code:
sudo gedit /boot/grub/menu.lst
Search for the line that looks like 'kernel  /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash' 
(exact entry can vary)
Just add 'noacpi acpi=off' (no quotes) to the end of that line.
Save.

2) Add 'apm' to /etc/modules
i.e. Code:
sudo gedit /etc/modules
Add 'apm' (no quotes) 
Save.

3) Create a file in /etc/modprobe.d (such as /etc/modprobe.d/power) and add the following:
options apm power_off=1 realmode_power_off=1
Save.

4) Reboot

note: Suspend and Hibernate work fully only when running on battery power. So unplug your AC adapter. 
Both the function key shortcuts and the menu based suspend/hibernate work for me. They should for you too. 
Tested under Dapper Drake v.6.06

Hope this helps and is clear enough for all newbies. 
Ubuntu gave and even shipped their product to me for free. This is the least that I can do. Should also work with all older thinkpads incl. T20/T21 and quite possibly other brands as well. Try it out, there is nothing irreversible or complicated about it. Good luck to newbies all the same!


This didn't work for me on my Znote 2415W ([www.zepto.se](www.zepto.se)). Sleep button stopped working and suspend only kicked me back to desktop when I tried. :confused:
I hope they fix the lousy ACPI support someday soon.

---

### Post by 2FishInATank on 2006-08-29
Thanks very much - everything now works on an old BX chipset motherboard using
'noacpi acpi=off apm=on noapic' in /boot/grub/menu.lst

N.B. noapic not nolapic! ;)

---

### Post by jruschme on 2006-08-30
You also need a Fat32 partition with the ThinkPad hibernation file, right?

---

### Post by jalexstark on 2006-08-31
Does not work on my T20.

From Gnome/system/quit/suspend I can do "ps ax"
and see a process with "acpi" in it.

Note: I upgraded, not installed fresh.

---

### Post by Dittohead on 2006-08-31
> **meng said:**
> Thanks. I'm going to try this with my Dell Inspiron 8200, which is having some issues with suspend.

It worked for me!! Awesome stuff!

The LCD panel wouldn't come on when X started, it would actually turn if off though everything was running just fine. Windows would even rarely come out of suspend or hibernation without turning the screen off. Now after these changes my monitor comes on every single time.

Sweet! :D

---

### Post by willingc on 2006-12-18
This worked for my T21 under Dapper Drake 6.06.  Thanks for taking the time to post the solution.:)

---

### Post by nmincone on 2006-12-21
This solution seems to work only on older laptops (which is a good solution in that case). If you have hardware that does not support APM (only ACPI) then you'll run into some problems.

---

### Post by bahrain on 2007-01-17
thanks

that is what i was looking for

---

### Post by fleerink on 2007-06-03
> **2FishInATank said:**
> Thanks very much - everything now works on an old BX chipset motherboard using
'noacpi acpi=off apm=on noapic' in /boot/grub/menu.lst

N.B. noapic not nolapic! ;)

Hello,
Thanks a lot. For me it worked also in the "quoted" way on my old Lifetec 300 Mhz Pentium2 laptop, with an Phoenix Bios. In order to use on my Kubuntu 7.04 system the hibernation partition that is used by the Phoenix Bios (rel 4.0 ver6.0) I had to shrink my hda1 partion with 300Mb via GParted LiveCD, Created a primary  hda3 partition of type aO in the freed space with Kubuntu's fdisk. Downloaded and run the lphdisk utility that is the equivalent of the DOS only PHDISK.EXE  that prepares and formats the hibernation partition for notebooks using Phoenix Bios.

Regards,    Frans

---

### Post by jon.reeve on 2007-06-08
Hooray! I'm running Fiesty (Xubuntu) on an old Fujitsu Lifebook FMV-650. Before, every time I tried to come back from standby/suspend I always got a black screen--the LCD wouldn't come back up. Now it works a charm. Thanks!

---

### Post by tk03759 on 2007-06-08
well... it fixed the error I used to get at startup about ACPI... but it still won't shut down right. hrm...

---

### Post by abrianb on 2007-08-19
[FONT=Garamond]How do I ?
   [/FONT]
>  3) Create a file in /etc/modprobe.d (such as /etc/modprobe.d/power) and add the following:
options apm power_off=1 realmode_power_off=1
Save.
  
    Still kind of new at this.

---

### Post by tk03759 on 2007-08-30
Open a terminal and type in 
```
cd /etc/modprobe.d
sudo gedit
```

That will move you into the /etc/modprobe.d folder. Type in the options, "apm power_off=1 realmode_power_off=1" and click save. It should already be in the location /etc/modprobe.d. If not, move to it, and save the file with a name such as "power."

---

### Post by Pressurized on 2007-11-26
Thanks for this, derekbei (if you're still active!), your solution worked perfectly for me in getting my PC to shutdown. My mainboard is an MSI 915GM Speedster-FA4 which I think is a notebook kind of board.

I had built it into a full size PC designed for low power consumption to use as a server. It later became a backup PC when I discovered the excellent Excito bubba.

Cheers!

---

### Post by pschalkx on 2007-12-24
Worked just fine on my T20; Powerdown finally works!

Tks!

---

### Post by buntubunny on 2007-12-25
Thanks derekbei for the research. On my NEC Versa E2000 laptop running Ubuntu v7.10 Gutsy, power off and hibernate work, but suspend doesn't work. Guess this is due to the old hardware, as suspend doesn't work in Windows either.

For the benefit of those using similar hardware, these are my kernel parameters in /boot/grub/menu.lst:
[INDENT]kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=18865d08-1dd7-4975-8a17-84f584721311 ro quiet splash acpi=off[/INDENT]

Here are the contents of the file /etc/modprobe.d/power: ("power" is just the filename suggested by derekbei above, you could use any filename, just put it into the /etc/modprobe/ folder)
[INDENT]options apm power-off[/INDENT]


Also found some docs which might be useful to some people:

kernel-parameters.txt - Describes the kernel options during bootup.
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt]("http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt")

It turns out that putting "apm=on" as a kernel parameter will be ignored as the APM driver is loaded as a module, not compiled into the kernel. So the configuration file in /etc/modprobe.d/ is necessary to set the options for APM. APIC (Advanced Programmable Interrupt Controller) is also not the same as ACPI (Advanced Configuration and Power Interface).

apm.c - Source code for the APM module. Describes options for the APM driver. How to see what your options are by going into /sys/module/apm/parameters/.
[http://www.gelato.unsw.edu.au/lxr/source/arch/i386/kernel/apm.c]("http://www.gelato.unsw.edu.au/lxr/source/arch/i386/kernel/apm.c")

---

### Post by easyjet on 2008-04-26
> **buntubunny said:**
> 

For the benefit of those using similar hardware, these are my kernel parameters in /boot/grub/menu.lst:
[INDENT]kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=18865d08-1dd7-4975-8a17-84f584721311 ro quiet splash **acpi=off**[/INDENT]

Here are the contents of the file /etc/modprobe.d/power: ("power" is just the filename suggested by derekbei above, you could use any filename, just put it into the /etc/modprobe/ folder)
[INDENT]**options apm power-off**[/INDENT]




Ubuntu was getting to the stage of shutting down the drives then stalling.

Was getting tired of having to restart into a secondry operating system as a result.

now powering off properly.Ubuntu 8.04 (Hardy Heron)

Fix worked on my desktop. 

[I]Motherboard Abit BX6 2.0
Award BIOS v4.51PG[/I]

---

### Post by fuseblower1123 on 2008-06-29
This works perfectly on a T20 with hardy and gutsy.
Thanks.

---

