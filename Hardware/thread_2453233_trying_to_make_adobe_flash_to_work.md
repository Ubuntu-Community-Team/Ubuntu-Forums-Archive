---
title: "trying to make adobe flash to work"
date: 2020-11-05
forum: Hardware
---

### Post by jgw on 2020-11-05
I have a problem with adobe flash.  I have deleted my current installation for flash and re-installed.  Same problem.  When it asks me to activate it comes up with a tiny kindofa long thing and then tells me I have error 2032.  I have found a lot of stuff on error 2032 but nothing seems to work.  the program I am running comes up as network video client and it displays some nvr cameras.  I have it working on another computer with no problem.  The difference is that the new installation always seems to end up as an addon for firefox called shockwave flash.  The machine that works shows no addon to firefox and works just fine.  I think my problem might be how I was installing adobe flash.  Apparently I am doing something wrong.

Thoughts?

---

### Post by TheFu on 2020-11-05
My only thoughts are these: 
[LIST]
[*]EoL: [https://www.adobe.com/products/flashplayer/end-of-life.html](https://www.adobe.com/products/flashplayer/end-of-life.html)
[*]Migrate to a non-Flash solution ASAP.
[*]Setup older minimal Ubuntu environments inside a VM or container to run only a browser+flash and nothing else. [https://stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/](https://stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/) is a little dated. Some others here have done similar. I have not.
[/LIST]
If you can get 18.04 + flash to work, fantastic. That provides a few more years to solve #2 above.

As usual, I'm very little help. Sorry.

---

### Post by ajgreeny on 2020-11-05
If it absolutely necessary to have flash on your system try ```
sudo apt install flashplugin-installer
``` which will pull in the most recent flash-plugin available.

However, like TheFu, I suggest you try to find alternatives to using flash, which is practically dead, insecure in its use, and will not be developed any more by Adobe after it becomes EOL Dec 31st 2020.

I can't really help with your specific problem of getting it to run in a browser, though I seem to remember even those years ago when I last used it, it was necessary to give permission for flash to run each time you wanted it.

I can not help with  the errors you are seeing either as I have not had flash on my systems for a few years, and I have certainly not missed it in any way.

---

### Post by CatKiller on 2020-11-05
Support for Flash plugins was removed from all browsers because Flash is dead and EOL.

---

### Post by jgw on 2020-11-07
First, thanks for the replies!

I thought I would try google chrome.  Works like a champ.  I think my main problem with adobe flash is how I have been installing it.  If I do the flash installer it installs shockwave flash (I think)  That is, I think, the problem.  I have two other machines I upgraded with no problem and they are both running adobe flash with no problem.  Its just this machine where its one of the problems I had with my upgrade to 20.04.1  (can no longer quit machine (seems to be hanging on something to do with snap), bootup takes about 15 minutes, etc., etc., etc.)

I think I will go with the chrome thing and giveup on firefox for that one - thanks again for the help!

---

### Post by TheFu on 2020-11-07
Google will be removing flash support in a few months. They announced this 1-2 years ago.

---

