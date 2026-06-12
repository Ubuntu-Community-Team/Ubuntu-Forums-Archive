---
title: "[SOLVED] very strange pidgin yahoo buddy list issue"
date: 2008-10-06
forum: General Help
---

### Post by hvymtlsteve on 2008-10-06
Hi guys,
I have a strange issue with Pidgin and my Yahoo (Japan) buddy list. It seems that I can only see that buddies are online whenever Pidgin tries to sync the buddy list with the server (i.e. when some change has been made to the buddy list last time I was online).

Here's how I noticed this:
Recently (ever since ability to login to yahoo Japan was restored in new versions of Pidgin after some small protocol change they made)  I haven't been able to see when my buddies from that protocol are online *except* the ones that have been added while I was using Pidgin. This is true for both of my computers.
The buddies are all on the list as they should be, they just don't show up as "online."

Curiously,  on one of my machines I changed the locale to Japanese, and next time I fired up pidgin, I was able to see some of my buddies online. However, the next time I opened Pidgin after that, the group once again showed no online buddies (even though a friend actually was online at the time). I decided to try this with my other machine, and the exact same thing happened.. I was magically able to see which buddies were online just one time.

After poking around a bit, I discovered this: 
As an example, if I try to rename the &#20210;&#38291; group to "y-j-buddies" and close Pidgin, then re-run it, the group y-j-buddies will still exist, but is completely empty, and the &#20210;&#38291;&#12288;group is recreated with all the buddies, and those who are online show up as online.
The same happens if I try moving a buddy from that group to another group. The next time I run pidgin, the buddy will be moved back to where it was, and I can see people online just fine.

Anybody else experience this?


EDIT--- Update-- I don't know what led me to try this, but I was able to fix the issue by logging into Yahoo J's own web messenger, and moving all buddies to a group with only English letters in the name...
That's good enough for me for now.. maybe I will file a bug report with Pidgin though :)

---

