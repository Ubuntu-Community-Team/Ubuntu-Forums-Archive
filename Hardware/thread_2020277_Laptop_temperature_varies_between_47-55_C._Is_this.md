---
title: "Laptop temperature varies between 47-55 C. Is this normal?"
date: 2012-07-08
forum: Hardware
---

### Post by foobantu on 2012-07-08
Hi,

I've installed Ubuntu 12.04 on my Lenovo Z570 laptop with Intel i5 processor, 3 GB RAM and Nvidia Geforce GT 520M Graphics with 1 GB dedicated Memory. [Optimus - switchable graphics]

Everything works fine. This is the only Linux Flavour where 1) Fn+F2 works (Screen blank out)  2) Suspend Resume works 3) Brightness reduce/increase works. 4) pppoe configuration works.

Just one issue is laptop heating. I have googled, but couldnt find definitive answers.

When I am not running youtube videos, temperature stays at about 47 C, but then if I am running youtube videos, it goes upto 51 C. Add some downloads or apt-get installs and it sometimes reaches 57C, but mostly at 55 C.

The bottom of the laptop also seems somewhat hot to touch.

Is this normal temperature or something I should worry about?

Please let me know.

---

### Post by Icarus315 on 2012-07-08
Normal temperatures should be around 30C idle.  55C is on the high end and your temperatures should never hit 70C.

The first thing you should try is to blow out any dust/dirt that may have accumulated in the heat-sinks below the fans in your laptop.  If you don't know how to do that you can bring your laptop into a computer store and it'll be cheap or even free for them to do that.

---

### Post by sanderj on 2012-07-08
I have a quite new laptop (Samsung R540) and temperatures are about the same as yours. Temp goes even up to 65 C.

That seems normal to me.

---

### Post by foobantu on 2012-07-08
Hi,

Thank you for taking time to reply.

I will surely get the laptop checked and get it cleaned up.

Meaning while, will have to work on the "Wired Network Disconnected" - false error message that keeps popping. 

Will open a separate thread for that one.

Thanks guys. This is really a useful community. :)

---

### Post by sanderj on 2012-07-08
PS:

This is the current CPU temp of my laptop:

```
sander@R540:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +53.0°C  (crit = +89.0°C)
temp2:        +53.0°C  (crit = +89.0°C)

sander@R540:~$ 
```


So I would say that's normal.

---

### Post by foobantu on 2012-07-08
Hi Sanderj,

I think then I should be fine.

```
linuxguy@linuxbox:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  (crit = +98.0°C)
temp2:        +42.0°C  (crit = +126.0°C)

linuxguy@linuxbox:~$ 
```

BTW, I turned off the "Optimus" Option in the EFI, keeping it to "UMA Only" so that my laptop is running off the Intel Graphics, and that seems to have cooled down my laptop.

Some other versions of Linux I used didn't require this. May be there is a workaround.

I'll try and look around.

---

### Post by foobantu on 2012-07-08
Hi,

The issue seems to be fixed, but I will keep monitoring for a few days.

Found this excellent tutorial on Youtube:

[http://www.youtube.com/watch?v=uKi1YHAq3wM](http://www.youtube.com/watch?v=uKi1YHAq3wM)

Using this, I modified the /etc/default/grub file as shown in the tutorial.

But before doing any of that, I copied the file so that in case something goes wrong, I can fix it easily by copying back the file.

```
root@linuxbox:~# cp /etc/default/grub /etc/default/grub.orig
```
Here is what is given in the tutorial comments section:

In Terminal: gksudo gedit /etc/default/grub
In GRUB: 

GRUB_CMDLINE_LINUX="" 

replace with:

GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"

Save, update GRUB using 

sudo update-grub

REBOOT, then open the Terminal again and type:

gksudo gedit /etc/default/grub

And replace the 2nd to last line with:

GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=\"Linux\""

I did the changes, and now my laptop seems much cooler. :)

---

### Post by foobantu on 2012-07-08
Looks like only when I start watching youtube videos, the temperature of the laptop goes about 55C. Else its almost steady at 46C or so.


Currently I have

Installed the relevant drivers for my graphics card and installed Bumblebee, but that didn't help much, so 

Switched off the Nvidia Graphics Card in EFI (Optimus)

Installed Jupiter and set it on "Power Saving" mode.

Did the updates mentioned earlier and edited the /etc/defaults/grub file. What I did different is only changed the following line:

```
GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"
```I had earlier changed the next line to :

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=\"Linux\""
```Which I changed back to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```And found that it helped bring down the temperature to about 47C.

Ran ```
update-grub
``` to ensure that the changes take effect.

But still, with youtube videos, the temperature goes high and reaches 55C.

Hope I am not being paranoid. Just want to ensure that the laptop life doesn't get affected with the heating issue.

The palm rest area around the touch pad still seems to be somewhat warm to touch and bottom part is still sort of hot.

Not sure where I am going wrong :(

---

### Post by americanman28 on 2012-07-12
my brand new laptop idles at the same temp but never increases more that 3 degrees under full load

---

### Post by foobantu on 2012-07-13
Hi americanman28,
 
Thank you for the update. Is your laptop a Lenovo Z570 as well?
 
Does the temperature increase when you watch youtube videos?
 
Please let me know.

---

### Post by Lupajz on 2012-07-14
The patch file for z570 ideapad laptops has already been signed off to be released in new linux kernel adding support for fan controll, special keys and touchpad to work like on windows :) with proper fan setting temperatures might be lower :)

---

### Post by foobantu on 2012-07-15
Hi Lupajz,

Thank you for that update !!

I will wait till they release it...Man if this works, I'll be hooked to Ubuntu even more!!

---

### Post by marinaG0 on 2013-02-26
Hello,
           i just updated from Ubuntu 10.04 to 12.04 and i have the very same problem with temperature. With 10.04 my laptop was running between 47C-55C and now i have temperatures between 55C-65C. I use a VAIO VCPEB4Z1E . I tried the video tutorial but it didn't help.
                                                                                                                             Thank you

---

