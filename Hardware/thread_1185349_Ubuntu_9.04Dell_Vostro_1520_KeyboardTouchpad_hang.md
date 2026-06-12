---
title: "Ubuntu 9.04/Dell Vostro 1520 Keyboard/Touchpad hang"
date: 2009-06-12
forum: Hardware
---

### Post by jimshawnz on 2009-06-12
I have just installed 9.04 on  brand new Dell Vostro 1520 laptop. The keyboard and touchpad hang 90% of the time after booting. If I plug in a USB mouse it reduces the hangs to maybe 20% of the time. 

I haven't tried a USB keyboard as well but it seems to me like there is a problem with the HID drivers on this system.

I have seen several other similar problems logged but no solutions. Anyone got any ideas of how to tackle this. 

BTW I have Ubuntu 8.10 running on several other laptops with no problems.

Jim

---

### Post by TrineH on 2009-06-12
I have just upgradet to Ubuntu 9.04 on my AspireOne and have problems with the buttons on both the touchpad and my USB mouse.

When using $xinput test (it displays the actions of the devices) I discovered something funny.
When pressing the buttons on my mouse this actions happened:
left1 button press + relase
left + right              2
right                     3
scroll down               4
scroll up                 5

When pressing on the touchpad:
left                      no action at all
right                     3 button press + relase
left + right              3

The only thing I can do now on my AspireOne (I can not left click) is to open Terminal by pressing Alt+F2.

This is the second time I install 9.04 and I lost mouse controll both times.  But inbetween the mouse and touchpad worked correct.

I think we can have the same problem even if my problem seems a little different.  My guess is that it is a register/variables somewhere which is not correct set when starting the machine and perhaps used by other process so that suddently everything can start to work again.  Can this be a problem with syndaemon?

---

### Post by patrick82 on 2009-07-04
I have solved the problem on my Vostro 1320 in
/boot/grub/menu.lst

add
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
to the kernel line.

kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=91013859-dfec-4a84-ae8d-21233f16c89a ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop

:guitar:

---

### Post by xavier83ar on 2009-09-01
Thank you so much!! you've saved my life! :D 
I have a vostro 1320 and have the same problem, I tried  everything to solve this issue without success.
It seems to be a problem with the interrupt controller and not only with ubuntu happens, I have installed windows 7 and does have the same problem, and after boot two or three times it starts fine.
Anyway, I use ubuntu most of the time. 

Thank you again!! =D>

---

### Post by Mt421 on 2009-09-09
> **patrick82 said:**
> I have solved the problem on my Vostro 1320 in
/boot/grub/menu.lst

add
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
to the kernel line.

kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=91013859-dfec-4a84-ae8d-21233f16c89a ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop

:guitar:

Just got a new vostro 1320, installed ubuntu and had this keyboard/touchpad problem. This little tweak seems to have fixed it so thanks v much!

---

### Post by shivanshtyagi on 2009-10-19
> **patrick82 said:**
> I have solved the problem on my Vostro 1320 in
/boot/grub/menu.lst

add
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
to the kernel line.

kernel          /boot/vmlinuz-2.6.28-13-generic root=UUID=91013859-dfec-4a84-ae8d-21233f16c89a ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop

:guitar:

thanks patrick, though i am curious what this line does ???:confused:

---

### Post by naarkhoo on 2009-12-04
It doesn't work for me !

I am not able to use touchpad after ubuntu karmic booted unless using external USB modem.

Also I use 1320 vostro ...

Listening from you

---

