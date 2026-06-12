---
title: "How to set minimum cpu speed at boot"
date: 2009-05-04
forum: Hardware
---

### Post by ahbart on 2009-05-04
Hello, 
I would like to set the minimum cpu speed at boot time. The cpu governor starts in ondemand mode. But In my opinion the lowest speed gives me a much to slow system respond. I found out that I can set the minimum speed with:
```
sudo sh -c "echo 1275000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq" & sudo sh -c "echo 1275000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq"
```
But how and where can I configure this at boot time? I do not want to double click and enter my password everytime.

---

### Post by kpkeerthi on 2009-05-04
ondemand automatically scales, well, on demand.

[https://help.ubuntu.com/community/RcLocalHowto]("https://help.ubuntu.com/community/RcLocalHowto")

---

### Post by ahbart on 2009-05-04
Are you sure? :D ;)
That is not exactly the answer I was hoping for. It doesn't scale fast enough. As I said before, I want to automatically higher the minimum cpu speed.

---

### Post by ahbart on 2009-05-04
Ah Oke I just followed the link. Yes I think that is what I was looking for. I'll try that. Thanks.

---

### Post by binbash on 2009-05-04
write it to /etc/rc.local before exit : 

echo 1275000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq

---

### Post by ahbart on 2009-05-04
Thanks, that is a more elegant solution. I was not aware of the existence of rc.local on Ubuntu now. Is this new?

I just created the /etc/init.d/local file and did a "sudo update-rc.d local defaults 80"
What is the command to remove this rc.d entry's?

Edit: ```
sudo update-rc.d -f local remove
``` (source=[google](http://wiki.linuxquestions.org/wiki/Update-rc.d))

---

