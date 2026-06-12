---
title: "wireless died:("
date: 2008-11-04
forum: General Help
---

### Post by theevilhamster on 2008-11-04
OK, So i put my cird into monitor mode with
```

ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

```

and it worked fine, then i put it back into managed mode with 

```

ifconfig wlan0 down
iwconfig wlan0 mode managed
ifconfig wlan0 up

```

but the network-manager wont connect to my network. it only displays one of my areas networks and if i attempt to connect to my own network i get one green dot and the get re-prompted with my password.

I know this is the right password as i use it when i boot OSX (im on it now so the card is also fine) i have changed no network settings. it will connect to no other networks.

am i doing something wrong?

can i connect to the network via terminal?

p.s.

if it helps i use wpa2 (psk) for encryption.

thanks!

Rob

---

### Post by theevilhamster on 2008-11-04
strange... logged in as root to do some maintenance, and now all is fine.

---

