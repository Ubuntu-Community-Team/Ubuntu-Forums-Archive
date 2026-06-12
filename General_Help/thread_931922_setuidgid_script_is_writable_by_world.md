---
title: "setuid/gid script is writable by world"
date: 2008-09-27
forum: General Help
---

### Post by MacDuff on 2008-09-27
Have been struggling with trying to get a USB modem to work and when I tried to "adduser"  the terminal displayed: 
"Setuid/gid script is writable by world" 

That does not sound good.  Is it a problem and how can I fix it?

---

### Post by lykwydchykyn on 2008-09-27
What are the permissions on adduser?

It's not a problem to change them back, but the real question is how they got changed in the first place.  If you can't remember doing anything that may have changed them, you might want to install chkrootkit and rkhunter and run them both.

To change permissions back on the script:

```

sudo chmod 0755 /usr/sbin/adduser
sudo chown root:root /usr/sbin/adduser

```

---

### Post by MacDuff on 2008-09-28
I have been struggling with trying to get a USB modem working on this laptop and have installed/uninstalled several applications as well as adjusted "things" as suggested by various Linux support sites. Probably some of the mucking about did it but I have no idea what.

Since this machine has not been connected to the Internet during this work, I doubt that it has been infected. 

Thanks for the advice about changing it back to what it should be.

You don't by chance know how to get a USB modem connected so I can get a dial-up connection for email and a web browser, do you?  I finally seem to have the modem working through wvdial but want to use it with GNOME-PPP.

Even when wvdial indicates that I have a connection, Firefox cannot find websites.  Most frustrating.

---

