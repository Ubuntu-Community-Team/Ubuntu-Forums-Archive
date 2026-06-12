---
title: "Asus X50V Laptop freezes on battery power"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by CheeseEatingBulldog on 2007-11-01
I have installed an Asus x50v laptop with Gutsy (7.10) and actually gotten the ATI card to play ball with XGL, but the laptop freezes when I remove the power cord. It shows the warning that it is going to battery mode and power icon changes, but then instant freeze.

Adding acpi=off to the grub list got rid off the hang, but now no battery indicator is given.

Is there anything I can do?

---

### Post by CheeseEatingBulldog on 2007-11-05
Bump. 

So there is no sollution for this? This also means that the laptop doesn't turn itself of either.

---

### Post by woole on 2007-11-20
Hi
Same problem...
ASUS F5V, ATI
Please help... It's shame to use windows because this problem.

---

### Post by lord-castigamatti on 2007-12-05
i have the same problem with my asus x50v. all work fine but when i use battery power everythings freeze...

i don't know what to do and i found one person with the same problem.

anyone can help?

please

---

### Post by jannevanhecke on 2007-12-12
i have the same problem with an asus M6000R
Cant anybody help?

---

### Post by jannevanhecke on 2007-12-13
nobody?:(

---

### Post by lord-castigamatti on 2007-12-14
up

---

### Post by Slade Winstone on 2008-01-13
Hi,

I'm running an Asus A8M Laptop running Gutsy 2.6.22-14-generic.

I also managed to get a working system by specifying acpi=off at boot. I have now found kernel boot parameters that will allow ACPI to run giving me the Fesity functionality that I have been missing (although I have been experiencing the odd hang every now and then so be warned...).

Instead of setting acpi=off to disable all ACPI (which previously was the only way of booting my A8M), I now use nosmp noapic which allows some ACPI functionality and a good boot

Add to the end of defoptions and the end of the current kernel in /boot/grub/menu.lst
nosmp noapic

As an aside, this looks like it could be a general problem with many ASUS bios as I've googled a couple of people reporting the same issue and there are some posts on the kernel list archives relating to this.

I hope this helps with other ASUS laptops...

Slade.

---

### Post by Slade Winstone on 2008-01-15
Hi again,

Actually this is only semi-solved... switching the ACPI on again and now I'm suffering the notorious lock/hang bug.  Sigh.... :confused: :( It looks like I'll be going back to acpi=off...

I'll try various fixes I've picked p in a couple of threads and report back if I can get ACPI working without the horror hang!

Slade.

---

### Post by lord-castigamatti on 2008-02-25
> **Slade Winstone said:**
> Hi again,

Actually this is only semi-solved... switching the ACPI on again and now I'm suffering the notorious lock/hang bug.  Sigh.... :confused: :( It looks like I'll be going back to acpi=off...

I'll try various fixes I've picked p in a couple of threads and report back if I can get ACPI working without the horror hang!

Slade.

Thanks for your answer. any news from your search?

Thanks again,
lord-castigamatti

---

### Post by lord-castigamatti on 2008-03-06
up

---

### Post by Slade Winstone on 2008-05-02
Upgraded to Hardy, and no change here.  Still experiencing lock-ups UNLESS I specify noacpi or acpi=off.  It's interesting to note that this sort of thing seems to be affecting more and more people.

I suspect in my case, at least, that it's a kernel update/upgrade from a while back and a poor ACPI implementation in my ASUS laptop.

Sigh.... oh well, praps a different laptop next time I upgrade.  My other laptop an Acer didn't have any trouble until the latest Hardy upgrade... :confused:

Slade.

---

### Post by Qphysics on 2008-05-16
Hey I also have an asus x50v and I Can't work on battery because the laptop freezes.
I'm new to ubuntu, and i dont know wat acpi is.

Is there an proper solution found yet??

---

### Post by bin-ich on 2008-06-27
Same problem still exists! added "nolapic" to menu.lst. Laptop starts, but just working with one core. :confused: Please HELP!

---

### Post by CheeseEatingBulldog on 2008-07-17
Has anyone gotten any further with this? Laptop still freezes when not on mains power.

---

