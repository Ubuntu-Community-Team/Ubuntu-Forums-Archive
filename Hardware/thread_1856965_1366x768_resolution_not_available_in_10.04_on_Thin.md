---
title: "1366x768 resolution not available in 10.04 on Thinkpad 420s?"
date: 2011-10-09
forum: Hardware
---

### Post by ysg030 on 2011-10-09
I have a new Thinkpad 420s with a native screen resolution of 1366x768 (inbuilt Intel HD Graphic 3000 card). I installed Ubuntu 10.04 and everything worked fine except for the screen resolution. I read various forum posts which suggested changing the resolution using xrandr etc. I did all of that but nothing seemed to work. Then I read this post: [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/cant-increase-toshiba-laptop-resolution-to-1366x768-875523/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/cant-increase-toshiba-laptop-resolution-to-1366x768-875523/) which suggests that the Intel Sandy Bridge graphics are not supported in 10.04.

Is this correct? Does that mean there's nothing I can do (with this distribution at least)? I thought that maybe I should just install 11.04, but I can't get it to boot from the Live CD (obviously that's another problem). If there's some way to fix the resolution in 10.04 that would be my preference, but I'm happy to try another version or another distribution if that is the best option.

Thanks for any help. As is probably obvious, I'm a linux novice, so please try to explain any help you can offer on that level :)

---

### Post by 2F4U on 2011-10-09
There seems to be a way to get it working. However, it requires some effort, since you would need backported versions of some software packages.

[http://ubuntuforums.org/showthread.php?t=1747206&page=2](http://ubuntuforums.org/showthread.php?t=1747206&page=2)

---

### Post by ysg030 on 2011-10-10
Great, with the patched drivers everything is working perfectly. Thanks a lot!

---

