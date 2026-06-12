---
title: "Graphic interface doesn't start"
date: 2006-10-08
forum: Hardware &amp; Laptops
---

### Post by ThomasD on 2006-10-08
I've had a weird problem:

the machine is a Compaq Presario R3000 (P4 3ghz, 1.2gb ram, ati mb and video).
The live CD works perfect, but when I start from a fresh install, the OS loads fine, the login screen comes up, but it stops there. Instead of having the logo pop up with the icons, etc it stays on an empty brown screen.
the OS runs though, I can go to a console. dmesg doesn't return anything weird.
btw, edgy does the exact same thing.
I tried acpi=off, noapic, etc same problem

so obviously there's a problem in the init of the window manager, but I do not know WHERE to look. What log should I look at, or what test should I do?

I also tried to delete .gnome and .gnome2 from the home folder, same problem

---

### Post by gigiya on 2006-10-08
I had the same problem (after installing Efty, though) and didn't find any solution after awhile so I just reformatted with Dapper.

---

### Post by wieman01 on 2006-10-08
Had a similar problem. My solution was to wait for 20 - 30 minutes & the Windows manager plus icons would finally appear. Could you try that?

---

### Post by dolphinsonar on 2006-10-08
Try reinstalling ubuntu desktop, its harmless if that is not your problem, but if it is it will fix it with minimal tweaking.

---

### Post by ThomasD on 2006-10-08
I've reinstalled a few times with no luck

with Dapper: I need acpi=off and IF I force a fsck on reboot, it will start, no fsck, no start :S
with Edgy, it simply doesn't start, but the live CD boots no problem.

The video is fine, but I tried to force VESA just to see.. same thing.

about waiting 20mn or so, I tried that in the past and tracked it down to a dhcp/wireless problem, when I disabled the interface it worked fine (well, when it was booting)


ok, now I'm not a linux expert, but --if I'm not mistaken-- once the login screen is up, the gui should be working, right? so I guess the rest is all scripts?

with Dapper, I get the following results:
- no boot options: brown screen
- force fsck: load task bar, but it's not responsive, no icon on desktop
- force fsck / noacpi: works sometimes, but not always

I also tried with two Bios revision (last and previous), same thing. Now, I know that ACPI doesn't work properly as Windows report problems and Edgy reports an APIC problem right away (apic not connected to timer or something like that), but acpi=off noapic will not help either :confused:

if the problem is in a gdm script (this is a guess), how can I debug this?

---

### Post by ThomasD on 2006-10-09
I reinstalled ubuntu desktop, same crap

so, I did a fresh reinstall, first reboot.. same problem

Can anyone point me to what log I should look at or if there's a verbose setting I should turn on somewhere? I mean the OS runs, so there has to be something I can look at

---

