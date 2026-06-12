---
title: "Strange warm area in Latitude 5591"
date: 2019-02-24
forum: Hardware
---

### Post by jkrawczyk on 2019-02-24
Hi,
I've installed on my laptop two distributions
- first kubuntu 18.4.1
and later
- xubuntu 18.4.2

all is almost perfect but:
strange warm area apeared on the right side to trackpad, near to fingerpront sensor. On kubuntu the heat was more intesive than on xubuntu.
i checked some dell documents like this:
[https://www.dell.com/support/manuals/us/en/04/latitude-15-5591-laptop/lati5591_service_manual/removing-the-system-board?guid=guid-34d15bad-8ef1-417a-92fd-6ba6303bef47&lang=en-us](https://www.dell.com/support/manuals/us/en/04/latitude-15-5591-laptop/lati5591_service_manual/removing-the-system-board?guid=guid-34d15bad-8ef1-417a-92fd-6ba6303bef47&lang=en-us)

and one board seems fit the this place, Dell calls it system board, not mother board.

When i was working on W10 this area was cold. 

Is there any way to check what is the warm component, and how to make it colder?

Best.

---

### Post by slow-speed on 2019-02-25
May I assume you are working all operating systems at the same rate?  Do you have specs on the processor loads for comparison purposes?

If all was the same, I would be concerned as you are.  I would have thought that W10 would have had more overhead than the other two.

---

### Post by jkrawczyk on 2019-02-27
Well, problem is solved.

**powertop** is wery useful tool to find and fix power leaks :).

The issue was that the fingerprint device was working all the time at 100%.

best.

---

