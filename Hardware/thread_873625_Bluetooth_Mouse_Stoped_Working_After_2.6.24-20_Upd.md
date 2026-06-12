---
title: "Bluetooth Mouse Stoped Working After 2.6.24-20 Update"
date: 2008-07-29
forum: Hardware
---

### Post by sultanoswing on 2008-07-29
As the topic says, my Dell Bluetooth Travel Mouse stopped working today after rebooting having updated to the new 2.6.24-20 kernel released today. Was running fine under 24-19. This is Dell XPS 1330, by the way.

The mouse still appears under the bluetooth > preferences > services > input services. And when I select 'Add' it says the mouse is connected, but it's not working / responding on screen i.e. no cursor movement or menu pop-up!

Thoughts?

---

### Post by sultanoswing on 2008-08-07
[SOLVED] well at least partially - just seems to not register the mouse on bootup sometimes and requires a manual restart of the blue tooth service. No biggie.

```

/etc/inid.d/bluetooth restart

```

---

