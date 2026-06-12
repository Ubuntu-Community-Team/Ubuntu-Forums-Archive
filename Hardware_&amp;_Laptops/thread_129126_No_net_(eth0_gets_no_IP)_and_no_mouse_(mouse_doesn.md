---
title: "No net (eth0 gets no IP) and no mouse (mouse doesn't work in X11) after fresh install"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by Kethinov on 2006-02-13
Doing either a fresh install of Breezy or Dapper produces the same result: no working eth0 and no working mouse in X11.

When I drop to terminal, become root, and run the command "dhclient eth0" it responds with several "DHCPDISCOVER" lines, then finally "No DHCPOFFERS received." This results in eth0 not having an IP.

Relevant specs:

NIC: lspci reports it as: Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Mobo: ASUS A7M266-D
Proc: Athlon MP 1200mhz (2x)

I suspect this is a result of kernel 2.6's apparent poor compatibility with my mobo. I've had very similar issues with other distros. Simply using kernel 2.4 in Debian resulted in a usable system. However, kernel 2.4 is not any longer a viable solution for me -- I need to be modern! (An upgrade to kernel 2.6 in Debian also produced these problems.)

Here are some boot specifics that may be useful: the boot process takes utterly forever. This is partially related to the bad network config, because it tries for a good while to get that up and eventually results in "fail." But also it also exerts slowness here as well:

Shortly after the Ubuntu pretty framebuffer screen displays "Loading modules..." the screen drops to the traditional kernel boot screen with the black and white text. Among the kernel message spam, I get the following errors:

Failed to mount /selinux/: No such file or directory

(insert long wait...)

* Detecting and activating hardware...
[bunch of numbers] shpchp: shpc_init: cannot reserve MMIO region

(insert much longer wait...)

[bunch of numbers] amd76xrom amd76xrom_init_one() unable to register resource 0xffff0000-0xffffffff - kernel bug?

--

I could really, really, use some help clearing this up. I am not a newbie -- My main desktop machine is a Breezy machine that I've kept in great shape since the Breezy release. Prior to that, it was an FC4 machine, and an FC3 prior to that. Before my FC days, it was stock Debian. Before that it was Gentoo. I am very good with Linux... but this other machine's hardware just refuses to cooperate! :(

---

