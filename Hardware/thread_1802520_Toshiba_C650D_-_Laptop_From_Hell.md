---
title: "Toshiba C650D - Laptop From Hell"
date: 2011-07-12
forum: Hardware
---

### Post by jeeves on 2011-07-12
I spent most of the day trying to get Ubuntu Natty (and several other Linux distros) to run properly a new **Toshiba Satellite C650D **laptop. The installations would go fine, but after using the new linux install it would inevitably freeze up so bad that even REISUB could not force the system to reboot. I even tried 'GRUB_CMDLINE_LINUX="acpi=ht"' and "acpi=copy_dsdt" fixes with no success.

Moral of the story, steer clear of this model if you want to run Linux on it.

---

### Post by rook_studios on 2011-07-13
hey there, I have spent the last day and a half having some fun with this laptop. I think I've got it working with Natty (after trying half a dozen kernel versions and wireless drivers).

I installed it by booting the live CD (on a USB) with the "acpi=copy_dsdt" switch (otherwise it was flaky), and doing the normal install (took 2 or 3 tries).

after installing it would freezing randomly after about 1/2 an hour or so, which lead to the fun with kernel versions. from what I see online, the problem is the Atheros wireless drivers (surprise!).

I tried a bunch of stuff, but in the end what seems to have work (current uptime is at 6:00 - much longer than all previous attempts) was upgrading to the 2.6.38-11 kernel. I had to add the pre-proposed source with:
```
sudo add-apt-repository ppa:kernel-ppa/pre-proposed
```

and then install the updated headers and image. you can see the exact package names (after adding the above):
```

apt-get update
apt-cache showpkg linux-headers
apt-cache showpkg linux-image

```
and installing (with 'sudo apt-get install NAME') the packages with inclued '2.6.38-11' in the name.

there's a bunch of suggestions out there to upgrade to the 2.6.39 kernel, but it's been removed from the sources as far as I can see. i'll upgrade to .39 when it's released properly.

hope you get a chance to try it out, and that it works for you!

---

