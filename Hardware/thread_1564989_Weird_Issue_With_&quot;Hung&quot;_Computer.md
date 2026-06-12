---
title: "Weird Issue With &quot;Hung&quot; Computer"
date: 2010-08-31
forum: Hardware
---

### Post by tom purl on 2010-08-31
About once a week, my Ubuntu system just "hangs".  I am unable to ssh into it or ping it.  Also, I can't use it from the local keyboard and monitor.  I have also tried switching to one of the tty virtual terminals, but I can't.  After rebooting the computer, it seems to work well.

To troubleshoot the issue, I looked at the /var/log/messages file.  All I found though (and it's a lot to look through) is a *lot* of USB-related messages that basically say the following repeatedly:  

* disconnecting USB port
* reconnecting USB port
* finding USB hub
* finding keyboard and mouse

I have an rf-wireless keyboard and mouse that go through a single USB port.

That USB message is repeated about every 5 seconds, every day.

Could something like this possible cause my computer to become unresponsive?  My initial guess is no.  I started having this hanging problem on 8/21, but I've been getting a ton of these USB message for over a month now.

Also, nothing has really changed on my computer over the last two weeks.  I installed a new graphics card and ram a couple of months ago, but they both seem to be working well.  Also, I installed a new DVD ROM about a month ago.

Does anyone know of anything else I can do to troubleshoot these issues?  Outside of the USB error messages, I really don't have any other information that points to a potential problem.

Thanks in advance!

Tom Purl

---

