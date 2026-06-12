---
title: "Do You Need Network Manager?"
date: 2008-10-18
forum: General Help
---

### Post by Kinetic Being on 2008-10-18
Is it necessary to have network manager running all the time? Or even just in the system tray? 

If it isn't, how do I remove network manager from my system tray?

Thanks,

Kinetic Being.

---

### Post by sci-fi guy on 2008-10-18
> **Kinetic Being said:**
> Is it necessary to have network manager running all the time? Or even just in the system tray? 

If it isn't, how do I remove network manager from my system tray?

Thanks,

Kinetic Being.

No, it's not necessary. You can edit your /etc/network/interfaces file instead (I don't recommend this if you use wifi, but it'll work)

To turn off NetworkManager, you can go into System>>Preferences>>Sessions and turn it off there.
You may also want to use rcconf to turn it off system-wide. (I think you need to install it first)

---

### Post by Kinetic Being on 2008-10-18
Thanks. I went to system>prefrences>sessions and turned it off. Internet still works... :) I'm hardwired to my router...

I always wondered why it even started, it didn't seem to do anything useful.

---

### Post by sci-fi guy on 2008-10-18
> **Kinetic Being said:**
> Thanks. I went to system>prefrences>sessions and turned it off. Internet still works... :) I'm hardwired to my router...

I always wondered why it even started, it didn't seem to do anything useful.

Don't thank me until it works after a reboot.

---

