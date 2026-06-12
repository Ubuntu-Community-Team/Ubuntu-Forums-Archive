---
title: "Gpu Scaling when on battery?"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by rj686 on 2007-01-30
Is there anyway to make the gpu scale inside linux while running on battery.  I know i can select "power savings over performance" but that doesn't seem to be enough. I get a little over 3 hours on this laptop while running windows. In linux i get 1.5hours our a little more :(. My guess is the cpu scales automatically....or it seems to anyway

---

### Post by K.Mandla on 2007-01-30
There are a couple of cpu scaling tools. Check out [cpufreqd]("http://packages.ubuntu.com/edgy/admin/cpufreqd"), [powernowd]("http://packages.ubuntu.com/edgy/admin/powernowd") and [cpudyn]("http://packages.ubuntu.com/edgy/admin/cpudyn"), for starters. If you have an Athlon, there's an [athcool]("http://packages.ubuntu.com/edgy/misc/athcool") package. It will depend on your hardware. ...

---

