---
title: "Dektop and server versions"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by tbobker on 2009-02-24
So i like the GUI interface of the desktop version to install applications and configure stuff.

But when everything is configured and installed to run as a server can i uninstall all applications that are installed on the desktop version to trim it down to a server install so i can manage it remotely?

Things like the interface, software like open office that comes with it..etc...

---

### Post by cariboo on 2009-02-24
Yes you can remove the gui programs. If you use the server install cd, it doesn't install all the extra gui applications, 

I find it is easier disabling gdm, so the desktop doesn't start automatically, but you've still got it if you need it.

```
sudo update-rc.d -f gdm remove
```

will stop gdm starting on boot. If you need the gui type:

```
startx
```

at the prompt.

Jim

---

### Post by tbobker on 2009-02-24
Jim,
Thanks for that. So just to reiterate.

If i install the desktop version and install all the server applications that i want and set up my server once this is done i can then just disable the desktop (this includes all the applications that come with the desktop version).?

Thanks.

---

