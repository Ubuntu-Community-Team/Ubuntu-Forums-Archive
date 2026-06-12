---
title: "Cannot burn anything to DVD. Could use some help, possible driver issue?"
date: 2016-06-18
forum: Hardware
---

### Post by marcus39 on 2016-06-18
Hi everyone. I'm fairly new to Ubuntu as a laptop OS. I'm a long-time developer and user/admin of linux servers.

I've recentlly installed 16.04 on my laptop. Most things work well but I cannot seem to use my DVD writer. It might legitimately be the case that I simply don't know how to use the UI well. I've worked in Linux flavors for years but always command-line. This is my first experience using the desktop environment.

However, I'm pretty sure I'm "doing it right" and something just seems off. When I right-click on the ISO I'm trying to burn (windows 10) I don't see a "write to disk" option. I've opened the disk creator but still just can't seem to get it.


Possibly related - I'm also running Virtual Box. I've tried to mount the .iso to the listed optical drive but I get an error with that also.

Can anyone offer advice on how to begin/proceed to troubleshoot? 

Thank you in advance!

---

### Post by coldraven on 2016-06-18
If you are using Brasero* I have never had much luck with it. Try installing K3B, it does have more dependencies because it's a Kubuntu utility but it's always worked for me. To create a bootable disc select "Burn Disc Image" from the menu.

*Brasero is the default Ubuntu disc burner

---

### Post by marcus39 on 2016-06-20
This comment was helpful, thank you. K3B is a much nicer tool and helped me identify I had a bad file. Thanks for pointing me in the right direction.

---

