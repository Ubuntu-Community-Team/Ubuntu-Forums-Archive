---
title: "default parameters for iwlagn module,"
date: 2012-04-15
forum: Hardware
---

### Post by eigenman on 2012-04-15
Hi,

I have a Lenovo X220 laptop, with an intel 6205 Centrino wireless card, running Ubuntu 12.04. For some odd reason, when 11n is enabled this wireless becomes really flakey (this is a known bug, I believe) and the workaround is to force 11g wireless. 

I've created the file /etc/modprobe.d/iwlagn.conf with the content
"options iwlagn 11n_disable=1", and now when I modprobe iwlagn, the wireless is pretty functional. However, when I restart my computer, 11n is enabled by default, and I need to remove iwlagn and then modprobe it again. Is there somewhere else I need to put these default options so that when the computer is started, 11n is disabled?

Cheers,
eigenman

---

### Post by blazerw on 2012-06-26
Here's a great Ask Ubuntu answer that tells you all you need to know: [http://askubuntu.com/questions/51226/how-to-add-kernel-module-parameters](http://askubuntu.com/questions/51226/how-to-add-kernel-module-parameters)

---

