---
title: "Problem with ftp"
date: 2008-11-26
forum: General Help
---

### Post by jarl on 2008-11-26
I am running Kubuntu Intrepid AMD64
I have problems using ftp (client). I manage some websites and one of them does not give me the prompt for user login/password, not even the welcome message.

I try to connect to [ftp://skovtrold.dk](ftp://skovtrold.dk), but it just hangs after writing "Connected to skovtrold.dk.", try out your self.

I have tried ftp, tnftp, ncftp, filezilla, and many others. What I can say is that I do get the welcome message from a windows box (guested in vmware), and also from a SuSE 11 (guested in vmware).

So I wonder if there is some firewall software running on a Intrepid that I should disable?

ftp'ing to other hosts ([ftp://ftp.gavia.dk](ftp://ftp.gavia.dk)) works fine

Please help.

Jarl

---

### Post by fatphilthethird on 2008-11-27
[ftp://skovtrold.dk](ftp://skovtrold.dk), works for me

Fat

---

### Post by jarl on 2008-11-27
Thanks a lot for trying. What kernel version are you running? I am using 2.6.27-7-generic
I also just tried from a preinstalled Ubuntu 8.10 64bit virtual machine (on vmware) downloaded from tuxdistro ([http://www.tuxdistro.com/torrents-details.php?id=1363](http://www.tuxdistro.com/torrents-details.php?id=1363)). On this VM (running kernel 2.6.27-7) I couldn't reproduce the problem there either.

Does anybody please have some hints on what could be wrong with my system? Kernel configurations? IPV6? iptables? firewall? blacklisting? anything?

I found this link, which may be related:
[http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon](http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon)

The last commenter mentions he still can't use ftp.

Jarl

---

### Post by fatphilthethird on 2008-11-27
Windows box, am at work.

Fat

---

### Post by Peter09 on 2008-11-27
This link works for me as well.

Try using a different ftp client (gftp) it might provide more information.

---

