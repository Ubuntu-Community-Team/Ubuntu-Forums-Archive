---
title: "Plugin-container keeps running after use"
date: 2011-11-26
forum: Hardware
---

### Post by scarleo on 2011-11-26
Hi, I have been looking into some power saving on my laptop recently. One thing that is bugging me is that plugin-container doesn't quit after it has been used. It keeps running and using 1-3% CPU constantly without really performing any tasks. What I have done:

1. Start Firefox with one tab without flash (blocked with noscript), run ps -e | grep plugin, no plugin-container is running.
2. Go to a site that has flash video, run ps -e | grep plugin, plugin-container is running.
3. Close the tab that has flash video on it and make sure there is no flash on the only active tab (all scripts blocked with noscript)
4. Run top and watch plugin-container continue to run with 1-3% CPU usage
5. Wait, wait and wait for 5 hours, run ps -e | grep plugin, plugin-container is still running with 1-3% CPU usage.

What I expect would be that plugin-container is terminated when it is no longer needed to save power and performance, there is no need for it to run when there is nothing for it to do. Firefox is obviously capable of starting it, it should also be able to terminate it and then start it again when it is needed.

Is there a reason for this behaviour? Is the problem with Firefox or with Ubuntu? (i.e. Where should I file bug report?)

---

