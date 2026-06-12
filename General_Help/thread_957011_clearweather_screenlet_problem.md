---
title: "clearweather screenlet problem"
date: 2008-10-23
forum: General Help
---

### Post by shahgols on 2008-10-23
Hi all,

I am having a problem with this screenlet not loading the weather.  It shows "no weather information available".  I see that the weather screenlets loads a few seconds before my laptop establishes wireless connection to the internet.  So when I log out and log back in, the weather shows up just fine.  So I guess the problem is that at the time this screenlet loaded, internet was not available, which makes sense.  But what can I do about it?  Is there a way around this problem?

---

### Post by shahgols on 2008-11-05
For those who have the same problem, I got around this problem by writing a little code that waits 25 seconds and then calls the weather screenlet.  Then I added this code to the list of things to run when the user logs in.  It does the job perfectly.

---

