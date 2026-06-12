---
title: "Shutdown workaround"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by spotslayer on 2006-10-30
I have found much about the problem were 6.10 hangs when shutting down. I have not seen any solution yet. I have noticed that if you select logout and then end current session when you get back to the login screen a proper shutdown or reboot can be done from there. I know it is kind of a pain in the tooch but until there is a better solution I will use this workaround. 

I hope a permanant solution is created soon.

David

---

### Post by DaveBorealis on 2006-10-30
Hello,

Have you tried opening a gnome-terminal or xterm and doing either below?
```
sudo /sbin/shutdown -h
or
sudo /sbin/shutdown -r
```

I'm curious if it's possible at all for you to shutdown or reboot from within a user's login session.

I'd try it myself, except I'm running Dapper (and am in no rush to update just yet!)

Best regards,
Dave

---

### Post by spotslayer on 2006-10-31
Actually I am using Kubuntu and forgot to mention it.

I can shutdown from a terminal prompt. I can also shutdown by exiting to the login manager and shutting down from there. Only hangs up when I try to right click, logout and from there choose to logout or shutdown. Then it hangs..

David

---

### Post by az on 2006-10-31
> **spotslayer said:**
> 
I can shutdown from a terminal prompt. I can also shutdown by exiting to the login manager and shutting down from there. Only hangs up when I try to right click, logout and from there choose to logout or shutdown. Then it hangs..

David

Please file a bug report.  I am not sure, but perhaps the package you should assign it to is kdebase.

---

### Post by David Corrales on 2006-10-31
> **spotslayer said:**
> I have found much about the problem were 6.10 hangs when shutting down. I have not seen any solution yet. I have noticed that if you select logout and then end current session when you get back to the login screen a proper shutdown or reboot can be done from there. I know it is kind of a pain in the tooch but until there is a better solution I will use this workaround. 

I hope a permanant solution is created soon.

David

I had to add the **acpi=force** cheat code to my kernel boot line, in order to get shutdown working on another machine.

---

