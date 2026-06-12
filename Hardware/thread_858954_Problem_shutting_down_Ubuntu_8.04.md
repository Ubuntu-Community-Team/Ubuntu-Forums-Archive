---
title: "Problem shutting down Ubuntu 8.04"
date: 2008-07-14
forum: Hardware
---

### Post by 900math on 2008-07-14
Hi,

I am a pretty new user to Ubuntu 8.04 and everything seems to be running pretty smoothly so far. I had to install my Ubuntu through the Wubi installer since the regular way didn't work for multibooting with Vista.

Something really strange happens when i shut down my computer through Ubuntu though. I press "Shut down" and the ubuntu logo starts counting down and the computer seems to shut down. All the fans stop and the power indicator on the chassi shuts off. But all my USB units, like keyboard, mouse and webcam are still running and i can see the optical light from my mouse still responding (not a wireless mouse).

So i have to restart the computer again and hold the powerbutton for 5 seconds everytime i want to power off it correctly. This does not occour when i shut down my computer trough vista.

Any ideas what to do about this? 

Systemspec for my computer.

Asus a8n-e motherboard
3 gb kvr ram.
Ati HD2600xt graphic (512mb).
3 Harddrives of different sizes, all Samsung spinpoint.

Thank you all in advance.

/Math (sweden)

---

### Post by Hubi17 on 2008-07-14
My cousin had the same problem on his pc. We tried countless settings of acpi etc, but nothing fixed it. In the end it turns out that the splash screen couldn't handle the resolution. After disabling it, the pc shut down perfectly.

To try that method, when booting, in grub:
press e to edit
then select the kernel you are booting
press e again to edit
and remove splash from the end
press enter to stop editing
press b to boot the edited kernel.

if that fixes your shutdown problem, make the changes permanent by editing your grub menu.lst

GL

---

### Post by 900math on 2008-07-15
Ty for the tip!

It didn't solve the issue in my case, same problem even without the splash-screen.

Anyone else that has this kind of issue? Does it have anything to do with Wubi?

/Math

---

### Post by Wheel_nut on 2008-07-15
I had a similar problem when I installed the 8.04 downloaded ISO. My Laptop would hibernate but the Wireless PC Card would remain active. 

A few days later, the CD I requested from Canonical arrived and when I installed from this CD, everything shuts down correctly.

---

### Post by 900math on 2008-07-16
> **Wheel_nut said:**
> I had a similar problem when I installed the 8.04 downloaded ISO. My Laptop would hibernate but the Wireless PC Card would remain active. 

A few days later, the CD I requested from Canonical arrived and when I installed from this CD, everything shuts down correctly.

But isn't hibernation non-supported when using the wubi installer because of looping?

---

