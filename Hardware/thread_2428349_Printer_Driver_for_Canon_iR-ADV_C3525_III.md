---
title: "Printer Driver for Canon iR-ADV C3525 III"
date: 2019-10-03
forum: Hardware
---

### Post by daniel-patrick on 2019-10-03
I trying to look for a driver for the Printer Model **Canon iR-ADV C3525 III **that's compatible with Linux Ubuntu?

I managed to find the driver from the official Canon [website]("https://www.canon.co.uk/support/products/imagerunner/imagerunner_advance_c3525i.html?type=drivers&driverdetailid=tcm:14-1506758&os=linux&language="), however it's not working.

Any suggestion please?

---

### Post by slickymaster on 2019-10-03
*Thread moved to **Hardware**.*

---

### Post by brian_p on 2019-10-03
You do not need any drivers in order to print. See [https://wiki.debian.org/CUPSQuickPrintQueues.](https://wiki.debian.org/CUPSQuickPrintQueues.)

---

### Post by daniel-patrick on 2019-10-07
> **brian_p said:**
> You do not need any drivers in order to print. See [https://wiki.debian.org/CUPSQuickPrintQueues.](https://wiki.debian.org/CUPSQuickPrintQueues.)

When I click on the URL I get "**Page not found".**

Yes, by default there is no need to have any drivers installed to print. 

However, you are limited to change options when you need to print.

For example, I need to do the below.

1. By default, even though it's a coloured printer, it should print in B/W. Colour should be chosen when printing from the laptop.
2. I need to set permissions accordingly to users on their floor levels. For example, some users can print on Level 5 printer, some on Level 6, some on both and some are not allowed to print.

Users have Ubuntu 18.04.3 LTS and Mac OS X installed on their laptop.

That's why I'm trying to find a specific driver in place.

How can I go around this? 

Thanks!

---

### Post by brian_p on 2019-10-07
> **daniel-patrick said:**
> When I click on the URL I get "**Page not found".**

A misplaced full stop. The correct link ([https://wiki.debian.org/CUPSQuickPrintQueues](https://wiki.debian.org/CUPSQuickPrintQueues)) is on the page you got.

> Yes, by default there is no need to have any drivers installed to print.

However, you are limited to change options when you need to print.

Not at all.

> For example, I need to do the below.

1. By default, even though it's a coloured printer, it should print in B/W. Colour should be chosen when printing from the laptop.

No problem for driverless printing.

> 2. I need to set permissions accordingly to users on their floor levels. For example, some users can print on Level 5 printer, some on Level 6, some on both and some are not allowed to print.

Such restrictions are not set up from drivers.

---

### Post by daniel-patrick on 2019-10-07
> **brian_p said:**
> A misplaced full stop. The correct link ([https://wiki.debian.org/CUPSQuickPrintQueues](https://wiki.debian.org/CUPSQuickPrintQueues)) is on the page you got.



Not at all.



No problem for driverless printing.



Such restrictions are not set up from drivers.



Can you kindly suggest how this can be done then?

---

