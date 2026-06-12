---
title: "Canon MP140 will not print"
date: 2021-01-21
forum: Hardware
---

### Post by torbentf on 2021-01-21
Hi,
I have tried to install Canon MP140 printer under Ubuntu 20.04 the normal way, but I dont find the driver in the list. MP140 is installed. The scanner works.

From the Internet I got two suggestions:

$ sudo apt install printer-drive-gutenprint
...
Unable to locate package printer-drive-gutenprint *******NO SUCCESS



$ sudo add-apt-repository ppa:thierry-f/fork-michael-gruz
- cangearmp2 driver add the 10/2019
- Cnijfilter2 driver add the 10/2019
- UFRII driver add the 10/2019

$ sudo apt update

$ sudo apt install cnijfilter2 scangearmp2 cndrvcups-utility *******probably SUPERFLUOUS
- Unable to locate package cnrdrvcups-utility

$ sudo apt install cndrvcups-lipslx, ....etc. *******NO SUCCESS

$ sudo apt install cnijfilter2 scangearmp2 *******SUCCESS, but probably SUPERFLUOUS?

Can anyone tell me what I should do next to make it work?
Best regards
torben

---

### Post by slickymaster on 2021-01-21
*Thread moved to **Hardware**.*

---

### Post by CelticWarrior on 2021-01-21
If the scanner part works then very likely the printer part works as well. Most printers do NOT need additional drivers with the latest Ubuntu releases.

---

### Post by kema77 on 2021-01-21
Funny, I had the opposite issue-- could print but not scan with a Canon MX310 on Ubuntu 20.04. For what it is worth, I had success printing after installing these packages using Synaptic:

printer-driver-gutenprint   version 5.3.3-4  (printer driver for CUPS)

libgutenprint9               (runtime for Gutenprint printer driver library)

libgutenprint-common   (support files)


I had lots of trouble getting scanning to work, however. I eventually gave up and purchased software.

---

### Post by brian_p on 2021-01-21
> Unable to locate package printer-drive-gutenprint *******NO SUCCESS

******Typo Alert******

*drive* is *driver*

---

### Post by torbentf on 2021-01-21
Hi Brian,
Thank you very much. That - + some unspecified fiddling - did it.
torben

---

