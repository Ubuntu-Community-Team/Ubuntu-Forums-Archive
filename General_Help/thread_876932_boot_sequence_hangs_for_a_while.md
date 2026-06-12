---
title: "boot sequence hangs for a while"
date: 2008-08-01
forum: General Help
---

### Post by Choad on 2008-08-01
kay... here's what i have got so far. fixing up an hp g7000 with ubuntu gutsy for a friend. it hangs on boot for 10-15 seconds. deduced it is to do with acpi... it's this line in particular it hangs on

[36.078981] ahci 000:00:1f.2: forcing ports_impl to 0x7  

not sure what it means... anyhoo booted with the option acpi=off and WOW... i have never seen that option break a system so completely. pretty much every hardware driver it tried to load threw an error, it took about 4 minutes to finish "loading" the hardware drivers, then it spazzed out for a while and eventually dumped me at the low graphics screen.... but with no keyboard and mouse! huzzah!

so yeah... i am stumped. any ideas?

---

### Post by Choad on 2008-08-01
bump

this is quite ugrent! i wouldn't normally bump so soon

---

