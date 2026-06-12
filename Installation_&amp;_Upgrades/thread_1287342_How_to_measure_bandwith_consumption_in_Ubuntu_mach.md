---
title: "How to measure bandwith consumption in Ubuntu machine"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by vksingh on 2009-10-10
Hi,

I have configured a Ubuntu repository mirror which is downloading the repositories.

I want to see what is by bandwith consumption with increase of threads in apt-mirror.

kindly suggest some tool to do this.

Please help.....:(
Thanks,

Vivek

---

### Post by sloggerkhan on 2009-10-10
vnstat can keep track of your overall bandwidth usage and is really easy to use.

---

### Post by vksingh on 2009-10-10
Hi,

 i installed vnstat. I tried to start it.

root@vivek-desktop:/home/vivek# vnstat -u -i eth0
root@vivek-desktop:/home/vivek# cd /var/lib/vnstat/eth0 
bash: cd: /var/lib/vnstat/eth0: Not a directory
root@vivek-desktop:/home/vivek# vim  /var/lib/vnstat/eth0 


How can i see the data monitored by the vnstat.

It will be great if u tell me how to use it.

Thanks,

Vivek

---

### Post by sloggerkhan on 2009-10-10
look at its man page. When you run it the first time, it needs to start a log.
```

 vnstat  -u  -i interface forces a database update for interface or cre&#8208;
       ates the database if it doesn&#8217;t exist. This is usually the  first  com&#8208;
       mand used after a fresh install.

```
The issue is that the first time you run it, it needs to be run as root so it can create the log files. So it should be fine if you sudo it once.

See: [http://humdi.net/vnstat/](http://humdi.net/vnstat/) for more info. Likewise, if you wanted you could look into a php web front end that makes it show up in a web browser very pretty.

---

### Post by lpwaqas on 2011-02-04
Same thing happened to me while installing vnstat on the machine for the first time, in my case it was wlan0 instead of eth0; I dissconnected and then connected back again ran the command again with
sudo vnstat -u -i wlan0 and it worked out just fine and created a new database. Then I restarted the vnstat services using etc/init.d/vnstat restart

and it started working :D

waqas@Waqas-XPS:~$ vnstat -d

 wlan0  /  daily

         day         rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
      02/04/11    245.27 MiB |   18.98 MiB |  264.24 MiB |   67.40 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated       659 MiB |      48 MiB |     707 MiB |

---

