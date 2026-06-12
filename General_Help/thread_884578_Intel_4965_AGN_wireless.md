---
title: "Intel 4965 AGN wireless"
date: 2008-08-09
forum: General Help
---

### Post by mordecai83 on 2008-08-09
Hello all,

I've got a problem, wireless doesn't work for me. Ive read several tutorials and its getting me nowhere. This is what ive done so far:

Ive got the intel 4965 AGN wireless module, and when i google it or search through this forum most pages come up with: works out of the box. But it doesn't for me tho. So i tried to use ndiswrapper, which was a problem cause the drivers i got with this computer are for vista. I finally got the right drivers for xp from the intel site and installed them with ndiswrapper and this is what i get:

```
netw5x32 : driver installed
	device (8086:4229) present (alternate driver: iwl4965)
```

Now im a real noob, but i think that means the driver works and it finds the device(cuz the device id matches)

But i still get no wireless, the network configuration manager doesn't even show a wireless option.

This is what i get when i do iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

pan1      no wireless extensions.

```

That is what i have so far. could it be possible ndiswrapper loads the wrong driver? the alternative one? and how do i disable that? Or do i need to do something else to load the right driver?
Any help would be apreciated. oh btw im using hardy

---

