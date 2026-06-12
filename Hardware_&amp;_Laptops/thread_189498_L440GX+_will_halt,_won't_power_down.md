---
title: "L440GX+ will halt, won't power down"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by halfvolle melk on 2006-06-05
When I shutdown my computer, it will halt the system but doesn't shut the power down. It has an Intel L440GX+ server board in it.

This issue was around with Breezy and unfortunately is unresolved in Dapper. Either shutting down with System -> Quit or from terminal **shutdown now, halt, init 0** will result in the same thing. The button on the front only works for turning it on, but if I press it when the system has halted nothing happens.
I looked at the BIOS but I don't understand it, to many options for stuff I never heard of.

Thanks for any suggestions you may have.

---

### Post by fer5437 on 2006-06-05
I have the same issues like you. I been upgrade my Brezzy to Dapper and the last update on 31st May it bring me this issues. When I shut down it stop and hang. So what I do is just reinstall clean Dapper that been downloaded. I think that should be a bug.

---

### Post by halfvolle melk on 2006-06-05
Well, I didn't dist-upgrade, but did a clean Dapper install from the start. The problem that I had in Breezy I still have in Dapper.

---

### Post by givré on 2006-06-05
You probably have the same bug as a lot of people
[http://www.ubuntuforums.org/showthread.php?t=187186](http://www.ubuntuforums.org/showthread.php?t=187186)
There is a big in launchpad, add your comment
[https://launchpad.net/distros/ubuntu....15/+bug/43961](https://launchpad.net/distros/ubuntu....15/+bug/43961)

---

### Post by halfvolle melk on 2006-06-05
Ok, thanks. I missed that one.

---

### Post by givré on 2006-06-05
Wrong url for launchpad, sorry :cool: 

This one is ok
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961)

---

### Post by halfvolle melk on 2006-06-05
Yep, I found in your first link, thanks :). Unfortunately the fix suggested in that thread doesn't work for me. I'll continue over there.

---

