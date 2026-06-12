---
title: "Ubuntu on AMD K6-II"
date: 2013-03-29
forum: Hardware
---

### Post by wrixis on 2013-03-29
Hi.

I know that since ubuntu 10.10 we don't have non i686 support but, I'd like to install ubuntu 12.04 in a AMD k6-II which is a pentium like but without cmov instruction. Does someone know if I could use a different kernel whit ubuntu 12.04 which could run on this machine? if yes, how could i do it?. 

Thanks.

---

### Post by matt_symes on 2013-03-29
Hi> 

I'd like to install ubuntu 12.04 in a AMD k6-II which is a pentium like but without cmov instruction.

That's really not going to happen. Even besides the cmov instruction missing from the processor, Ubuntu (with Unnity, gnome shell or KDE) would run like treacle. 

Surely that box has to be over 15 years old ? :)

You want a kernel compiled for a i486 or a i586.

In the browser, navigate to

[http://distrowatch.com/search.php](http://distrowatch.com/search.php)

Select i486 or i586 in the **"architecture"** drop-down box and click **"submit query"**.

Then choose some to have a play around with.

EDIT: ...and get the lightest window manager, desktop you can find.

Could you post the specs of the machine ?

Kind regards

---

### Post by mörgæs on 2013-03-29
I had a K6 once but sent it to recycling years ago. I wouldn't recommend investing time in the project.

If you happen to get an operative system running then next question is which applications? Just imagine how slow a browser would be on such old iron...

---

### Post by wrixis on 2013-04-16
ummm maybe I can try with opensuse using suse studio.

specs, I have to see because it's not my "daily machine" but basicaly:

K6-II 450MHz
256 or 512 MB of RAM
I don't remember the Graphic Card right now. An old ATI.

Thank you very much.

---

### Post by mörgæs on 2013-04-17
May I guess? An ATI Rage? 

Though some distros are famous for bringing semi-old hardware back to life this one is not worth it, sorry.

Take a look at the used gear you can get for € 50-100.

---

