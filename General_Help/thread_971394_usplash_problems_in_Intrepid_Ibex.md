---
title: "usplash problems in Intrepid Ibex?"
date: 2008-11-04
forum: General Help
---

### Post by VengefulIce on 2008-11-04
Hi,

I just upgraded from Hardy to Intrepid, and now my splash screens do not work.

I have already tried to reinstall the usplash package to no avail.

Any other suggestions?

Thanks

---

### Post by red_team316 on 2008-11-07
There is nothing wrong with usplash in 8.10 Intrepid. Anyone wanting to use a custom usplash will have to recompile it on an Intrepid box.

There were obviously changes to usplash from Hardy 8.04 to Intrepid 8.10. One of those changes was changing the THEME VERSION to 3. I'm not 100% sure if this is the reason why the old usplashes wont work, but I'm betting on it. A dapper(THEME VERSION 1) usplash doesn't work on Edgy(THEME VERSION 2). It makes sense to me that a hardy(THEME VERSION 2) usplash theme does not work on intrepid(THEME VERSION 3).

[https://launchpad.net/ubuntu/+source/usplash](https://launchpad.net/ubuntu/+source/usplash)

Somebody just needs to update the Usplash Customization page as to what we can do with the new API changes...

---

