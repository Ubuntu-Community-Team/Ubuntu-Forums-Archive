---
title: "Hp printer not working with Hardy"
date: 2008-09-20
forum: Hardware
---

### Post by billbog on 2008-09-20
Hi - I cannot get my Photosmart P1000 to work with Hardy. It prints gibberish. Test page prints fine.

root@bill:/home/bill# tail -f /var/log/cups/error_log
E [18/Sep/2008:11:58:51 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [20/Sep/2008:12:44:33 +0100] Unable to execute /usr/lib/cups/backend/hp: No such file or directory
E [20/Sep/2008:12:44:33 +0100] [Job 4] Unable to start backend "hp" - No such file or directory.
I have downloaded hplip 2.8.9 tar gz file as I was getting nowhere with automatic install could someone tell me how to use it.

---

### Post by 1/0 on 2008-09-20
Have you installed the hpijs back end?

---

### Post by billbog on 2008-09-24
Yes it looks like  that got it working - many thanks

---

### Post by jimdwa on 2009-06-26
I had the same problem on 9.04 after installing KDE desktop. This fix worked for me, thank you very much for the information. I couldn't use the apt-get --reinstall option. I was getting the dreaded "is not possible cannot be downloaded". So I just did ap-get remove. Now my HP printer is installed and visible on the network. And it prints!!
Commands:
  sudo /etc/init.d/cups stop
  sudo apt-get remove hplip
  sudo apt-get remove hpijs
  sudo apt-get install hpijs
  sudo /etc/init.d/cups start

---

