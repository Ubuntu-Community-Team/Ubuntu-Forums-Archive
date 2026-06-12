---
title: "use rcp to copy files, met: unknow host"
date: 2008-07-11
forum: General Help
---

### Post by Hxsrmeng on 2008-07-11
Hi

I try to use rcp to copy files and got an "unknown host" message. 

$rcp myfile usrname@remoteIP:/remotefolder/remotefile
::ffff:remoteIP: unknown host

I use the remoteIP in this command, because I only know the IP address of the remote machine, don't know its name.

This command worked well between these two machines before, but ran into "unknown host" problem today.

I tried:
From my machine,
ping remoteIP, and remoteIP is alive
copy file to remoteIP with "scp", works
rsh to remoteIP to do "ls", works
copy file to a 3rd machine with "rcp", works

From the remoteIP,
ping my_machine, alive
copy files to a 3rd machine with "rcp", works
copy files to my machine with "scp", works
copy files to my machine with "rcp", shows: "permission denied"

I checked the /etc/hosts on both machines. It seems /etc/hosts files on both machines don't have information of the other's. Should I add remoteIP to the /etc/hosts on my machine? 

I also checked /etc/resolv.conf. They share the same domain, but different name server(this might not be related).

Could you give me any hints? Thanks.

BTW: I have to use "rcp" instead of "scp".

---

### Post by dcstar on 2008-07-12
> **Hxsrmeng said:**
> Hi

I try to use rcp to copy files and got an "unknown host" message. 
........
Should I add remoteIP to the /etc/hosts on my machine? 
.......

Yes.

---

### Post by Hxsrmeng on 2008-07-15
> **dcstar said:**
> Yes.

Thanks. But what's your suggestion?

---

