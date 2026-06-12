---
title: "Monitor temperature of remote computer"
date: 2008-07-10
forum: General Help
---

### Post by Woody1987 on 2008-07-10
I have Ubuntu 8.04 on my desktop and laptop, and Ubuntu Server 8.04 on my server. I would like to be able to monitor the servers CPU and hard drive temps on both my desktop and laptop. I presume lm-sensors is needed on the server. I assume the solution would be to somehow send the data that lm-sensors gets over the network. Is the correct method? If so how? If not what do i do?

---

### Post by carcdrcdr on 2008-07-10
This all depends on how far you want to go with your monitoring solution.

If you want to go all out (like me) use Nagios: [http://nagios.org](http://nagios.org)

Naigos is an all in one monitoring solution that can even send email alerts and SMS messages to your cell phone on critical alerts and such.

The problem is you will have to configure every monitor manually.  Searching around google should do the trick!

If you want something more simple, maybe a cron job snarfs data from lm_sensors, then sftps the data to where you wants it, or copy it to a web accessable directory.  That should give you a nice dirty fix for what you want.

---

### Post by Woody1987 on 2008-07-10
thx carcdrcdr, i gave nagios a try and managed to get it up and running. I checked google for ways to use it to capture temperatures and i was unsuccessful in finding the relevant information. Any help with nagios would be apprecitated. I am also interested in your second idea but i dont know where to start on that front. Any help with that is also apprecitated.

---

### Post by carcdrcdr on 2008-07-10
Do you have the skillz required to write simple script that outputs your tempature?

If so you can just write that script and then configure nagios to run that script to output the temp.

Here is a good read on getting into nagios basics: (up and running)
[http://www.debian-administration.org/articles/299](http://www.debian-administration.org/articles/299)

And setting up monitors via SNMP with your custom script:
[http://www.kilala.nl/Sysadmin/index.php?id=729](http://www.kilala.nl/Sysadmin/index.php?id=729)

Here is an example script on ubuntu useing lm-senors for temp:
[http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors](http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors)

Hope that helps, using Nagios may be more work then you want to commit to this project (but it will be worth it in the end)  If you just want the script solution have the script output its data via cron to your web dir... here is an example crontab that checks temp every 5 mins:
*/5 * * * * /monitor/temp.sh

Just make sure to direct output to your '/var/www' folder (or wherever apache DocumentRoot lives) with the '>' operators.

---

