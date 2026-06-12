---
title: "[SOLVED] disable CONFIG_USB_SUSPEND?"
date: 2008-05-18
forum: Hardware
---

### Post by toni_uk on 2008-05-18
found this in regards of a problem I have with my USB - anyone here who knows how to disable CONFIG_USB_SUSPEND on Ubuntu 8.04?

Cheers!

> Re: Error -71 on device descriptor read/all
Previous message: [thread] [date] [author]
Next message: [thread] [date] [author]
From: Chuck Ebbert <cebbert@...>
To: Renato S. Yamane <renatoyamane@...>
Cc: <linux-kernel@...>, USB development list <linux-usb-devel@...>
Subject: Re: Error -71 on device descriptor read/all
Date: Tuesday, June 19, 2007 - 12:17 pm

On 06/19/2007 10:45 AM, Renato S. Yamane wrote:
quoted text
> Hi, > I see this in dmesg: > usb 1-1: device descriptor read/all, error -71 > > Using 2.6.21.1 > > Someone know what it is? >

Try disabling CONFIG_USB_SUSPEND



link to forum is:
[http://kerneltrap.org/mailarchive/linux-kernel/2007/6/19/106270]("http://kerneltrap.org/mailarchive/linux-kernel/2007/6/19/106270")

---

### Post by toni_uk on 2009-01-06
The problem had to do with the autosuspend of my USB ports - solution on post 7 of this thread:

[http://ubuntuforums.org/showthread.php?t=797789](http://ubuntuforums.org/showthread.php?t=797789)

Hope it helps others with the same problem.

---

