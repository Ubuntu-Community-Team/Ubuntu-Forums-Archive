---
title: "Hardy to Intrepid upgrade - Boot issue"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by Zwack on 2009-04-07
Well, the title explains the basics... but this one is strange.

I upgraded a perfectly working hardy to intrepid on my laptop (HP Pavilion dv9700) and now I have a boot issue.  Once it's booted it runs perfectly, but it won't boot properly.  I've tried going into the grub menu and removing quiet and changing splash to nosplash.  It doesn't help, I see the same symptoms but nothing obvious as to a cause.  

So, what happens is Grub starts, and hangs very quickly.  It will basically remain paused unless I press control-alt.  When I do that it will move on.  once it gets the kernel loaded and init running it carries on on it's own.

Anyone got any ideas?

Z.

---

### Post by Zwack on 2009-04-07
On further investigation it's not Grub it's the kernel...

Kernel 2.6.27-11-generic doesn't want to load properly unless control is held down.  

I can switch back to 2.6.24-23-generic and it works perfectly.  The only "unusual" part of my install kernel wise is that I have to use a patched madwifi driver to get the wireless card to work.  

Z.

---

### Post by Zwack on 2009-04-08
It is an issue with the 2.6.27 kernel series.  I moved up to Jaunty (I figured it couldn't be any more broken...) and the problem has gone away.

Z.

---

### Post by Zwack on 2009-08-12
I should have updated this long ago...

However it wasn't a kernel issue per se.

After it happened again a few times I worked out that it would boot normally when the laptop was plugged in, but would hang when it was on battery power.  The solution was to add acpi=noirq to the kernel options in /boot/grub/menu.lst and run update-grub.

I hope that this helps anyone with a similar problem.

Z.

---

