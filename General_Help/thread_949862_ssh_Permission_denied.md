---
title: "ssh Permission denied"
date: 2008-10-16
forum: General Help
---

### Post by linux8654 on 2008-10-16
SSH authentication fails for an unknown reason. I am running Ubuntu and both a remote server and my laptop.  When I attempt to ssh into the remote server from my laptop, I receive a permission denied error.  However if I ssh into another Linux machine from my laptop and then ssh into into my remote server, I can log-in.  

I have root access on both the remote server and my laptop. I have also unsuccessfully tried logging into the server from multiple IP-Addresses. 

Any help resolving this issue is appreciated.

Thanks,

Ethan

---

### Post by shawnrgr on 2008-10-16
Please post how you are connecting. remember you need to specify user@host. If you just specify host then your usernames must match.

pc1 (192.168.1.100 username=shawn)
pc2 (192.168.1.101, username=ubuntu)

shawn@pc1$ ssh ubuntu@192.168.1.101

the above would work because you specified a user that exists on the remote box

shawn@pc1$ ssh 192.168.1.101

this would not work because ssh will assume a remote username of 'shawn' which doesn't exist on the target machine.

Hope that helps!

---

### Post by linux8654 on 2008-10-16
I am connecting using the following:
```
ssh user-name@remote-Server
```
where user-name is the user name on the remote server
and remote-Server is the Address of the Remote Server

I can connect to the remote Server from any machine except directly from my laptop

---

### Post by HermanAB on 2008-10-16
Turn on verbosity to see what is going on:
ssh -vvv user-name@remote-Server

A little bit of staring at the screen should give you a clue.

Cheers,

Herman

---

### Post by geirha on 2008-10-16
Check the logs on the server, they should explain why it's denying access to your laptop. /var/log/auth.log is the file you want to check.

---

### Post by shawnrgr on 2008-10-16
Do you have Firestarter configured or something of that nature? Maybe its allowing your laptop and nothing else?

---

### Post by linux8654 on 2008-10-16
I tried > ssh -vvv user-name@remote-Server
I did this from my laptop, and a different computer where I was able to log-in, then compared the files.  I did not see anything distinguishable discrepancies of the comparing the output from using verbosity.

On the remote server, I checked /var/log/auth.log
It displays the successful log-ins when I log-in from other machines, but it does not display any failed log-in attempts from my laptop.

I am using fireStarter, however I have an exception for ssh access.  Further more I was previously able to login to my remote server from my laptop, until just recently.  I can not pinpoint any changes which led up to the denied access from my laptop.

---

