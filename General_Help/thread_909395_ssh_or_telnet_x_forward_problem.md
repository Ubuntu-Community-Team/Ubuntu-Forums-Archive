---
title: "ssh or telnet x forward problem"
date: 2008-09-03
forum: General Help
---

### Post by charbo on 2008-09-03
Hello all,

My colleague has been using his Windows desktop to telnet into a linux server, and forward the Display back onto his desktop to use some gui application on the server.  He has been having some minor problems, and asked me to help him set up a Linux machine to be a client for this.

I was pretty confident that he was talking about X11 forwarding, and I was also confident that this would be an easy task.

Before purchasing a new machine for this purpose, we decided to try it out using an existing linux machine as a client.

I made sure that the server's sshd_config said "X11Forwarding yes", and client's ssh_config said "ForwardX11 yes".  Every time he connects, he issues the command "setenv DISPLAY client'sIP:0.0", which seems correct.  

I made him try ssh, ssh -X, ssh -Y, and xhost + and telnet, but all of them allow him to connect to the server, but when he runs an x application, it just spits out display connection error.  Even xclock & says "Error: Can't open display: client'sIP:0.0".

The server is running Red Hat Enterprise 3, and the client is running breezy kubuntu.

Any idea as to why telneting from Windows works and not from kubuntu?

Any pointer I can get is highly appreciated.

---

### Post by Nepherte on 2008-09-03
You have to run an X server on the client (the computer from where you are accessing your linux server) as well. This one for example: [http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

---

### Post by charbo on 2008-09-03
Yes, and X is running.
We are accessing the server from Konsole in Xfce or KDE on Kubuntu breezy.

---

### Post by monkeyking on 2008-09-03
check your display env.

```
echo $DISPLAY
```

If it's wrong then export proper values

---

