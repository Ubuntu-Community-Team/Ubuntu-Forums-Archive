---
title: "[SOLVED] how to throttle duplicity?"
date: 2008-08-22
forum: General Help
---

### Post by pluggy13 on 2008-08-22
Hi,

I'm using duplicity ([http://duplicity.nongnu.org/index.html](http://duplicity.nongnu.org/index.html)) to encrypt and backup large amounts of data onto my offshore server.

The upload usually takes hours and eats up almost the entire DSL bandwidth. How can I limit the duplicity's upload speed?

This is a typical example for the way I am using duplicity: 
 
duplicity /backupsourcedir scp://root\@myserver.net/~

Duplicity does not natively offer this feature, but since it is using scp or ftp for the upload, there might be a workaround. For example using throttle ([http://klicman.org/throttle/](http://klicman.org/throttle/)), but I do not know how to do this exactly. 

Thanks in advance for your time and help,

Adrian

---

### Post by qstraza on 2008-08-22
Pure ftp server allows you to specify upload and download speed for each virtual user you add, maybe this is a solution

---

### Post by pluggy13 on 2008-08-22
> **qstraza said:**
> Pure ftp server allows you to specify upload and download speed for each virtual user you add, maybe this is a solution

Actually a great idea, but duplicity is run by a cron job and the script running duplicity must not contain any passwords. Thus it looks like to need to stick to ssh / scp as underlying transfer method for duplicity.

---

### Post by qstraza on 2008-08-22
yea thats true, did not think about that;)
maybe you could add user and allow connection only from selected ip, so no password is needed (or is, doesnt matter), if this is posible in pureftp to set it up...

---

### Post by pluggy13 on 2008-08-22
> **qstraza said:**
> yea thats true, did not think about that;)
maybe you could add user and allow connection only from selected ip, so no password is needed (or is, doesnt matter), if this is posible in pureftp to set it up...

Unfortunately that won't work since I am doing the backups over a DSL line (which is why I want to throttle it in the first place). The IP is changing with every login to my ISP.

---

### Post by qstraza on 2008-08-22
well i use a script which dls from ftp daily, i put username and pasword in it, but its local pc, so no harm can be done...

You can make a ftp user which has very restricted rights (upload files in specified dir and no deleting), than u manipulate the data from where ftpd is running.

---

### Post by pluggy13 on 2008-08-23
Thanks for your suggestions, but I think I have a better idea - Simply installing wondershaper or trickle and then limiting the upstream of the linux box. 

Thanks to all for your help!

---

### Post by qstraza on 2008-08-23
what ever suits you the best ;)

EDIT:
Do you maybe know how could i limit a clients upload/download speed based on ip? I run a server on ubuntu and clients access the net via server... Ah hell, ill open a new thread

---

### Post by joenix on 2008-09-01
Duplicity has an option --scp-command and scp has an option to limit the bandwidth: '-l x', where x is the bandwidth expressed in kbit/s.
I have not tested it, but I would think passing something like '--scp-command "scp -l 256"' to duplicity should do the trick.

---

### Post by pluggy13 on 2008-09-01
> **joenix said:**
> Duplicity has an option --scp-command and scp has an option to limit the bandwidth: '-l x', where x is the bandwidth expressed in kbit/s.
I have not tested it, but I would think passing something like '--scp-command "scp -l 256"' to duplicity should do the trick.

Just what I was looking for and works like a charm. Thanks a lot, Joenix! =D>=D>=D>

---

