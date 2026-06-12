---
title: "Dell D600 + internet connection"
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by Copps on 2006-09-27
I've recently installed Ubuntu onto a Dell Latitude D600. After using firefox for a while (usually 5-10 minutes) my ethernet link goes down. At first I thought the system was hanging because everything (inc. mouse pointer) freezes. After hard rebooting and the same problem occurring again, I noticed  I could still type to the command console.

I checked out /var/log/messages and have the following in there:

```
Sep 27 22:40:33 laptop1 kernel: [17180323.780000] tg3: eth0: Link is down.
Sep 27 22:40:35 laptop1 kernel: [17180325.780000] tg3: eth0: Link is up at 100Mbps, full duplex.
Sep 27 22:40:35 laptop1 kernel: [17180325.780000] tg3: eth0: Flow control is on for TX and on for RX.
Sep 27 22:43:01 laptop1 kernel: [17180470.804000] tg3: eth0: Link is down.

```

And this time it hasn't come back (posting this from another PC). The system freezes for about 5 seconds at a time, then works for 1 sec, then freezes ... the network connection icon in the taskbar shows as disconnected.

Anyo troubleshooting ideas? Or other log/system files that might point me toward a solution?

---

