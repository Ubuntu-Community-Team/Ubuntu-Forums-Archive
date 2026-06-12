---
title: "Why did Samba magically quit working?"
date: 2008-10-01
forum: General Help
---

### Post by Calmor on 2008-10-01
My girlfriend's machine, running Ubuntu Gutsy, has been printing from a networked printer on a Windows XP "server" for months.  This past weekend, I updated the software on my router to a dd-wrt build.  She was able to print just fine after the install.  Otherwise, nothing else has changed, and neither machine was updated.

The printer is set up as a samba printer on smb://<workgroup>/<server>/<sharename>

Yesterday, she attempted to print, and the print job list just showed the job as "processing".  The server print job status did not register anything.  I was able to print a test page from the server with no problems.

I deleted the printer and tried to reinstall it (using the GUI).  Samba can browse the network and find the printer just fine.  When I attempt to verify it, I receive an "Inaccessible" error message.  The printer is set up shared with public and doesn't need a login, but I tried my Windows login anyway, with no luck.

Using smb://<IP>/<sharename> works, however.

Any ideas?

---

### Post by Peter09 on 2008-10-01
can you ping the windows machine by hostname from a terminal?

---

### Post by airtonix on 2008-10-01
If the ip works but the hostname does not i suggest looking at your router with a katana.

Specifically investigate its dns or hostname lookup ability.

---

### Post by Calmor on 2008-10-01
> **Peter09 said:**
> can you ping the windows machine by hostname from a terminal?

Yes - the ping works with no problem. 

I'm suspecting it's a Samba issue because when trying to browse the network in Nautilus, I can see the server but not the shared folders.

---

### Post by Calmor on 2008-10-02
> **airtonix said:**
> If the ip works but the hostname does not i suggest looking at your router with a katana.

Specifically investigate its dns or hostname lookup ability.

When I first read this, I thought you wanted me to chop up my router into little bits! (and sometimes I do want to...)

What's this katana tool?  I haven't been able to find anything on it.

---

### Post by der_joachim on 2008-10-03
> **Calmor said:**
> What's this katana tool?  I haven't been able to find anything on it.

It's a hacking tool. :) Ok that one was redundant.

On a more serious note: have the settings on your GF's PC been changed by any chance? Or is there perhaps an authentication issue?

---

### Post by Calmor on 2008-10-04
That was what I found odd - nothing on her machine changed, not even any updates between when it worked and when it stopped.  She doesn't really get under the hood - that's my job.

It could be an authentication issue, I'm not sure.  It still works with the IP set instead of the hostname/servername, so could authentication problems still allow it to print from the IP address?

---

### Post by taladan on 2008-10-04
it sounds like your router isn't allowing netbios name resolution.  It could be something on the windows machine's end, but I'd check the router first and make sure it has a dns entry for the server - hopefully you have your server statically assigned - if so, you should be able to operate off the dns name of the machine.

Tal

---

### Post by Calmor on 2008-10-07
> **taladan said:**
> it sounds like your router isn't allowing netbios name resolution.  It could be something on the windows machine's end, but I'd check the router first and make sure it has a dns entry for the server - hopefully you have your server statically assigned - if so, you should be able to operate off the dns name of the machine.

Tal

Tal, 

There's an interesting idea I'll have to try when I get home.

dd-wrt doesn't seem to care much for a machine assigning its own IP - it prefers you leave the machine at DHCP and assign an IP based on MAC address via the router (one of the reasons I changed to dd-wrt in the first place).  If the router doesn't see the host name for the server because it's set for a static IP itself, perhaps it won't allow it to print correctly.  

I'm curious why it would allow a ping to that host name but not print or sharing functionality?  I'm pretty new to the details of networking... 

In any event, I'll set the server to DHCP and set a static IP via the router, see if that clears anything up.

Thanks,

Jim

---

### Post by taladan on 2008-10-08
Nevermind...Too early in the morning, thinking ddclient, not dd-wrt.

---

