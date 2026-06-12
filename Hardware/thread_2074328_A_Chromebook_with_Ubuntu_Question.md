---
title: "A Chromebook with Ubuntu Question"
date: 2012-10-21
forum: Hardware
---

### Post by nyamina on 2012-10-21
Just thinking about getting a Chromebook - I know that there is ChrUbuntu out there, I'm just wondering if I can just turn off secure boot (or whatever it is), boot off a straight ahead 12.10 live USB and install it, or would I have to use ChrUbuntu?

Also, can I use just ChrUbuntu, or does it just dual-boot it? And does anybody know when 12.10 is out?

Thanks =)

---

### Post by caffeinatedev on 2012-10-31
I believe the whole point of Chrubuntu is that normal Ubuntu doesn't have drivers available for a Chromebook. I imagine you would have to keep the ChromeOS partition, if for no other reason than to keep your *book from screwing up.

---

### Post by grahammechanical on 2012-11-01
Have a read though this:

[http://www.omgubuntu.co.uk/2012/10/ubuntu-12-04-up-and-running-on-samsung-arm-chromebook]("http://www.omgubuntu.co.uk/2012/10/ubuntu-12-04-up-and-running-on-samsung-arm-chromebook")

I think that the fact that the Chromebook is a ARM CPU based device is why a standard Ubuntu live CD will not be any good.

> Getting Ubuntu up and running on a Chromebook &#8211; ARM or Intel &#8211; is not a straightforward process. It requires effort on the part of the developer in customising and compiling the Chromium OS kernel to work with Ubuntu.

Installing Ubuntu is not easy , either. By default the bootloader of Chromebooks are signed and locked. You can&#8217;t use a live USB and install Ubuntu, Knoppix or Hannah Montana Linux in the &#8216;typical&#8217; fashion.

But Google make it very easy to switch the lock off (and enter &#8216;development mode&#8217;), allowing you to dual-boot between Ubuntu and ChromeOS.

Regards.

---

