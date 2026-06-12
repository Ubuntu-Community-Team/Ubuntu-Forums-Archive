---
title: "Asus laptop numpad not working (Dvorak kb layer)"
date: 2010-04-17
forum: Hardware
---

### Post by QuanTime on 2010-04-17
My numlock kb switch works, the LED goes on / off..  The enter key works, and so do the home / end and stuff.. BUT.. when i want a numberpad, the numbers DONT work.  And the arrows mostly dont work either.  When the numlock pad is set to "on" (LED on) the up / 8 and down / 2 key makes the mouse move up and down.  If the numlock is OFF, the same thing happens.

Id like a working number pad, and the ability to use the / * - + keys.  

Anyone know a way to fix this or had similar problems ?  Heres some basic outputs if its any help.  PLease advise.

cat /proc/bus/input/devices
```

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

```Only thing of interest, rest is lid / power switch, etc..

dmesg | grep input
```

[    0.876143] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5

```Theres nothing in my xorg.conf file, but i do indeed use the Dvorak KB layer.
Just so you can physically see what ive got, here is my laptop model.  
[IMG]http://www.gadgetgad.com/wp-content/uploads/2009/12/ASUS-K70IC-A2-17.3-Inch-Entertainment-Laptop.jpg[/IMG]

---

### Post by Machaon on 2010-05-11
I had a similar problem and found this solution:

Try going to System, Preferences, Keyboard. Then select the "Mouse Keys" tab and uncheck "Pointer can be controlled using the keypad".

---

### Post by QuanTime on 2010-05-11
worked perfectly.   Settings went to hell when i went Lucid.  Such is life.

Still never solved my gsynaptics-device settings problem.  I want the touch pad to disable while typing,, which i STILL cant make it do.. Otherwise im set.

---

### Post by Arminho on 2010-06-17
I had the same problem and the fix worked for me as well.
Thx!!!

---

### Post by TiloBunt on 2011-01-06
kudos from my side as well. Had this issue on a Asus G73 and num block

---

### Post by raghuramos1987 on 2011-01-27
thanks! worked perfectly!

---

### Post by ItalOz on 2011-02-18
worked perfectly for an ASUS K50IJ

thanks

12345679 hehe

---

### Post by adduds on 2011-03-21
> **Machaon said:**
> I had a similar problem and found this solution:

Try going to System, Preferences, Keyboard. Then select the "Mouse Keys" tab and uncheck "Pointer can be controlled using the keypad".

right on mate you did me good!!

EDIT:

worked on my acer aspire 5820TG

---

### Post by leorolla on 2011-09-13
Thanks!

I have a standard ASUS laptop, with USA International (with deadkeys) layout, and this workaround did the job for me.

I don't know why suddenly this option appeared checked, I have never set it... (a bug?)

Cheers

---

