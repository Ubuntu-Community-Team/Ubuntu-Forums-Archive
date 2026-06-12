---
title: "Finding out Motherboard Manufacturer?"
date: 2008-12-07
forum: Hardware
---

### Post by icanfly0307 on 2008-12-07
Hi,
   I have Sony Vaio PCG FX370 laptop and I'd like to find out which motherboard it's using so that I can update my BIOS *directly* from the motherboard manufacturer's website. Any ideas on how to do this before I open up the laptop and check the motherboard physically?

Thanks for your help.):P

---

### Post by nick09 on 2008-12-07
Run this:
```
sudo lshw
```

If you want to keep a copy:
```
sudo lshw -html > your-file-name.html
```

---

### Post by icanfly0307 on 2008-12-07
Thanks. I'll try it out.

---

