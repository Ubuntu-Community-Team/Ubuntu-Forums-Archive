---
title: "Can't start ccpd"
date: 2009-12-25
forum: Hardware
---

### Post by AmrH on 2009-12-25
While setting up my Canon LBP3010, I followed [the guide posted by [URL="https://launchpad.net/%7Ethomaslloyd"]TommyBoy]("https://help.ubuntu.com/community/LBP3010")[/URL] and I was able to print a test page; however, after rebooting, I found out that only one of the 2 ccpd processes is alive. Whatever I try to do to start ccpd properly fails. It doesn't even give me more info than 
```

amr@amr-desktop:~/Desktop$ sudo /etc/init.d/ccpd start
 * Starting Canon Printer Daemon for CUPS: ccpd                          [fail] 

```Would somebody please help me with that? I've already followed each step in the guide. It was supposed that the ccpd should startup properly; however, it's still not working.

---

### Post by giruzz on 2009-12-28
> **AmrH said:**
> While setting up my Canon LBP3010, I followed [the guide posted by [URL="https://launchpad.net/%7Ethomaslloyd"]TommyBoy]("https://help.ubuntu.com/community/LBP3010")[/URL] and I was able to print a test page; however, after rebooting, I found out that only one of the 2 ccpd processes is alive. Whatever I try to do to start ccpd properly fails. It doesn't even give me more info than 
```

amr@amr-desktop:~/Desktop$ sudo /etc/init.d/ccpd start
 * Starting Canon Printer Daemon for CUPS: ccpd                          [fail] 

```Would somebody please help me with that? I've already followed each step in the guide. It was supposed that the ccpd should startup properly; however, it's still not working.


How did you solve it?

thanks

giruzz

---

### Post by 2ways on 2009-12-31
Yes.  Please post solution.

Am having the same problem.

Thanks,
Lewis

---

### Post by AmrH on 2010-01-01
For those who want to know how I solved this, I backed up the configuration file, over wrote what was in it with the script in the tutorial and restarted my computer. By that time, I had two running ccpd services.

---

### Post by 2ways on 2010-01-04
Can anyone tell us what the two processes are that are supposed to be running?

Thanks,
Lewis

---

### Post by notlistening on 2010-01-04
Your looking fpr these processes:

 1921 ?        00:00:00 ccpd
 1930 ?        00:00:01 ccpd
 1931 ?        00:00:01 captmoncnab8

The Process ID are going to be different but essentially you have to have the two ccod processes and the third is the status monitor which is not essential.

Between these two they communicate to render and send throught the print job. 

If you only see one process then there is a problem and if the status monitor is not showing that is because it can not connect to the ccpd process to access the status information.

Problems might be the the script in etc/init.d/ccpd is not executable by root, if you created a new one. Symptoms of this would be that after login there are no ccpd processes running.

so running:
ps -A | grep ccpd

Should give you somthing like this:

1921 ?        00:00:00 ccpd
1930 ?        00:00:01 ccpd

If you are getting just one ccpd process then this means the the stage at which ccpd is being launched is too early and that communication can not be established with the printer. If you are following the guide then this might be hardware issue but we can identify this based on your feedback.

Working out the status of the ccpd processes will give a clue as to what the problems are. 

You can also run:
top

and if ccpd is the top of the list then you have  a problem where the script is being started during boot. At the moment i start it at login at the same time as pulseaudio just before you get a login prompt so that you do not have to login to get the comptuer to print as a server. 

If you also post the version of Ubuntu you are using then that will also help.

Sorry for the slow reply just got back from Egypt today.

---

