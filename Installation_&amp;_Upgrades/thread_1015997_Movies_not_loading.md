---
title: "Movies not loading"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by jafar3001 on 2008-12-19
Hey i just recently installed a bunch of firefox updates.  I now have a problem playing videos online.  Before I used to have to click on the video, then it would play.  Now it doesn't even let me click it.  

When I right click on the video, it says Movie not loaded..., but it doesnt let me click on it.  It also says About Adobe Flash Player 10, but I have the most recent version of Flash installed. 

I know this problem has something to do with the Firefox update, but can't figure out what.  Does anyone else have this problem or can help?

Thanks

---

### Post by stakken on 2008-12-20
I have the same problem, flash is up to date. I have tried to install flash manually. But it does not make any difference.

Sjoerd

---

### Post by stakken on 2008-12-20
I found it, flashblock does not work in combination with the adobe flashplugin since my last update.

When I removed flashblock (extention of firefox) all works well after restarting firefox.

```
sudo apt-get remove flashblock

```

---

### Post by ismoore999 on 2008-12-21
well spotted. 
I have also noticed that it is not as simple as this. Some sites do indeed work still (for example try last.fm) so there must be something that sites such as youtube or others (news.bbc.co.uk also fails) are doing that prevents flash from working.

---

### Post by ismoore999 on 2008-12-21
One other quick note on this - it appears to be that uninstalling flashblock as described in your email and then add flash block via the "add-ins" for firefox works fine. 

Maybe some versioning issue or something fixed in flashblock since the version packaged.

---

