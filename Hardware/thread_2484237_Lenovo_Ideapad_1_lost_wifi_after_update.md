---
title: "Lenovo Ideapad 1 lost wifi after update"
date: 2023-02-20
forum: Hardware
---

### Post by temporos on 2023-02-20
My Lenovo Ideapad 1 (15ALC7) has a RealTek 8852BE wireless network adapter. I had to follow the instructions [here]("https://askubuntu.com/questions/1426695/wifi-not-working-on-ubuntu-22-04-1-with-dual-boot-on-lenovo-ideapad-3") to get the computer connected to Wifi after I bought it, but after that, it was working fine. Today, Ubuntu performed a regular update, and I noticed that update included several "Ubuntu base" components. Now, the Wifi adapter has disappeared again, and it makes me think the update broke the drivers.

I followed the instructions on the askUbuntu site again, but now, the **make -j8** command throws a bunch of errors.

The kernel version is Linux 5.19.0-32-generic.

How can I get this laptop back online?

---

### Post by temporos on 2023-02-21
OK, I fixed it. The update to Ubuntu moved me from kernel 5.15 to 5.19. On the [AskUbuntu site]("https://askubuntu.com/questions/1426695/wifi-not-working-on-ubuntu-22-04-1-with-dual-boot-on-lenovo-ideapad-3"), I followed the link to the [GitHub site]("https://github.com/HRex39/rtl8852be") that contains the driver. There's a section down in the readme about a different process to follow if you're running kernel 5.18 or later. The only difference is the options on the end of the *[FONT=courier new]git clone[/FONT]* command.

```
git clone https://github.com/HRex39/rtl8852be.git -b dev
```

I had to delete the *rtl8852be* folder that was used to install the driver the previous time. Then, I followed the instructions on GitHub for kernel >= 5.18.

Trying to clone the repository was interesting on a laptop with no ethernet port and missing its Wifi drivers. :?

---

### Post by bimblesticks on 2023-04-21
Old thread I know but I thought I should mention for anyone that  stumbles across here that if you're running Jammy Jellyfish you can use  the 6.1 OEM kernel instead of having to compile a driver from GitHub.  It's maintained and supported by Canonical and contains backported  support for the adapter (see here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2002601](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2002601)).

Run `sudo apt install linux-oem-22.04c`

Support will be available on the Jammy HWE kernel some time in August, once the kernel from Lunar Lobster is backported.

---

