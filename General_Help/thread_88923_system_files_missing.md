---
title: "system files missing"
date: 2005-11-11
forum: General Help
---

### Post by holiday on 2005-11-11
I have two ubuntu machines. They have both been configured for nfs and this was successfully working until I tries to run exportfs on one of the machines. The file has gone. And not only exportfs. I ran a diff on the two /usr/sbin directories. The output is below.

Because of the selection of deleted files, I'm wondering if I have an intruder. Am I paranoid? A disc errror would not be so selective, I don't think.

chkrootkit finds no problems.

 
1```
6d15
< automount
48a48
> exportfs
50a51
> firestarter
77a79
> inetd
103d104
< mksmbpasswd
106d106
< nmbd
108d107
< ntp-keygen
130d128
< regionset
142a141
> rpc.svcgssd
151d149
< smbd
152a151
> statd

```

---

### Post by holiday on 2005-11-11
So  fixed the problem by apt-get-remove and apt-get-install nfs-kernel-server.

I'll just have to watch the ports, I guess

---

