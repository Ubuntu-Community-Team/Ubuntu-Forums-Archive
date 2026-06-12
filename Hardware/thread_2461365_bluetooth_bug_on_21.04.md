---
title: "bluetooth bug on 21.04"
date: 2021-04-29
forum: Hardware
---

### Post by incedis on 2021-04-29
This seems to be hitting a few people. 
Was running 20.10 and never had issue. 
Upgraded to 21.04 and bluetooth disconnects randomly and reconnects. I never had issue with the this bluetooth speaker running 20.10. This is a fresh install of 21.04.
```

profiles/audio/avdtp.c:avdtp_connect_cb() connect to F4:4E:FD:19:52:4D: Host is down (112)
avril 29 07:19:10  bluetoothd[25742]: plugins/policy.c:reconnect_timeout() Reconnecting services failed: Operation already in progress (114)
```

---

