---
title: "snort not logging to alert file"
date: 2008-09-03
forum: General Help
---

### Post by fast-Eddie on 2008-09-03
Hi,

I new to Ubuntu and have just installed snort 2.8.2.2 and Base 1.4.1. The install seemed to have gone okay however nothing is being logged to the /var/log/snort/alert file. I assume that none of the stats on the main BASE site update because this log is empty. 

I have checked for running instances of snort and get the following:

@ubuntu804desktop:/var/log/snort# ps -aux | grep snort
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root     24812  0.1  0.0 128020     8 pts/0    T    12:40   0:09 snort -c /etc/snort/snort.conf
root     24934  0.1  1.9 128172 10220 ?        Ss   12:54   0:08 snort -c /etc/snort/snort.conf -i eth1 -D
root     25400  0.1  8.6 128100 44700 pts/2    T    13:27   0:09 snort -c /etc/snort/snort.conf
root     25683  0.4 20.6 128076 106604 pts/2   S+   14:16   0:08 snort -c /etc/snort/snort.conf
root     25772  0.0  0.0   1652   280 pts/0    R+   14:48   0:00 grep snort
root@ubuntu804desktop:/var/log/snort# 

I have also tried running ´nmap -sS <my_IP> however this doesn´t log anything to the alert file either. 

Any ideas??

---

### Post by Mister.Vash on 2008-09-03
It could be a permission issues with the snort log files.  To test that out, navigate to the snort log directory and then do a try a sudo chmod 666 alert

Then restart snort and see if it logs.  If if does, then we just need to see what the correct ownership of the file should be

---

### Post by fast-Eddie on 2008-09-03
Hi,

Its not a permissions issue as I already did a chmod 777 on the alert file.

Any other suggestions.

---

