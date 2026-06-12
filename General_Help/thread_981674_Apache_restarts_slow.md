---
title: "Apache restarts slow"
date: 2008-11-13
forum: General Help
---

### Post by mech7 on 2008-11-13
I can't find anything in the error logs but restarting apache is really slow.. it does give some warnings about virtual hosts not being found.

Does anybody know what could be the cause :confused:

---

### Post by y@w on 2008-11-14
I've seen Apache do this once on one of my Ubuntu 8.04 servers.. In the logs it said something about creating digests. Then the next time it started up faster. How slow is really slow? Can you qualify that? You can also just do a reload of Apache rather than a restart. A reload will just reload the config and a restart will actually kill off the processes and spawn new ones. If you're just looking at changing a configuration then I'd use reload. It's almost instantaneous.

---

### Post by mech7 on 2008-12-03
> **y@w said:**
> I've seen Apache do this once on one of my Ubuntu 8.04 servers.. In the logs it said something about creating digests. Then the next time it started up faster. How slow is really slow? Can you qualify that? You can also just do a reload of Apache rather than a restart. A reload will just reload the config and a restart will actually kill off the processes and spawn new ones. If you're just looking at changing a configuration then I'd use reload. It's almost instantaneous.

Even force-reload is kinda slow.. but restarting takes minutes like upto 5 minutes which is waayyyy to slow i think. 

I do have allot of virtual hosts setup like around 20... I am not sure if this will have an effect.. but should not be that much i think.

---

