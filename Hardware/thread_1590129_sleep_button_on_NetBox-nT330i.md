---
title: "sleep button on NetBox-nT330i"
date: 2010-10-07
forum: Hardware
---

### Post by RichardUK on 2010-10-07
I have a NetBox-nT330i running Ubuntu server 10.4, great little bit of kit. I'm using it for a server to connect of some industrial hardware to the internet. The sleep button currently does nothing and i've been trying to wire it in using ACPI so that it can be used to trigger a recue mode for the user. The power button currenlty works and powers down the device so I know the ACPI is working.

This is my sleep event
```

event=button[ /]sleep
action=/etc/acpi/goto-adhoc.sh

```My my test script.
```

echo "this is a test"

```The script is marked as executable...


The idea is that it will reset the wireless card to a tempory open ad-hoc mode so an engineer can connect to it if some bad has happned to normal settings or the network it was on had been lost. A kind of 'I can't connect to the admin page, use get me out of jail free card'

Ta,
Richard e Collins.

---

### Post by markturnip on 2011-01-08
Hey Richard, did you make any progress with this?

---

### Post by markturnip on 2011-01-12
Are button presses logged in any way? 
Can I run an application that reads button presses such as the sleep button?

---

