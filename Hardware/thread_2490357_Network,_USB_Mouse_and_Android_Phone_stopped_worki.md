---
title: "Network, USB Mouse and Android Phone stopped working"
date: 2023-08-31
forum: Hardware
---

### Post by Jonners59 on 2023-08-31
This is odd.  I noticed my Android phone wouldn't work (share files, charging was fine).  Then suddenly the network stopped working.  I have been away for a few weeks and returned a couple of days ago.  Tried using the PC yesterday and the issue was still there - so using my laptop to upload this.

I've tried updates and all sorts, but as expected nothing works as there is no network.  Googling and forums, any solution required some kind of network connectivity or dropping back to a previous kernel (which would work and I could hence update) but nothing works

Can anyone help?   I'll try and type some cmd outputs below:

uname -r ```
6.2.0-1005-oracle
```

sudo lshw -C network
```
*-network UNCLAIMED
description: Ethernet Controller
Product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor
physical ID: pci@0000:07:00:0
version: 06
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap-listnce.

resources: ioport:b000 (size=256) memory:d2104000-d2104fff memory: d2100000-d2103fff
```

I tried this, though option 2 is standard.  Still does not work.  The stage to "Activate" did not work.  The cursor would not move to the button.  So tried various cmds I found instead, but none made a difference
From here,[HTML]
https://askubuntu.com/questions/1437477/22-04-1-network-unclaimed[/HTML]

 I then tried here.
[HTML]https://itslinuxfoss.com/ubuntu-22-04-network-configuration/?utm_content=cmp-true[/HTML]

```
sudo service network-manager restart
``` Failed, said it was not found.

Not tried this as I have no network:
```
sudo apt reinstall linux-modules-extra-5.15.0-75-generic
```  Such things are useless if one doesn't have network!

```
 https://packages.ubuntu.com/jammy/kernel/linux-modules-extra-6.2.0-1005-oracle
```

Tried that, as a mod of a suggestion, but when I select the link the web  [page says error as it's not the same as my machine (my laptop I'm  using to download the file), which wouldn't be the same.

---

### Post by Jonners59 on 2023-08-31
OK, Update.  I restarted my PC and the networking started, as if by magic.  So one of the below must have worked, even though the networking restarts didn't, a full restart did.

Not closing this as the USB Mouse, USB storage and the Android Phone elements do not work still.

---

### Post by Jonners59 on 2023-09-02
So after a reboot a couple of days later the Ethernet has stopped again and again the card is listed as "UNCLAIMED".  Tried another card and it too says the same.  In nmtui the cards are not listed, just the virtual connection the system creates.  I am at a loss.  Please HELP.

---

