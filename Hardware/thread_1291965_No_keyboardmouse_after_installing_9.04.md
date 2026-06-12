---
title: "No keyboard/mouse after installing 9.04"
date: 2009-10-15
forum: Hardware
---

### Post by adlin5000 on 2009-10-15
Here's the issue. I'm installing Ubuntu on my bosses HP. LiveCD and install work just fine. After install, the mouse and keyboard just stop working. The keyboard works up to the login screen. at that point not even the numlock/capslock work.

Its a HP Pavilion pj508aa-aba a710n with a HP/Asus Kelut 2.02 MB and a HP keyboard and mouse (from a different system).

Thanks for any help.

---

### Post by Giblet5 on 2009-10-15
Is the keyboard/mouse USB, PS/2, or mixed?

Is there a KVM in the middle?

How old is the BIOS? (it should display a date when you hit Tab to see the self-test details)

---

### Post by Giblet5 on 2009-10-15
Note: some HP "multimedia" PS/2 keyboards are defective. They will work and fail intermittently. HP recalled them, but there are still a LOT of those in the wild...

---

### Post by adlin5000 on 2009-10-15
Both keyboard and mouse are ps/2.

Had to look up what a KVM was. No, they are both connected to the MB

According to lshw the bios is Phoenix ver 3.10 (07/26/2004)

It is a HP "multimedia" keyboard, but it works fine when I boot with a CD. Its only when I boot with the new install both it and the mouse just dont work.

Hope that helps.

---

### Post by Giblet5 on 2009-10-15
> **adlin5000 said:**
> Both keyboard and mouse are ps/2.

Had to look up what a KVM was. No, they are both connected to the MB

According to lshw the bios is Phoenix ver 3.10 (07/26/2004)

It is a HP "multimedia" keyboard, but it works fine when I boot with a CD. Its only when I boot with the new install both it and the mouse just dont work.

Hope that helps.


I would check [www.hp.com](www.hp.com) for newer BIOS. That one's older than my 12 yo HP Kayak's BIOS.

If that doesn't fix it, I'd verify that "Plug-n-Play OS" is disabled in BIOS setup.

If it still doesn't work, I'd test by swapping in a different keyboard and mouse.

That's all I got.

---

### Post by adlin5000 on 2009-10-15
I should probably update the bios regardless.

Now that I think about it, I believe PnP OS was enabled. I'll give that a try.

I tried the keyboard from my system and got the same results.

---

### Post by adlin5000 on 2009-10-15
Ok. PnP OS was on, I disabled it, but still nothing. Tried reinstalling after that and it seems to be working.

Thanks for the help.


Now I just need to figure how to update the bios with the windows exe that HP has.

---

### Post by Giblet5 on 2009-10-15
> **adlin5000 said:**
> Ok. PnP OS was on, I disabled it, but still nothing. Tried reinstalling after that and it seems to be working.

Thanks for the help.

Now I just need to figure how to update the bios with the windows exe that HP has.


I keep a cheapo USB stick with DOS on it, just for updating BIOS.

To make a bootable DOS stick, [follow these directions]("http://www.bootdisk.com/pendrive.htm").

---

