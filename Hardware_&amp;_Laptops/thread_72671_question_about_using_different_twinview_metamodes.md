---
title: "question about using different twinview metamodes"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by oldmanstan on 2005-10-07
I have a geforce 4400 128mb card that i recently set up using 2 lcd panels, a 19inch ( 1280x1024 ) and a 15inch ( 1024x768 ).  Before I was just using the 19inch.  I followed the directions on nvidia's web site to set up the x server to use twin view and it works just fine for the most part.  However, i noticed that 3d stuff wasn't running as fast (which is to be expected since the card is having to handle a lot more pixels).  Also, games running fullscreen would use the two monitors as one screen and therefore become unplayable (though they would generally run ok as far as framerate and whatnot).  Thinking I could solve the problem by setting up a separate metamode that NULL'd out the smaller display I did just that:

Option		"MetaModes" "1280x1024, 1024x768; 1280x1024, NULL"

However, it hasn't seemed to work, the framerates on anything 3d or gl (screensavers, etc.) are still much lower than they used to be with one display (even using the new metamode, small display disabled) and fullscreen 3d apps won't load, they just hang at a black screen.  I was wondering if there was something else I could do to solve this problem, essentially what I want to do is turn off the smaller monitor entirely in software so that I can use both when I'm working on things on the desktop and just use the 19 when im playing games, etc.

To be honest I seldom play games but I have a need to make my computer always "work".:) 

Any help anyone could lend would be appreciated.
-oldmanstan

p.s. here is my xorg.conf file contents

[http://www.meknow.net/xorg.txt](http://www.meknow.net/xorg.txt)

---

