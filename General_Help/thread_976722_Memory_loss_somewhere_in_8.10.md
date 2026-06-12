---
title: "Memory loss somewhere in 8.10"
date: 2008-11-09
forum: General Help
---

### Post by hipogrito on 2008-11-09
Hello,
Ubuntu 8.10 in a Compaq Laptop.


I have been using Ubuntu for the past 2 years. Nice work fellas!

This last week I am experiencing one problem. Maybe related with 8.10, maybe related to any upgrade of an application... probably this last option, but I am not sure.

So, I was wondering if someone is experience something like this as well.

If I open my system monitor and open the resources tab I can see the memory display. Well, my memory is going up all the time... little by little, step by step, but going steady up, until I have to reboot my machine as it becomes too slow... few hours until this happens.

I had not had this problem before.

So, I start to close applications, even to kill processes, but still the memory loss is somewhere that I cannot find.


The smoking gun?

Well, the applications I use are:
- Firefox
- VPN to connect to my work network
- Eclipse

So, my first choice would be... ok, Eclipse is killing my machine. The funny thing is that I turned on the machine, I turned on Eclipse, and the memory seems to be flat. No rising. I was checking for few minutes, and keep fine.

Now, I was writing in a forum similar to this one as I had also Firefox, and after 20 minutes I checked the memory and it was starting to go up. I closed Eclipse, and keeps going up. If I close Firefox, I have tested before, it will still keep going up.

Any idea?

Thanks!

Regards,
Fran

---

### Post by jpeddicord on 2008-11-09
When you close Firefox, check the monitor. Is a 'firefox' process still running at that point?

Also, the kernel will also cache memory of shared libraries or other frequently used objects. Even though the reported memory might be lower, this cached memory will be freed up when you want to use an application.

---

### Post by todak on 2008-11-09
In the Firefox address bar type ```
about:config
```Then in the "Filter" bar type ```
browser.cache.memory.enable
``` See if its value is set to "false". If not, double-click on the entry you see and it will toggle from "true" to "false". This stopped my memory leakage instantly and I do not see any performance degradation in Firefox.

---

### Post by hipogrito on 2008-11-09
Hello,

Thank you for your tips.

After 4 hours I can say that Firefox seems to be the guilty one. The suggested fix has not helped, but I have been running the machine without Firefox for a decent time without memory leaks, which is good. I was pointing fingers towards Eclipse and, it seems, that this time, is innocent :-)

Regards,
Fran

---

