---
title: "SATA hardware RAID-1 not working"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by gaebriel on 2006-12-27
Hi all, I have a couple of computers with different models of built-in SATA RAID controllers and I haven't been able to get either of them to work. I'm wondering if it's just something I'm doing wrong, or if it's the hardware, or if it's even possible to get any systems with hardware SATA RAID controllers to work. If anyone has successfully installed linux (any distro, but preferably ubuntu) onto a system with an onboard SATA RAID-1 configuration, please let me know the details. If you can figure out why neither of my systems work as well, that would be awesome. 

Here's my setup and what happens. Any insights would be truly appreciated. TIA: 

On my Supermicro X7DAE, I enable enhanced SATA support and then enable RAID support. After the system boots (I've tried using the Intel BIOS and the Adaptec BIOS but both have the same result), I enter the controller's setup facility and create a mirrored (RAID-1) volume using two identical hard drives. I reboot and the system says the volume is configured correctly and loads the BIOS successfully it says. 

Then I boot off the Ubuntu CD (I've used the server and desktop model) and when it's time to choose the hard drive to install on, both /dev/sda1 and /dev/sda2 show up, but no RAID volume does. I can install to either disk but then I can't boot from the hard disks unless I disable the hardware RAID support in the BIOS, at which point the hardware RAID is obviously not in use. 

I've had the exact same situation with my other system, a Gigabyte 8KNXP motherboard. The SATA controller on the Supermicro board is an Intel ESB2 SATAII controller, and the SATA controller on the Gigabyte is a Silicon Image Sil3114. 

gaebriel

---

### Post by tszanon on 2006-12-27
It seems that those RAID controllers you have are not real hardware-RAID (they depend on drivers to work).

In this case, if you have a good computer, I suggest that you forget about the RAID controller and use software-RAID. You won't notice the performance decrease.

---

### Post by psusi on 2006-12-27
Yes, you have a fakeraid controller, not a real hardware raid.  Read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by gaebriel on 2006-12-31
Thanks for the posts. I guess I assumed, incorrectly, that since the motherboards claimed to have RAID controllers that it was truly hardware based. The [https://wiki.ubuntu.com/FakeRaidHowto]("https://wiki.ubuntu.com/FakeRaidHowto") link is great.

---

