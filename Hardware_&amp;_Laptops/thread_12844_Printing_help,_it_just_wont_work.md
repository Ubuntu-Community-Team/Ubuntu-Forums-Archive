---
title: "Printing help, it just wont work"
date: 2005-01-27
forum: Hardware &amp; Laptops
---

### Post by andy_sp1ke on 2005-01-27
Hi

 I have a fresh install of ubuntu (i have used it for a while now) and have always had printing issues. namely that it forgets my printer pretty often. Now however i cant access the gnome printer panel, it just says "the cups server could not be contacted". I cant connect to cups through the web interface even though i enabled it with:

sudo adduser cupsys shadow
Adding user cupsys to group shadow...
Done.

and i get no error messages if i do:
/etc/init.d/cupsys start
/etc/init.d/cupsys restart

and in one post there was something about the lo network not being activated at boot so i made sure to start that with:
sudo ifconfig lo 127.0.0.1

And the webbrowser can point to 127.0.0.1 but still no control over the printer. its very annoying, Being rubbish on printers and power management are the only things i dont like about ubuntu. The rest of it i like enough to make me always return to it after playing with other distros. three weeks on mandrake 10.1 and i came back again!

please help because i also have an essay to print tomorrow!!

Andy

---

### Post by Weman on 2005-12-20
Hello, I can't help but I have the same problem. It worked fine two days ago efter fresh installation of Ubuntu, but now I get the same message "CUPS cannot be contacted" when trying to access. 

When I try: /etc/init.d/cupsys restart
I get:
" * Restarting Common Unix Printing System: cupsd                         [ ok ]"

So it is there but won't work. I have tried everything I have found to read about it but no luck. Hoping someone will help us soon.
It's frustrating.
/// weman

---

### Post by Weman on 2005-12-20
Hi again, have you seen this?

[http://lists.debian.org/debian-printing/2005/09/msg00067.html](http://lists.debian.org/debian-printing/2005/09/msg00067.html)

Could be the bug.

// weman

---

