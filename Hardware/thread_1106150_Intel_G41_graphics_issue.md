---
title: "Intel G41 graphics issue"
date: 2009-03-25
forum: Hardware
---

### Post by vtach3743 on 2009-03-25
Hi, I installed 8.10 then I tried Jaunty and I have the problem when I run video it is choppy. The MB I'm using is an Intel DG41TY and the resolution I'm set at is 1440x900. Any ideas?

---

### Post by middlechild on 2010-01-02
Working with 9.10 and same motherboard, using the on-board graphics port.  Screen went to black, with a single white dot remaining upon boot a couple of days ago, reinstalled to fix.

Investigating issue, found the following output:
lspci | grep VGA:
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

Looking at the web site for Free Software Foundation ([http://www.fsf.org/resources/hw/video](http://www.fsf.org/resources/hw/video)) found that the Intel Corporation 4 series CIGC is only supported in "rev 07"

The question then is how much difference, is this worth going out to buy a new video card to permanently fix the display problem?  

Has anyone else discovered a similar issue, with revisions of motherboard chipsets?

---

