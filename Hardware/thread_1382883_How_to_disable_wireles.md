---
title: "How to disable wireles"
date: 2010-01-16
forum: Hardware
---

### Post by alvin4 on 2010-01-16
HI, when I right click on the network connection thingy in the toolbar I deselect "Enable Wireless" but whenever I reboot the laptop it selects itself again, how do I disable it for good?

Thanks! :)

---

### Post by gabo.cr on 2010-01-16
Try this:

```
sudo gedit /etc/network/interfaces
```

Add the following...

```
#
```

at the beginning of the wireless info.
Edit: Then save the file and restart the computer.

---

### Post by alvin4 on 2010-01-16
> **gabo.cr said:**
> Try this:

```
sudo gedit /etc/network/interfaces
```Add the following...

```
#
```at the beginning of the wireless info.
Edit: Then save the file and restart the computer.Thanks, but I figured out how to disable it via BIOS. :)

---

### Post by Jose Catre-Vandis on 2010-01-16
> **gabo.cr said:**
> Try this:

```
sudo gedit /etc/network/interfaces
```

Add the following...

```
#
```

at the beginning of the wireless info.
Edit: Then save the file and restart the computer.

This is what I would have done, in the old days, but am trying to be good now and let network manager do the work. However, my interfaces file is empty save the auto lo entry. So the question is still how to disable wireless, or at the very least, stop connecting by both wired and wireless when wired up. I can do this with WICD, and may go that way again....or even head back to an interfaces file :)

---

### Post by gabo.cr on 2010-01-17
> This is what I would have done, in the old days, but am trying to be good now and let network manager do the work. However, my interfaces file is empty save the auto lo entry. So the question is still how to disable wireless, or at the very least, stop connecting by both wired and wireless when wired up. I can do this with WICD, and may go that way again....or even head back to an interfaces fil

I think we should add that option on the Network Manager.
Installing WICD is one way do it, like you said, but still, we should have it in the Network Manager.

---

