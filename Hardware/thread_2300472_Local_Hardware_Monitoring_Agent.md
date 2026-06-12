---
title: "Local Hardware Monitoring Agent"
date: 2015-10-26
forum: Hardware
---

### Post by Ivac_Nikolov on 2015-10-26
Hello everybody

I need some help about Local Hardware Monitoring Agent. I search all around but I can't find the right solution for me. I will appreciate to point me at the right direction. 
My scenario is:
Local Xubuntu desktop -> Local Monitoring Agent that works independently (Peace of software for Hardware monitoring (RAM, HDD, CPU, Current OS State, What is the current software state - Do I need update or not - this one is not mandatory) -> All these information put in a .XML format -> Send to IP address or Send with HTTP post on a server.

10x

---

### Post by tgalati4 on 2015-10-26
Welcome to the forums.  You might consider Landscape:  [http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use](http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use)

---

### Post by Ivac_Nikolov on 2015-10-26
> **tgalati4 said:**
> Welcome to the forums.  You might consider Landscape:  [http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use](http://askubuntu.com/questions/549809/how-do-i-install-landscape-for-personal-use)

Thanks. This looks great but not working for me. I have 200 host in my  network and I need every host to send http post (curl) for example, on  custom made ERP system that will generate graphics. For that reason I  need to generate .XML format from every local machine with some software  like Monitorix or M/Monit or Munin.

---

### Post by tgalati4 on 2015-10-27
There are [several]("http://www.infoworld.com/article/2683857/network-monitoring/article.html") to choose from.  They all have a learning curve.  They all require extensive setup.  

On each host, you will run a small script through a cronjob that dumps the data to an XML file and then pushes it to a collecting server.  Have you written a monitoring script yet?  It is not difficult.  

Why do you need RAM, CPU?  They will fluctuate wildly each second, so capturing load every hour doesn't make sense.  HDD SMART status is important, that can be done once per day.  Update status is easy to get, but only needs to be done on one machine.  When that machine needs updates, then all the rest will need them.  But for production machines,  I would only apply updates once every 6 months, and only on a small group of machines that run for a week to make sure there are no regressions.  If they pass, then roll out the updates to the rest.

---

### Post by Shane_Carmichael on 2016-01-27
Nagios will be a reliable monitor for 200 hosts. It will provide quite a bit of flexibility and efficiently check your RAM, CPU, etc. You can also set up notifications through SMS or email, which is convenient. On risk here is that with 200 hosts, you may be monitoring quite a lot of data. I would look into a solution like [BigPanda]("https://bigpanda.io/integrations/nagios-the-alternative-to-a-flood-of-alerts"), which plugs into Nagios, and will correlate your related alert notifications into single incidents. This will save time and reduce the size of your inbox.

---

