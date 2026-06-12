---
title: "failed to suspend"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by tetrafuran on 2008-02-15
When I tell it to suspend, it just turns of the screen. When I return it asks for my password and tells me "Your computer failed to suspend".

This has forced me to read a lot about this. During my adventures I have :
- changed settings in the power menu
- tried hacking the fles at /etc/acpi/events
- ran some scripts at /etc/acpi
- tried s2disk

Previously I had Wolvix and DSL on this laptop and they were able to handle the lid event very well. When I closed the lid, the computer said beeb-beep and went silent. I could leave it like that for ages and as soon as I reopened the lid I was back where I left it in a matter of seconds.

At the moment I'm using debian etch and the only thing I can do is to hibernate. This just seems to save all stuff to the HD and shutdown. After a time consuming reboot it returns where I left it. 

However now I'm trying to suspend as I automatically did in Wolvix and DSL. Instead suspending in debian seems to mean turning off the screen and leaving HD on.

This laptop has a battery lifetime of about 30s while the screen is on. In ths semi suspend mode it is 5 minutes. In a full DSL suspend it is propably days, weeks or even months. Haven't tried yet. I would like to have full suspendability in Debian too.

---

### Post by tetrafuran on 2008-02-27
I noticed another strange thing. When I'm in bios or in system reboot, the lid does exactly what it is supposed to do. When the system finally starts it looses this ability.

---

