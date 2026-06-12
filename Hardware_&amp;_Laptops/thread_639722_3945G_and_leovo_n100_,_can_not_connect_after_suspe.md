---
title: "3945G and leovo n100 , can not connect after suspend or Hibernate ,wireless problem"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by DO55 on 2007-12-13
hi

the only problem that i have with Ubuntu is losings wireless connection after suspend or Hibernate 

if i  wake up the laptop after suspend or Hibernate  i need to do one of these 

1-some time the wireless work automatically after suspend or Hibernate but its very very  rare 
2-i re-enter SSID and the passkey and some time its work
3-i reboot the system 
4-some time if i reboot the system the wireless dose not connect directly but after 2 or 3 min's
5-some time after reboot the wireless dose not work after 2 or 3 mins  so i re-enter the SSID and passward again and the wireless work again


i have windows and i dont have this problem

in windows its need seconds to connects to the wireless  but ubuntu need 5 min's or more to do the same thing

---

### Post by DO55 on 2007-12-14
Up

---

### Post by DO55 on 2007-12-14
up

---

### Post by DO55 on 2007-12-15
up

---

### Post by aspie on 2007-12-23
I have an ASUS laptop with the 3945ABG wireless card.  I also have exactly the same issue.  Very annoying!  Please let me know if you find a fix

---

### Post by aspie on 2007-12-23
Ah, I just found this.  It seems to work for me, so maybe you should try it.

> **tommie74 said:**
> I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.

---

### Post by DO55 on 2008-01-24
> **aspie said:**
> Ah, I just found this.  It seems to work for me, so maybe you should try it.

thanks for help  but its not work

---

### Post by alexei_colin on 2008-01-24
Similar problem on:
Gutsy with Kernel 2.6.24
Thinkpad T60 with PRO/Wireless 3945ABG Network Connection
using driver iwl3945

I got suspend/resume to work with the newest (8.01) ATI drivers (fglrx), but
wirless device would get lost upon resuming always.

This gets the device back for me:
$ sudo /etc/init.d/hal restart

Try it. A complete workaround would be to add this to some script
and make it execute upon every resume automatically. I'm looking into
this now. But a real fix would be better..

EDIT: To have this run upon every restart, place the following script
into /etc/acpi/resume.d and do not forget to make it executable with
chmod +x this_script.sh

> 
#!/bin/sh

# Restarts hal daemon so that wireless device is
# found again after resume
/etc/init.d/hal restart


---

