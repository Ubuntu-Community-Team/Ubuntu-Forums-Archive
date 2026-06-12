---
title: "[SOLVED] Skype Audio Issues"
date: 2008-11-28
forum: General Help
---

### Post by clyde9999 on 2008-11-28
I have an IBM NetVista P4 2.4 Gig HZ cpu, Intel 82801DB-IC4H audio platform. Ubuntu 8.10 Intrepid Ibex. Skype worked fine with 8.04.1, but with Ibex, I cannot get skype to work with the built in audio platform. No matter what audio options I choose, I get an error message "Problem with Audio Playback" in the call window. I am not sure if I am in the  right part of this forum. Sorry if I am not.

clyde9

---

### Post by sstusick on 2008-11-28
I had this problem too...all I had to do was kill pulse audio and everything was fine again.

---

### Post by rajeev1204 on 2008-11-28
> **clyde9999 said:**
> I have an IBM NetVista P4 2.4 Gig HZ cpu, Intel 82801DB-IC4H audio platform. Ubuntu 8.10 Intrepid Ibex. Skype worked fine with 8.04.1, but with Ibex, I cannot get skype to work with the built in audio platform. No matter what audio options I choose, I get an error message "Problem with Audio Playback" in the call window. I am not sure if I am in the  right part of this forum. Sorry if I am not.

clyde9

Go to audio settings and select pulse for output instead of default and try changing similarly for input if u have problems hearing your own voice.

Trust me it works.

Also make sure nothing is muted in ubuntu volume settings on right side of panel.

---

### Post by clyde9999 on 2008-11-28
> **rajeev1204 said:**
> Go to audio settings and select pulse for output instead of default and try changing similarly for input if u have problems hearing your own voice.

Trust me it works.panel.

Thank you so much, and yes it works very well now. I am up and running again. One problem solved after another is sure making my week a good week.

clyde9999 :popcorn:

---

