---
title: "Networking disabled after suspend"
date: 2008-11-01
forum: Hardware
---

### Post by Cl0ud9 on 2008-11-01
I upgraded to 8.10 from 8.04 and now networking is always disabled after a suspend. I can easily enable it manually after every suspend, but I was wondering how to make Ubuntu do this for me.

---

### Post by berthiggins on 2008-11-01
I have the same issue on 2 machines a desktop and a laptop

---

### Post by jdeslip on 2008-11-03
I also have this problem - except that networking is only disabled about half of the time.  Is there a bug report for this?

---

### Post by xur17 on 2008-11-05
I am getting this same issue.  It only occurs for me some of the time.

I found another thread that appears to be discussing the same issue, and a workaround:
[http://ubuntuforums.org/showthread.php?p=6077775](http://ubuntuforums.org/showthread.php?p=6077775)

---

### Post by kthxbai2u on 2010-05-31
How do you enable it?

I have tried resetting, didnt work.

I also tried:

ifconfig wlan0 down
ifconfig wlan0 up

service networking stop
service networking start

I also tried using the hardware switch to turn it off and on, and I still cant get networking enabled...

What ticks me off is it worked perfectly fine before...

Anyone know how to re-enable networking?

---

