---
title: "How do I create a script to start DNSCrypt at boot?"
date: 2012-03-23
forum: Hardware
---

### Post by chazinams on 2012-03-23
I've read that I can create a script and add it to /etc/init/ or /etc/init.d/ (not sure which is correct) that will run DNSCrypt at startup automatically (so I don't have to manually start it after every boot).

I've installed DNSCrypt. Now just need the script.

How do I do this?

---

### Post by Paddy Landau on 2012-03-24
Do you wish to start it when you boot the machine or when you log in?

To automatically start when you log in, it's easy. Open Startup Applications. Press *Add*, enter a descriptive *Name*, type your *Command*, enter a descriptive *Comment*, and press *Add*. Log out or reboot; log in.

---

