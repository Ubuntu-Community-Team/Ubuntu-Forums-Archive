---
title: "Lifebook A544 Ubuntu 14.04 CPU 1 high usage"
date: 2015-08-30
forum: Hardware
---

### Post by jmmrly on 2015-08-30
Hi, I'm running a fairly clean install of ubuntu 14.04 64bit on my A544 laptop. I noticed however, that the fan was noisy and the battery was running down very quickly compared to windows which I run as a dual-boot. I executed top in terminal and got the following;  ([http://oi61.tinypic.com/w87q6s.jpg](http://oi61.tinypic.com/w87q6s.jpg))   that the kworker was using almost 80% of my first cpu core constantly. I did some research and I did sudo perf record -g -a sleep 10 then sudo perf report which got me the following: ([http://oi57.tinypic.com/whn1ao.jpg](http://oi57.tinypic.com/whn1ao.jpg)). I have tried this post - [http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high) in which I found out that my gpe13 was at a very very high value -( [http://oi58.tinypic.com/1z1ae6v.jpg](http://oi58.tinypic.com/1z1ae6v.jpg)) and I typed in the cp /sys etc and then crontab -e and added the line in, restarted and still no change.

Any ideas on how to fix this issue?

Thanks.

---

### Post by Yellow Pasque on 2015-08-31
[http://askubuntu.com/a/421916](http://askubuntu.com/a/421916)

---

