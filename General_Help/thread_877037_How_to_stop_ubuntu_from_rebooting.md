---
title: "How to stop ubuntu from rebooting?"
date: 2008-08-01
forum: General Help
---

### Post by Ashy72 on 2008-08-01
Hi this is driving me nuts now. How can I stop my headless ubuntu linux box from re-booting on its own automatically. I only use it as a music server and it stops my music at random times when i am listening to it when the machine reboots. The machine rebooted at 15:32 it may be something to do with anacron? what is it? do i need it? can i get rid of it? I have prevented automatic updates for everything in software sources I update manually once a week now. If anyone can help many thanks in advance.  

here is a log:-

Aug  1 15:32:24 Black-Widow syslogd 1.5.0#1ubuntu1: restart.
Aug  1 15:32:24 Black-Widow anacron[5493]: Job `cron.daily' terminated (mailing output)
Aug  1 15:32:24 Black-Widow anacron[5493]: Job `cron.weekly' started
Aug  1 15:32:24 Black-Widow anacron[7061]: Updated timestamp for job `cron.weekly' to 2008-08-01
Aug  1 15:32:31 Black-Widow kernel: [ 1727.935236] Outbound IN= OUT=eth0 SRC=192.168.1.68 DST=208.67.222.222 LEN=57 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39892 DPT=53 LEN=37 
Aug  1 15:32:31 Black-Widow kernel: [ 1727.941568] Outbound IN= OUT=eth0 SRC=192.168.1.68 DST=208.67.220.220 LEN=57 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60824 DPT=53 LEN=37 
Aug  1 15:32:32 Black-Widow syslogd 1.5.0#1ubuntu1: restart.
Aug  1 15:32:32 Black-Widow anacron[5493]: Job `cron.weekly' terminated
Aug  1 15:32:32 Black-Widow anacron[5493]: Normal exit (2 jobs run)
Aug  1 15:43:12 Black-Widow nmbd[5155]: [2008/08/01 15:43:12, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Aug  1 15:43:12 Black-Widow nmbd[5155]:   find_domain_master_name_query_fail: 
Aug  1 15:43:12 Black-Widow nmbd[5155]:   Unable to find the Domain Master Browser name MSHOME<1b> for the workgroup MSHOME. 
Aug  1 15:43:12 Black-Widow nmbd[5155]:   Unable to sync browse lists in this workgroup. 
Aug  1 15:58:18 Black-Widow nmbd[5155]: [2008/08/01 15:58:18, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351) 
Aug  1 15:58:18 Black-Widow nmbd[5155]:   find_domain_master_name_query_fail: 
Aug  1 15:58:18 Black-Widow nmbd[5155]:   Unable to find the Domain Master Browser name MSHOME<1b> for the workgroup MSHOME. 
Aug  1 15:58:18 Black-Widow nmbd[5155]:   Unable to sync browse lists in this workgroup.

---

### Post by madhusker on 2008-09-03
This post is 4 weeks old!  This is a major problem and no resolve.  Any admins on here??

---

### Post by Ashy72 on 2008-09-09
Thanks Madhusker for your concern it doesnt look like this is going to be resolved.

FYI I have managed to stop the automatic reboots by switching off all updates, not what I really want to do. I was on notify of updates before and as I run headless this is useless anyway. Now I just have to do a manual search for updates once a week and then turn them off again.

---

### Post by djp3 on 2008-09-15
FWIW, I have the same problem. Random reboot of my HP DL160 headless server running Ubuntu 8.04. In my case I'm actually rebooting. I have a 4 drive RAID also.  I'm not automatically updating though.

---

