---
title: "Toshiba fan noise"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by bgoody on 2006-09-24
Does anyone know why this kernel 
Linux 2.6.15-26-686
and no other, earlier or later, runs the fans quietly.  They come on when there is activity and then gradually fade away.  Much much quieter than the other kernels. It was the first one to operate the fans correctly and the newer kernel reverted to one fan on all of the time at about 1/3 speed.

Thanks in advance.

---

### Post by Kateikyoushi on 2006-09-25
You could try [this script]("http://www.thinkwiki.org/wiki/ACPI_fan_control_script") to set it up manually.

---

### Post by bgoody on 2006-09-25
Hi: Thanks for the response.  It seems that those scripts require access to the sensors but nobody seems to know how to do that for Toshiba machines with Phoenix bios'.

It's weird because for some reason or other when I came back from vacation the fans ran as they do in Windows (as required) and I though it was something that was changed in one of the kernels.

Now I'm not sure as I rebooted and they are running all the time.

Brian

---

### Post by bgoody on 2006-09-30
Hi.  Found the solution.  It turns out that Ubuntu 686 kernel is multi processor by default and neglects to comunicate this information to a single processor machine so the machine is idling too high.

Go to a root terminal:

 cd /sys/module/processor/parameters

then 

echo 1 > sys/module/processor/parameters/max_cstate

There's a way to do this automatically.  Do a search on the main Ubuntu forum for "max_cstate"

Great stuff. No earplugs!

---

