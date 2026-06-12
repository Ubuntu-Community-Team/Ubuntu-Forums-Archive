---
title: "WakeUp Suspend with PS2 Keyboard How ?"
date: 2008-11-23
forum: Hardware
---

### Post by Rodney9 on 2008-11-23
Hello, 
      How do I set my ps2 keyboards '*Wake Up*' key to wakeup/resume from suspend.

I can not find anything in Keyboard Shortcuts.

I have searched this forum and can find references to usb, so I did try -

$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
P0P2	  S4	 disabled  pci:0000:00:01.0
P0P3	  S4	 disabled  
P0P1	  S4	 disabled  pci:0000:00:1e.0
UAR1	  S4	 disabled  pnp:00:0c
PS2K	  S4	 disabled  pnp:00:0e
EUSB	  S4	 disabled  pci:0000:00:1d.7
USBE	  S4	 disabled  pci:0000:00:1a.7
P0P5	  S4	 disabled  
P0P6	  S4	 disabled  
P0P7	  S4	 disabled  
P0P8	  S4	 disabled  pci:0000:00:1c.4
P0P9	  S4	 disabled  pci:0000:00:1c.5
GBEC	  S4	 disabled  
USB0	  S4	 disabled  pci:0000:00:1d.0
USB1	  S4	 disabled  pci:0000:00:1d.1
USB2	  S4	 disabled  pci:0000:00:1d.2
USB3	  S4	 disabled  
USB4	  S4	 disabled  pci:0000:00:1a.0
USB5	  S4	 disabled  pci:0000:00:1a.1
USB6	  S4	 disabled  pci:0000:00:1a.2
P0P4	  S4	 disabled  pci:0000:00:1c.0

and -
 
$ echo PS2K > /proc/acpi/wakeup
bash: /proc/acpi/wakeup: Permission denied

beyond this I'm stumped, any clues ?

Thanks,
Rodney.

---

### Post by kerry_s on 2008-11-24
> S4 disabled
check your bios, there should be settings to set the key pressed, mine says "any" for the keyboard wakeup. i also changed mine to use s3 instead of s4 in there.

---

### Post by Rodney9 on 2008-11-24
My brand new Asus P5Q Pro m/b has power on by keyboard in the bios, but no wake execpt "PCIE devices to generate a wake event", I don't know what this means.

---

### Post by kerry_s on 2008-11-24
sorry, i have no experience with something so new.
have you looked through your manual? i see on the site:
[http://www.asus.com/products.aspx?l1=3&l2=11&l3=709&l4=0&model=2269&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=11&l3=709&l4=0&model=2269&modelmenu=1)

>  ASUS EPU-6 Engine
System Level Energy Saving
The new ASUS EPU - the world´s first power saving engine, has been upgraded to a new 6 engine version, which provides total system power savings by detecting current PC loadings and intelligently moderating power in real-time. With auto phase switching for components (which includes the CPU, VGA card, memory, chipset, hard drives and CPU cooler/system fans), the EPU automatically provides the most appropriate power usage via intelligent acceleration and overclocking - helping save power and money


AI Nap
Minimize noise and power consumption when temporarily away!
With AI Nap, users can instantly snooze your PC without terminating the tasks. System will continue operating at minimum power and noise when user is temporarily away. It keeps downloading files or running applications in quietest state while you´re sleeping. Simply click keyboard or mouse, you can swiftly wake up the system in few seconds.


i haven't had the pleasure of working with such fine hardware.
i would suggest you hit google see what problems/fixes if any:
[http://www.google.com/search?hl=en&safe=off&client=iceweasel-a&rls=org.debian%3Aen-US%3Aunofficial&q=Asus+P5Q+Pro+linux&btnG=Search](http://www.google.com/search?hl=en&safe=off&client=iceweasel-a&rls=org.debian%3Aen-US%3Aunofficial&q=Asus+P5Q+Pro+linux&btnG=Search)

---

### Post by blackpaw on 2008-11-24
> **kerry_s said:**
> sorry, i have no experience with something so new.
have you looked through your manual? i see on the site:
[http://www.asus.com/products.aspx?l1=3&l2=11&l3=709&l4=0&model=2269&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=11&l3=709&l4=0&model=2269&modelmenu=1)

> AI Nap / EPU 6-Engine

i haven't had the pleasure of working with such fine hardware.
i would suggest you hit google see what problems/fixes if any:
[http://www.google.com/search?hl=en&safe=off&client=iceweasel-a&rls=org.debian%3Aen-US%3Aunofficial&q=Asus+P5Q+Pro+linux&btnG=Search](http://www.google.com/search?hl=en&safe=off&client=iceweasel-a&rls=org.debian%3Aen-US%3Aunofficial&q=Asus+P5Q+Pro+linux&btnG=Search)


Man, I wish these tools were available for Linux. I hate having my system run at full speed for a download over night...

Windows only I guess.. 

What this board does extremely well is monitoring case and CPU temp and slowing down the fans to make it quite (adjustable in BIOS)


I have contacted ASUS on this.


Andreas

---

### Post by Rodney9 on 2008-11-24
Why can't  I - 

$ sudo echo PS2K > /proc/acpi/wakeup
bash: /proc/acpi/wakeup: **Permission denied**

Would a usb keyboard work ?

---

### Post by kerry_s on 2008-11-24
> **Rodney9 said:**
> Why can't  I - 

$ sudo echo PS2K > /proc/acpi/wakeup
bash: /proc/acpi/wakeup: **Permission denied**

Would a usb keyboard work ?

```
$ sudo su
echo PS2K > /proc/acpi/wakeup

```

---

### Post by Rodney9 on 2008-11-24
> $ sudo su
echo PS2K > /proc/acpi/wakeup I tried that,

Now the the sleep and wakeup keys fail.

---

### Post by Rodney9 on 2008-11-24
I have re-booted and used System/Preferences/Keyboard Shortcuts and still the 'Sleep' key will not work as it did before I used the code above.

Now The 'Wakeup' and 'Sleep' keys both don't work, how do I get them to ?

---

### Post by Rodney9 on 2008-11-24
> sudo su
echo PS2K > /proc/acpi/wakeu

I have re-booted and used System/Preferences/Keyboard Shortcuts and still the 'Sleep' key will not work as it did *before* I used the code above.

> cat /proc/acpi/wakeup shows PS2K disabled, I do not understand ?

I have again checked the bios in my brand new Asus P5Q Pro m/b, it  has power on by keyboard in the bios, but no wake .


Now The 'Wakeup' and 'Sleep' keys *both* don't work, how do I get them to ?

Rodney.

---

### Post by quinn on 2010-08-25
Sorry for the thread necromancy, but i just had this problem, and solved it!

Try this command:

```
echo KBC0 > /proc/acpi/wakeup
```

Did the trick for me

---

