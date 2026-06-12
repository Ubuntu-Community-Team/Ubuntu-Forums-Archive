---
title: "scheduling shell script in crontab"
date: 2008-08-13
forum: General Help
---

### Post by madhatter563 on 2008-08-13
I am attempting to schedule my script to run every minute.  I add this in crontab (using crontab -e) and then verify it added okay.  The command will not execute.  I restarted the machine, ran the same exact commands in terminal and then it ran fine.  Am I doing something wrong?  Do I need to add extra steps for crontab?  Thanks in advance.

```
* * * * * ./home/user1/scripts/sys-stat.sh
```

---

### Post by kpkeerthi on 2008-08-13
Change it to 
```
* * * * * /home/user1/scripts/sys-stat.sh
```

---

### Post by madhatter563 on 2008-08-13
thanks for the response!  Well.. I tried that and it did seem to start the script!  The odd thing now is that it is not finishing it.  For example, at the start of the script I have it ping several machines.  It only logs the result of one and then doesn't log any more.  However, I ran it manually again and it completed just fine.  I didn't think executing from cron would make the script execute differently? :confused:

---

### Post by madhatter563 on 2008-08-13
Any ideas?

---

### Post by madhatter563 on 2008-08-13
So it looks like if the ping is unsuccessful its gets hung up.  If I comment out the unsuccessful pings and then let it run it completes just fine.  Is there something I can do to get it to run successfully without having to comment out those lines? ...because commenting it out defeats the whole purpose. :(

---

### Post by Mister.Vash on 2008-08-14
Not sure if this would help, but what options are you giving to ping?
something like this
```
ping -c 5 -w 6 google.com
```
would try to ping google 5 times and give up if that didn't occur in 6 seconds

From the man page for ping
 -c count
Stop  after  sending  count  ECHO_REQUEST packets. Withd eadline option, ping waits for count ECHO_REPLY packets, until the time&#8208;out expires.

-w deadline
              Specify  a  timeout, in seconds, before ping exits regardless of how many packets have been sent or received. In this  case  ping does  not  stop after count packet are sent, it waits either for deadline expire or until count probes are answered or  for  some error notification from network.

---

### Post by madhatter563 on 2008-08-21
nope that doesn't seem to make any difference..

---

