---
title: "AMD Ryzen 9 3950X on Ubuntu?"
date: 2021-02-08
forum: Hardware
---

### Post by santanine on 2021-02-08
Hi!

Just bought a box with an AMD Ryzen 9 3950X CPU ([https://www.amd.com/en/products/cpu/amd-ryzen-9-3950x](https://www.amd.com/en/products/cpu/amd-ryzen-9-3950x)) and a Gigabyte B550 AOURUS Elite V2 motherboard ([https://www.gigabyte.com/Motherboard/B550-AORUS-ELITE-V2-rev-10#kf](https://www.gigabyte.com/Motherboard/B550-AORUS-ELITE-V2-rev-10#kf)), wondering how different Ubuntu versions support this hardware?

I have important software that only runs on Ubuntu 16.04, wondering if I could just install 16.04.7, without getting screen freezes or any other unexpected problems when I in the future start to push the Ubuntu and the hardware.

If 16.04 is too old, I still want to stay with as old Ubuntu as possible (perhaps 18.04) since I want to use software that will not install on new Ubuntu versions.

Many thanks for replies (starting to install 2/11/21)

---

### Post by CelticWarrior on 2021-02-08
Welcome.

In a nutshell the answers are no, no and no.
- Support for Ubuntu 16.04 ends in April unless you want to pay for ESM but then
- Ryzen 9 needs the newest kernel, graphics stack and drivers, brand new [I]everything.
[/I]- Everything that works in 18.04 works in 20.04 or 20.10.

---

### Post by Yellow Pasque on 2021-02-09
I know Ubuntu 18.04 can boot Zen2 CPU's, so 16.04.7 should work fine too (except for maybe some smaller things like temp monitoring):
Test the LiveUSB before installing though.

The problem with 16.04 is that it is nearing EOL, as CelticWarrior pointed out.

---

### Post by mastablasta on 2021-02-10
> **santanine said:**
> 

I have important software that only runs on Ubuntu 16.04,

great software design huh? 

is virtualisation an option?

Options: 
Ubuntu ESM 
Try to get software running on at least 18.04 or 20.04

you have to get the latest kernel installed somehow...

---

### Post by santanine on 2021-02-10
> **Yellow Pasque said:**
> I know Ubuntu 18.04 can boot Zen2 CPU's, so 16.04.7 should work fine too (except for maybe some smaller things like temp monitoring):
Test the LiveUSB before installing though.

The problem with 16.04 is that it is nearing EOL, as CelticWarrior pointed out.

Thanks for different expert views, including CelticWarrior! Showing Ryzen 9 (Zen2) at least may work on 16.04.07 is great, but since 16.04 support is almost gone, it is also a good time point to move to a newer Ubuntu. Perhaps moving to the newest version is the best if it is true everything installs there compared to 18.04. I will at least give it a shot to try to install my old software on 18.04 or higher before sticking to 16.04.

After my first post here I am thankful for this community that rocks!

---

