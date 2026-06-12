---
title: "Brother scanner driver needs to be updated for 12.04"
date: 2012-09-12
forum: Hardware
---

### Post by feydrutha on 2012-09-12
Thought i'd post this since it might be useful to someone else.

My brother MFC 8690-DW was previously scanning just fine over the network on my ubuntu host, but was not functioning anymore (on an up-to-date 12.04). 

I am not sure what update broke it, but thankfully the [brother drivers webpage]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html") has a news section that states the brscan4 and brscan3 drivers were updated in June 2012.

So it was just a matter of downloading the updated driver and once again following [the instructions]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html"):

In my case, what i did is:

```
 dpkg -i --force-all brscan4-0.4.1-1.amd64.deb 
 brsaneconfig4 -a name=SCANNER model=MFC-8690-DW ip=X.X.X.X
```

---

