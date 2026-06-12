---
title: "firewall blocking ports?"
date: 2005-12-03
forum: General Help
---

### Post by lysis on 2005-12-03
so i installed azureus, and changed the port on azureus from 6881 to 16881. it has NEVER connected to torrents EVER. does ubuntu block ports automatically with a software firewall? my router is forwarding those ports; in fact i'm using DMZ on my ip.

---

### Post by bionnaki on 2005-12-03
did you install firestarter?

---

### Post by Joeak on 2005-12-03
Ubuntu (5.1) does not block ports by default.  You'd have to configure iptables rules by hand or use a utility like firestarter.  I haven't tried azureus on Ubuntu yet.  On Windows, there was one version where I let it get too far behind on updates and it refused to connect even to download updates so that it WOULD work.  Sorry I'm not more help.

---

### Post by lysis on 2005-12-03
i've tried several bit torrent programs and NONe of them will connect. azureus finally had a green face (connected) but didn't download anything from the 120 seeders and 2000 peers (over a 6 hour span)

---

### Post by sapo on 2005-12-03
[QUOTE=lysis]so i installed azureus, and changed the port on azureus from 6881 to 16881. it has NEVER connected to torrents EVER. does ubuntu block ports automatically with a software firewall? my router is forwarding those ports; in fact i'm using DMZ on my ip.[/QUOTE]
Yes, ubuntu blocks by default, to solve it, open up a terminal and type:

```
sudo apt-get install firestarter
```

The firestarter menu entry should appear on the internet menu tab, open it.

In the policy tab, right click on the alow service rule, and fill the name and port field with 6881-6889, click add and then apply rule.

Now your azureus should connect :)

---

### Post by lysis on 2005-12-03
[QUOTE=sapo]Yes, ubuntu blocks by default, to solve it, open up a terminal and type:

```
sudo apt-get install firestarter
```

The firestarter menu entry should appear on the internet menu tab, open it.

In the policy tab, right click on the alow service rule, and fill the name and port field with 6881-6889, click add and then apply rule.

Now your azureus should connect :)[/QUOTE]
sapo you're a damned genius!

---

### Post by keiffee30 on 2007-08-07
Just to pop in another problem if i may .....

I have had the same problem with azureus too. I found this post and downloaded Firestarter. i have added a profile and every time i keep getting Azureus saying that it can not use t any ports from 6881 - 6889, 

i am running edubuntu im not sure if this makes any diffrents. 

Any comments would be nice

Many thanks

---

