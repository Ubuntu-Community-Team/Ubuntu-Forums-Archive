---
title: "Flash 10 solved Youtube crashes, but..."
date: 2008-08-08
forum: General Help
---

### Post by iamah on 2008-08-08
...now it crashes at flash ads :confused: 

Youtube videos now have some white dots here and there, but at least there's no crashing... however, I'm crashing now at other sites: mininova and myspace, just to cite some...

I wonder if installing other browser could solve this? Opera, maybe?

EDIT: i used [this](http://kemal.bioeng-network.org/2008/06/08/how-to-get-rid-of-annoying-firefox-crashes-in-ubuntu-hardy-flashplugin-nonfree/) to get Youtube working

---

### Post by gobbles414 on 2008-08-08
I encountered very similar problems with Flash 10. I tried downgrading to Flash 9, but still experienced crashes. The solution that worked for me was to turn off all visual effects in *System => Preferences => Appearance => Visual Effects*.

Let me know if this works for you.

---

### Post by tuxxy on 2008-08-08
I use flash 9 fine, maybe the web adds ahv e something to do with your java web plugin?

---

### Post by igotnoluck on 2008-08-08
I'm using flash 9 and in youtube I ave some crashes now and then.
but if you want to fix the crashes maye try to install (for firefox) an adblocker (like [adblock]("https://addons.mozilla.org/en-US/firefox/addon/1865")) plus a flash blocker which prevents flash from playing automatically (like [flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433") ).

It works for me :)

---

### Post by iamah on 2008-08-08
> **gobbles414 said:**
> I encountered very similar problems with Flash 10. I tried downgrading to Flash 9, but still experienced crashes. The solution that worked for me was to turn off all visual effects in *System => Preferences => Appearance => Visual Effects*.

Let me know if this works for you.

I had it disabled already. I'll try to disable composite in xorg.conf later. 

here are some locations that made me crash using the flash 10 howto linked in the first post:
[http://www.mininova.org/user/axxo](http://www.mininova.org/user/axxo)
[http://profile.myspace.com/index.cfm?fuseaction=user.viewprofile&friendID=374286707](http://profile.myspace.com/index.cfm?fuseaction=user.viewprofile&friendID=374286707)

---

### Post by timcredible on 2008-08-08
yeah, flash 10 is no better than flash 9 - buggy.  makes me wonder if the problem is flash or firefox, because firefox 3 is buggy also (stuff that's not flash used to work fine in firefox 2, but doesn't work in firefox 3).  flash 10 did indeed make youtube not crash, but it put weird white noise at the top and bottom of most videos, and it won't work at playlist.com and other sites.  hopefully the final version of flash 10 will be good, and if firefox fixes their issues, maybe all will be good soon.

---

### Post by gobbles414 on 2008-08-08
> **timcredible said:**
> yeah, flash 10 is no better than flash 9 - buggy.  makes me wonder if the problem is flash or firefox, because firefox 3 is buggy also (stuff that's not flash used to work fine in firefox 2, but doesn't work in firefox 3).  flash 10 did indeed make youtube not crash, but it put weird white noise at the top and bottom of most videos, and it won't work at playlist.com and other sites.  hopefully the final version of flash 10 will be good, and if firefox fixes their issues, maybe all will be good soon. I should have mentioned this in my original reply... In addition to downgrading to Flash 9, I also tried downgrading to Firefox 2. Neither of those downgrades solved my Flash crashing issues. But with the solution that I suggested previously, Flash 10 is now stable in Firefox 3. I'm sorry that it seems my idea only works on some PCs.

---

