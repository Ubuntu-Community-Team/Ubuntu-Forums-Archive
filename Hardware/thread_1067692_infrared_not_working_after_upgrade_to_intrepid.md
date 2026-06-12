---
title: "infrared not working after upgrade to intrepid"
date: 2009-02-12
forum: Hardware
---

### Post by pierref on 2009-02-12
Hello

After upgrading to Intrepid, irda no longer works. I applied points 1 to 11 of the first option described in [https://help.ubuntu.com/community/IrdaHowto]("https://help.ubuntu.com/community/IrdaHowto").

Well, irdadump works:); my PDA is detected:

```

$ sudo irdadump
09:58:51.003657 xid:cmd 3a617547 > ffffffff S=6 s=0 (14) 
09:58:51.091650 xid:cmd 3a617547 > ffffffff S=6 s=1 (14) 
09:58:51.179662 xid:cmd 3a617547 > ffffffff S=6 s=2 (14) 
09:58:51.267652 xid:cmd 3a617547 > ffffffff S=6 s=3 (14) 
09:58:51.352885 xid:rsp 3a617547 < 07931e69 S=6 s=3 Pierre Francois hint=8220 [ PDA/Palmtop IrOBEX ] (33) 
09:58:51.355662 xid:cmd 3a617547 > ffffffff S=6 s=4 (14) 
09:58:51.443653 xid:cmd 3a617547 > ffffffff S=6 s=5 (14) 
09:58:51.531654 xid:cmd 3a617547 > ffffffff S=6 s=* papagolf hint=0400 [ Computer ] (24) 

```

but pilot-xfer freezes. I issue

```
$ pilot-dlpsh -p /dev/ircomm0 -i

   Listening for incoming connection on /dev/ircomm0... ^C

```

and I start a HotSync on my Palm on the IR port. Nothing happens, till I interrupt it with ^C. The Palm gives an error message: "The connection between your handheld computer and the desktop could not be established. Etc..." :(

Same problem with ircp and irxfer: these are waiting for files and nothing happens.

My question is: when irdadump recognizes my handheld, what could be wrong in my irda settings.

---

