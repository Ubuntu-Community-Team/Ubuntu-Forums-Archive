---
title: "Disconnecting from internet because ip-down is being executed"
date: 2008-08-26
forum: General Help
---

### Post by jonian_g on 2008-08-26
This is what I get from the modem log when it disconnects. I have a Linksys WAG200G modem router and i'm running Ubuntu 8.04.
Does anyone have an idea why this happens?

```
Tue, 2008-08-26 17:54:12 - run_program(/etc/ppp/ip-down) 

Tue, 2008-08-26 17:54:12 - chld,got_sigchld=1 

Tue, 2008-08-26 17:54:12 - ret=3312 

Tue, 2008-08-26 17:54:12 - LCP down. 

Tue, 2008-08-26 17:54:12 - reap_kids,waitfor=0 

Tue, 2008-08-26 17:54:12 - This terminate is called from lcp_finished() 

Tue, 2008-08-26 17:54:12 - Connection terminated. 

Tue, 2008-08-26 17:54:12 - Connect time 10.7 minutes. 

Tue, 2008-08-26 17:54:12 - Sent 588515 bytes, received 29541461 bytes.
```

---

