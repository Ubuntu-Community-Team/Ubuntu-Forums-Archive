---
title: "How can i connect to the internet on startup?"
date: 2008-07-23
forum: General Help
---

### Post by killerwhale65 on 2008-07-23
Hello,

I would like to know how i can have my network connection enabled when i start up my PC. Currently, the "wired netword connection" icon in ths systrau has a red cross when i start up. Clicking on it shows me the options 'wired network' and 'manual configuration'. Clicking on 'wired network' starts my internet connection, but of course this is not handy. 

Thanks!

Matt

---

### Post by Flyingjester on 2008-07-23
I am afraid i have not encountered this problem, on both my wired connection and wireless connection they sync automatically. The only thing i can suggest is filing a bug report through launchpad.

---

### Post by knutschr on 2008-07-23
I haven't this problem either.
It might be because I in Control senter --> Session has asked Gnome to remember?

---

### Post by KeyserSoze93 on 2008-07-23
you could try putting a line in /etc/rc.local (before the "exit 0") containing "/sbin/ifup eth0"

---

### Post by killerwhale65 on 2008-07-26
> **knutschr said:**
> I haven't this problem either.
It might be because I in Control senter --> Session has asked Gnome to remember?

What session do you make for it then?

thanks!

---

### Post by stevoo on 2008-07-26
r you using the build in manager for Ubuntu.

May i reccomend that you try out WICD.

---

### Post by killerwhale65 on 2008-07-26
> **KeyserSoze93 said:**
> you could try putting a line in /etc/rc.local (before the "exit 0") containing "/sbin/ifup eth0"

That is without the quotation marks i suppose?

---

### Post by knutschr on 2008-07-26
> **killerwhale65 said:**
> What session do you make for it then?

thanks!

I don't understand.
In the last tab, mark for remember.

---

### Post by killerwhale65 on 2008-07-26
> **knutschr said:**
> I don't understand.
In the last tab, mark for remember.

What screen are you talking about?

---

### Post by knutschr on 2008-07-26
System --> Control center --> Session

---

### Post by jerome1232 on 2008-07-26
I get that problem when the wired network is set for roaming, I set it to manual and tell it DHCP and it will be connected on boot.

---

### Post by killerwhale65 on 2008-07-27
> **jerome1232 said:**
> I get that problem when the wired network is set for roaming, I set it to manual and tell it DHCP and it will be connected on boot.

That worked! You are wonderfull! Thanks!!

---

