---
title: "Compiz Grid plugin not working in 9.04"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by mexp on 2009-05-04
Just upgraded to Jaunty, and all good - except that my favorite compiz plugin Grid is not working any more - the plugin is listed on CCSM, but it won't stay active.

I could not find instructions to make this plugin work on 9.04, and the previous instructions from this site [http://forum.compiz-fusion.org/showthread.php?t=8821&page=2](http://forum.compiz-fusion.org/showthread.php?t=8821&page=2) didn't work.

How to get the Grid functionality back????

---

### Post by peterka.jiri on 2009-05-20
Hi Mexp,

just remove ~/.compiz folder, re-login and everything should be just fine.

Bye

---

### Post by mexp on 2009-05-20
Thanks, worked :)

---

### Post by srf21c on 2011-02-23
This bug still exists in clean installs of Maverick 10.10.  

I had been pulling my hair out trying to figure out why the grid plugin was not working until I found this post.  THANK YOU.

---

### Post by trybik on 2011-03-10
> **peterka.jiri said:**
> 
just remove ~/.compiz folder, re-login and everything should be just fine.


Did not work for me. On not clean 10.10 install I've removed all compiz config folders and restarted gdm. Any ideas?

Miko&#322;aj

---

### Post by FLeiXiuS on 2011-04-13
sudo apt-get install compiz-fusion-plugins-extra

For the grid plugin

---

### Post by Andrew_P on 2011-07-07
> **trybik said:**
> Did not work for me. On not clean 10.10 install I've removed all compiz config folders and restarted gdm. Any ideas?

Miko&#322;aj

Are you sure that the Grid plugin is active?  Go to System > Preferences > CompizConfig, navigate to the Window Management view and make sure the Grid icon's checkbox is checked.

---

