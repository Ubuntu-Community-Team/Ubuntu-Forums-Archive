---
title: "Sony Vaio VGN-S4"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by quik on 2006-06-03
I recently bought a Vaio VGN-S4 laptop. I was warned that linux didn't go to well with it.

Dapper came out and I tried it. Everything seemed fine, until I tried to shutdown/reboot it. It just freezes down...

Can someone help me? Is there any issue with the ACPI on this particular laptop?

---

### Post by NikoC on 2006-06-04
I have the same problem on the same machine, but haven't found a solution yet...

---

### Post by Herios on 2006-06-04
i have the sony vaio tx650p had same problem. fixed it using a thread "breazy on tx650" a most helpful thread. it hasn't been that active lately. might be able to fix your problem there. just do a thread searh for "sony vaio tx650".

hope that helps

---

### Post by quik on 2006-06-04
In an attempt to get some Linux working on the beast, I installed Breezy which, indeed, was now able to shutdown the laptop but couldn't also reboot (freezed the same way as in Dapper).

The provided solution, precisely for Breezy, worked... although it presents me with a blank screen for a few seconds before actually rebooting.

Gotta reinstall Dapper and try the same solution to see how it goes... but I'm starting to consider only using XP on the thing... I'm getting a little bit disapointed with all this, since I suspect the acpi isn't working that well to the point the fan is always on...

---

### Post by NikoC on 2006-06-05
I think we can blame sony for that ;-)
There's also something weird going on: when Dapper reboots and you want to enter BIOS setup by hitting F2, the laptop just hangs... when you press ctrl+alt+del to reboot again and then F2 it works fine...

---

### Post by 89c51 on 2006-06-05
i have a S4hp/b and running dapper since beta (clean install) and everything works great (except hibernate/suspend)

the only thing that is weird is that restart takes more time than it used in hoary (the previous OS of the laptop)

also some locks in gnome (mouse moves but cant open/click on anything) -but a ctrl+alt+backspace solves it

---

### Post by quik on 2006-06-05
Another thing I noticed was that the fan seemed to be always on. So, besides taking 2/3 times more to boot and not being able to shutdown/reboot properly, the power management sucks.

Linux is OK in the workstation, but definitely not in the laptop.

---

### Post by 89c51 on 2006-06-06
[QUOTE=quik]Another thing I noticed was that the fan seemed to be always on. So, besides taking 2/3 times more to boot and not being able to shutdown/reboot properly, the power management sucks.

Linux is OK in the workstation, but definitely not in the laptop.[/QUOTE]

do you boot linux with acpi off???

---

### Post by quik on 2006-06-06
If by acpi off you mean passing "acpi=off" in grub, no.

It lists sonyacpi in "lsmod", but I think it doesn't manage acpi quite well as windows... as I said before, the fan seems to be always on...

---

### Post by 89c51 on 2006-06-06
its weird because on the same laptop (with dapper) everything just worked (except suspend/hibernate) 

maybe try and reinstall it :confused:

---

### Post by ilbozo on 2006-06-06
same problem with vaio vgna417m... no solution! But i saw an interesting thing (i think). During the installation my notebook rebooted properely! Any difference between installation reboot and normal reboot?! (I used alternative cd)

---

### Post by quik on 2006-06-06
Yes, indeed the same happened here. I never thought about that... now the whole issue gets a bit stranger... I don't think it makes any sense having different kind of reboots, since the purpose is always the same.

Nevertheless, I'll try installing Dapper-alternate, since a couple of people told me there is a difference between the packages in this one and Dapper-desktop, the one I first tried.

Wish me luck :)

---

### Post by quik on 2006-06-12
I give up.

Installed Ubuntu Dapper Alternate and, as usual, it doesn't Shutdown/Reboot.

I would like to know how you did it to make it work flawlessly in your S4HP/B, 89C51... since I have the exact same model :/

---

### Post by 89c51 on 2006-06-13
[QUOTE=quik]I give up.

Installed Ubuntu Dapper Alternate and, as usual, it doesn't Shutdown/Reboot.

I would like to know how you did it to make it work flawlessly in your S4HP/B, 89C51... since I have the exact same model :/[/QUOTE]

i really dont know :confused: :confused: it just worked

whats your Bios version??

mine are
```
Bios Version: R0091V0
EC Bios Version: RK091V0
Video Bios Version: V0N44_12
```

---

### Post by quik on 2006-06-13
mine seem to be more recent:

```

BIOS Version: R0092V0
EC BIOS Version: RK092V0
Video BIOS Version: V0N44_16

```

*argh* :)

---

### Post by 89c51 on 2006-06-13
[QUOTE=quik]mine seem to be more recent:

```

BIOS Version: R0092V0
EC BIOS Version: RK092V0
Video BIOS Version: V0N44_16

```

*argh* :)[/QUOTE]

yeah they are the latest 

i didnt installed them because there is no way to do it under linux and i dont have windows

maybe you can find the older bios or wait the developers to fix it

if you want something else i ll be pleased to help

---

### Post by quik on 2006-06-15
Today I updated the Ubuntu in my laptop hoping that the new kernel (2.6.15-25) and the updates to nvidia-glx would bring my pain to an end :P

The good news: the problem with the sound was resolved. It now works correctly, despite the Fn-Keys messing around with the wrong parameter in the volume control mixer (they change the headphones volume and not the pcm).

The bad news: the darn thing still isn't able to shutdown/reboot properly, requiring a cold shutdown everytime :/

---

### Post by 89c51 on 2006-06-20
there was an acpi-suport update today

any good news???

---

### Post by quik on 2006-06-21
unfortunately, no.

still no shutdown/reboot. screen blacks out and nothing happens... :(

---

### Post by spider007 on 2006-10-19
I updated from breezy to dapper and when I boot with the old kernel from breezy (2.6.12-10) shutdown works fine but soundcard and wireless won't wok anymore(I guess I updated the correspunding driver modules so tey are not available anymore). So maybe we can fix the problem by comparing the configuration of the new 2.6.15-27 kernel with the old one???

flo

---

