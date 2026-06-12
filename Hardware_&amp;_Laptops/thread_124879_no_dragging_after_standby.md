---
title: "no dragging after standby"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by dskloet on 2006-02-02
Standby seemed to be working well on my laptop (Fujitsu Siemens Lifebook S6120) and I was happy about that. But lately I noticed that after I return from standby I can't drag with my touchpad by tapping on it and then moving. I can drag using the button and I can drag using an external USB mouse but not by tapping the touchpad. I don't have this problem when returning from hibernation, only with suspend to memory (aka standby).

Does anybody have any idea what is cause this, and better, how to fix it?

thanks,
David

---

### Post by stangbang on 2006-02-02
sounds like its losing the synaptics options from your xorg.conf file when coming off suspend. Try going into suspend, and after coming out save any open work, and press ctrl+alt+backspace. This will log you out of your current session, and reload the xorg.conf file. Does it work after doing this?

---

### Post by dskloet on 2006-02-02
Unfortunately that didn't work...

---

### Post by stangbang on 2006-02-02
before you go into the standby go open your console and type
"cat /proc/bus/input/devices > /home/*username*/prestandby.txt"
replace *username* with your username.

Go into standby, and when you come back out type
"cat /proc/bus/input/devices > /home/*username*/poststandby.txt"

check to make sure that the event# for the synaptics device is the same in both. If for some reason the event# has changed that would cause the synaptics driver to not work properly.

Chances are that they will be the same, but its worth checking out. Let me know what you find out.

---

### Post by dskloet on 2006-02-03
I can't reproduce the problem anymore. Could it be solve just by catting /proc/bus/input/devices? Anyway, the pre~ and poststandby.txt are identical and the latter is attached.

Thanks for the effort so far.

---

### Post by stangbang on 2006-02-03
that would not fix the problem, but according to the devices file your touchpad is not even being identified. This is probably why it is acting up some.

---

### Post by dskloet on 2006-02-03
That's strange. Could it even work if it's not identified?

Edit: Isn't the ps/2 mouse the touchpad? Because I don't have a ps/2 mouse connected.

---

### Post by stangbang on 2006-02-03
it will still work if its not identified, but the synaptics driver will not be doing anything.

try deleting the file /etc/modprobe.d/psmouse.modprobe

when you reboot it should rebuild itself, and then do cat /proc/bus/input/devices

hopfully you should see a synaptics touchpad, or an alps touchpad device added in there

---

### Post by dskloet on 2006-02-03
There is no such file :-k .
```

$ ls -lF /etc/modprobe.d/
total 48
-rw-r--r--  1 root root  4405 2005-09-20 03:09 aliases
-rw-r--r--  1 root root 12305 2005-09-29 16:12 alsa-base
drwxr-xr-x  2 root root  4096 2005-11-16 19:57 arch/
lrwxrwxrwx  1 root root     9 2005-11-16 19:57 arch-aliases -> arch/i386
-rw-r--r--  1 root root   484 2005-10-03 11:12 bluez
-rw-r--r--  1 root root    38 2005-10-12 14:42 ibm_acpi.modprobe
-rw-r--r--  1 root root   399 2005-10-04 18:39 isapnp
-rw-r--r--  1 root root    29 2005-07-26 17:23 nvidia-kernel-nkc
-rw-r--r--  1 root root    41 2005-10-12 14:42 toshiba_acpi.modprobe

```

---

### Post by stangbang on 2006-02-03
well I have no clue then. It should come up with a touchpad device in there. here is what mine looks like on my fujitsu lifebook N6010.

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
H: Handlers=mouse1 event1 ts1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7322
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse2 event2 ts2
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event4
B: EV=40001
B: SND=6

If the psmouse.modprob file is not there then it should be able to detect the touchpad. I also looked up your model and it is using an alps touchpad. Maybe someone else has an idea as to why the touchpad is not being detected.

---

### Post by dskloet on 2006-02-03
Thanks for all the effort! At the moment it seems to be working so let's hope it stays that way :-).

---

### Post by stangbang on 2006-02-03
I did come accross somthing that mentioned acpi causing some problems with the alps touchpad. try booting with the parameter acpi=off or noacpi then do a cat /proc/bus/input/devices and see if the touchpad is detected then

---

### Post by dskloet on 2006-02-03
How do I do that? Should I edit /boot/grub/menu.lst ?

---

### Post by stangbang on 2006-02-03
when grub comes up select your kernel press e, and then the boot peramaters will come up. on the line with all the fancy peramaters press enter and add acpi=off. it should give you instructions on what to do while in there.

---

### Post by dskloet on 2006-02-03
I tried it but see no touchpad in /proc/bus/input/devices. But standby doesn't really work now so I guess I succeeded in turning off acpi.

---

### Post by stangbang on 2006-02-03
rebooting will turn acpi back on, but not sure on anything else to get the touchpad to show up in the devices

---

### Post by dskloet on 2006-02-03
I thank you for you time, though.

---

### Post by dskloet on 2006-03-27
It's happening again :-(.

---

