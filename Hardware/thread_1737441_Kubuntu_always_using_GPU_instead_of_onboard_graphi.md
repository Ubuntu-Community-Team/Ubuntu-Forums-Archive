---
title: "Kubuntu always using GPU instead of onboard graphics"
date: 2011-04-23
forum: Hardware
---

### Post by cnkt on 2011-04-23
Hi,

I have got a Asus N53SN laptop with onboard Intel graphics and a Nvidia GT 550M graphic card.

On Windows, system uses Intel onboard graphics (i can understand this from the led indicator on keyboard) whenever i want to use Nvidia i can right click the program icon and select "Use high performance Nvidia graphics" bu on ubuntu the indicator is always on and system uses Nvidia.

This is not good because it uses more power, produces more heat and more noise becuase fan is always turning.

How can i fix this?
Thanks.

---

### Post by Yellow Pasque on 2011-04-23
You probably can't, unless you have a BIOS switch to disable the nvidia card. Some people have managed to shut off the nvidia card with acpi_call script. Sadly, nvidia hybrid graphics are not supported on Linux.

---

