---
title: "Hibernate after x minutes sleep?"
date: 2008-07-09
forum: Hardware
---

### Post by bobpaul on 2008-07-09
On Windows if your battery gets critically low, it will wake up from sleep mode and initiate a hibernate. This tells me that the processor must either have some pin interrupt running that's connected to a voltage monitor /or/ the processor is waking up every 500ms or so to poll the battery state.

If the second is the case, I see no reason why a counter couldn't be incremented every time the processor wakes up--ie, it should be possible to have the computer go to sleep and once it's been asleep for say, 10 minutes, wake up and proceed to hibernate. Does anyone know if this is already possible to configure?

---

