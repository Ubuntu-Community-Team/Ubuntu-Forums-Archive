---
title: "gsynaptics shmconfig.fdi"
date: 2009-05-21
forum: Hardware
---

### Post by Memorice on 2009-05-21
I tried to enable SHMConfig by creating a shmconfig.fdi file in /etc/hal/fdi/policy as recommended everywhere on the internet. Unfortunately after reboot I still cannot use gsynaptics, because SHMConfig is still disabled.

This is what I put in the shmconfig.fdi:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>

I use Kubuntuu 9.04 on a MSI GX620 laptop.

---

### Post by Memorice on 2009-05-21
I 'solved' this problem by removing shmconfig.fdi, performing a reboot, creating the same shmconfig.fdi again followed by a reboot. I am not sure why it works, but it works :)

---

