---
title: "Shell command to show system usage stats?"
date: 2008-11-26
forum: General Help
---

### Post by ryodoan on 2008-11-26
Hello, I have just started playing around with creating an Ubuntu server.  I don't know a lot about linux but am doing this as a learning experience (and for fun).

In any case, when I log into my server over SSH I receive a welcome message as follows:
[IMG]http://img260.imageshack.us/img260/9738/sshws9.png[/IMG]

My first question is, is there a command that I can use to print out the system information similar to what the welcome message displays?  

My next question is, how do I go about customizing the welcome message? 

Thanks for your help.

---

### Post by kanikilu on 2008-11-26
/etc/motd has the welcome message. I'm not sure about the stats, though.

*EDIT* - Actually the file you'd want to edit is probably motd.tail

*EDIT 2* - The command for those stats is "landscape-sysinfo"

---

### Post by ryodoan on 2008-11-26
Wow, thanks for the excellent and fast reply, that is exactly what I was looking for.

---

