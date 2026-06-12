---
title: "Mythbuntu 9.10 will not boot up"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-11-06
I have a grub2 boot partition on (hd0,1). I installed Mythbuntu 9.10 32bit on (hd0,9), a logical partition and I installed the boot loader into that partition using the advanced option at the end of the installation process. I have the grub2 on the boot partition set to chainload Mythbuntu on (hd0,9).

What happens is that Mythbuntu seems to go through the bootup process correctly but it stops at the console login and the whole screen is flashing/blinking. In fact, even keyboard input is sporatic. I'm afraid the system is in a state that could damage the harrdware. It is not even possible to type enough to log in. The only option is to reboot.

I thought the problem was related to a defective installtion, so I installed fresh again (reformatted partition). I get the exact same problem after the second install.

I have Kubuntu, sidux and openSUSE on other partitions. All will boot up correctly. Mythbuntu is the only OS that will not boot. However, if I install Mythbuntu without putting the boot loader into its partition (i.e., using the whole hard drive) Mythbuntu will boot correctly on this computer.

My computer is a Thinkpad T61p.

There is some background in [this thread]("http://www.linuxquestions.org/questions/linux-general-1/opensuse-wont-boot-after-i-resized-its-partition-grub2-related-766528/"), but it is largely unrelated.

---

