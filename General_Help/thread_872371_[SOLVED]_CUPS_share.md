---
title: "[SOLVED] CUPS share"
date: 2008-07-27
forum: General Help
---

### Post by Potatoj316 on 2008-07-27
I am trying to set up a shared printer using ipp (i think thats the correct thing to use).  
I have a computer running Ubuntu-Server 8.04.1 that has the printer connected to it.  This computer can print just fine to the printer. Im going to call this the server.
I have another computer running Ubuntu 8.04 that I want to be able to print from.  Im going to call this the local computer.
I have been using the CUPS web interface with lynx over an ssh connection to the server in an attempt to set up the share.  I am also using the CUPS web interface for the local setup.  (viewed in firefox) I eventually got to a point where my local computer added the remote printer using the correct drivers.  (ie I saw it in the CUPS printers tab)  When I tried to print the test page it acted like it did (sent the job #100) and when it redirects to the page that shows the printing status it says sending 75% (or something like that) but then eventually it says Forbidden.  
Does anyone know what the problem is or how to fix it?

---

### Post by Vivaldi Gloria on 2008-07-28
[COLOR="Blue"]Server = the computer with the printer
Client = the computer without printer [/COLOR]

Have you edited the adresses that the server listens to? Press ALT+F2 and start 

```
gksudo gedit /etc/cups/cupsd.conf
```

and now add the client's adress there:

<Location />
...
...
  Allow From <clients_ip_number>
</Location>

Here you can also add "Allow all". Now restart cups so that changes take effect:

```
/etc/init.d/cups restart
```

---

### Post by Potatoj316 on 2008-07-28
I have "Allow all" in that space.  I have been trying to connect with ipp, is this correct?  If I go into System->Administration->Printers and try to add a new printer using ipp it will show me the list of printers for localhost/192.168.1.2(client IP) but it tells me that it cant load printers list (or something to that effect) when I try to look at 192.168.1.3(server IP)

I had been using ssh to view the CUPS config page in lynx (text browser) but now for some reason I can no longer view the CUPS page in lynx.  I can still ssh to the server but it tells me that it cant load remote page (im not exactly sure what it said, im not on that computer at the moment)

On the client I set it to show shared printers and the server set to share connected printers.
All firewalls have been off for these attempts.

---

### Post by Potatoj316 on 2008-07-29
well it works now, I dont really know what I did to fix it.  I just used the default config file and it magically worked.  I tried setting up shared printing right after installing ubuntu-server so it should have already been the default config file.  The printer automatically showed up in my client computer's printers window, so Im happy, thank you all for helping

---

