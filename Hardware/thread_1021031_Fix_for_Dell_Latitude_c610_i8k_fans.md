---
title: "Fix for Dell Latitude c610 i8k fans"
date: 2008-12-24
forum: Hardware
---

### Post by RabidWeezle on 2008-12-24
With the latitude c610, the fans go back down automatically after you do your fanctl, so what I did was made a script that will automatically crank it back up every 10 seconds.

First of all, you need the i8k tools from the repo.

Then make a script called Full Fans or something like that with:

alt+f2, gedit, enter

copy and paste this in there

```

gksu modprobe i8k force=1
while x=0; do i8kfan 2 2; sleep 10; done
```

save it to your desktop or somewhere like that

Right click it, goto properties, goto permissions and check executable

double click it and type in your root password. You can also make this a startup program if you want later. Only need to run it once per boot.

I got sick of the fans shutting themselves off even after the cpu scaling trick, so maybe that will help some of you.

Cheers
RabidWeezle

---

