---
title: "RSSOwl + Internal Web browser problems"
date: 2005-11-05
forum: General Help
---

### Post by danj205 on 2005-11-05
I don't get it. I followed the Ubuntu Starter guide to get the internal web browser to work (that's why I got RSSOwl because it is the few RSS readers that do that).

When I first got it "working" Firefox actually kept crashing (up to the point where typing about:plugins b0rked firefox until I removed the Sun java plugin). After doing that, RSSOwl now only randomly crashes. Sometimes I can browse a couple of items and then it'll crash, or I just click on an item and it'll crash.

I'm using Breezy (default Firefox too), with Sun Java 1.5 and I first tried RSSOwl 1.2RC1, but also tested RSSOwl1.1.3.

I added this to their run.sh:
```
export MOZILLA_FIVE_HOME=/usr/lib/mozilla-firefox
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:${MOZILLA_FIVE_HOME}
```

Oh, and the error I got in the terminal was:
```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xafdd9bf7, pid=14282, tid=3084793536
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_05-b05 mixed mode, sharing)
# Problematic frame:
# C  [libtoolkitcomps.so+0x29bf7]
#
# An error report file with more information is saved as hs_err_pid14282.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
run.sh: line 5: 14282 Aborted                 java -Xmx134217728 -jar -Djava.library.path=. rssowl.jar
```

Anyone have any ideas?

Thanks

---

### Post by magnusbb on 2005-11-28
I have the same problem. Is it possible to changes to another browser for internal use, perhaps the old standard Mozilla?

---

### Post by danj205 on 2005-11-28
Yeah, I solved the problem. Install mozilla-browser and change the script so then it points to that instead. Firefox support is apparently sketchy.

---

