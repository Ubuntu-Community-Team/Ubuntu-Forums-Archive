---
title: "Dell E1405 Function Keys"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by noseeme on 2007-01-25
Hello.

I've almost done everything I want to do in this install of Edgy on my Dell E1405 Core 2 Duo laptop with a GMA950 integrated graphics chip, except for one thing: I cannot change the brightness of my screen, and I can not disable or enable the wireless card with the keyboard. Both of these functions use the function key.

I know that my function key is not broken, because functions like CD eject, volume, and the number pad work.
I'm guessing I'm going to need to reconfigure xorg to some extent.

Does anyone know how I can fix this?
Thanks.

---

### Post by antar on 2007-01-26
Those are actually BIOS settings.

Reboot, hit F2 when you see the Dell screen. The last section has the options to enable this stuff.

Best of luck!

---

### Post by The_night on 2007-01-26
Actually, if you updated your bios to the newest version, anything past a.05, then your brightness controls will not work.  see [http://www.ttuttle.net/blog/computers/software/dell-inspiron-e1405-bios-a05-linux-brightness-hotkey-fix.html]("http://www.ttuttle.net/blog/computers/software/dell-inspiron-e1405-bios-a05-linux-brightness-hotkey-fix.html") wish that I knew how to fix this because I have the same problem...  :confused:

---

### Post by tschneiter on 2007-02-01
The strange part is that the controls work while booting, but only after the computer is into X will specific function keys not work. Strange stuff. :confused:

---

### Post by noseeme on 2007-02-08
Thanks for your posts, but I still have not got the function keys working.
Anyone else have any ideas?

---

### Post by tschneiter on 2007-02-08
Ive heard from more than one source that downgrading the bios to a05 will get the keys working properly again. I saw no real improvements going from a05 to a08 anyways; let me know if you try it and it works :)

---

### Post by jabao_ron on 2007-03-27
if you are using the Media Direct buttons on front of your pc, then they are configurable. i have the same question about the wireless button, because when i turn it on, the bluetooth LED stays on and it seems to be working because when i do *lspci*, it appears as an installed device.


if you get an answer from this, please inform.

---

### Post by jabao_ron on 2007-03-27
in my pc the brightness buttons (Fn + Up/Down) they work perfectly. 
the mute button also (Fn + End), and the volume up/down too (Fn + PgUp/PgDn).

i've tried all of them, and they work perfectly.
probably a BIOS issue.
check the BIOS settings.

---

### Post by bigfatdummy on 2007-03-28
My Bluetooth light is always on as well. Since I dont use bluetooth with this laptop, I'll just disable it.

---

### Post by cleatsupkeep on 2007-04-11
> **noseeme said:**
> Hello.

I've almost done everything I want to do in this install of Edgy on my Dell E1405 Core 2 Duo laptop with a GMA950 integrated graphics chip, except for one thing: I cannot change the brightness of my screen, and I can not disable or enable the wireless card with the keyboard. Both of these functions use the function key.

I know that my function key is not broken, because functions like CD eject, volume, and the number pad work.
I'm guessing I'm going to need to reconfigure xorg to some extent.

Does anyone know how I can fix this?
Thanks.

This is actually a bug in the ACPI drivers in the current kernel, it's actually pretty funny, someone found the method that causes this bug. This is a paraphrase, but:

int acpiBrightness(*arguments*)
{
     //write me
}

What you need to do is:

Go to the command line:

sudo gedit /etc/modprobe.d/blacklist

and add to the bottom

"blacklist video"              (Without quotes)

and then restart X, and it should work. Once again, it has to do with the ACPI brightness level settings.

Let me know if this works,
Brian

---

### Post by Limitlesschannels on 2007-04-13
Will that work for many other laptops or specifically Dell?  I am using a Sony FJ series and have been working on the Fn Key problem for quite some time.  Nothing in the syntax suggests Dell, but if there is anything you can say on that subject, please post.
If you aren't sure, I guess I can try it and see.

---

