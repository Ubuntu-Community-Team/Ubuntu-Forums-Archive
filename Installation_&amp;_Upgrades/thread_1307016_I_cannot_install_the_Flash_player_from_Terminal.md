---
title: "I cannot install the Flash player from Terminal"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by mrbinitie on 2009-10-30
I have been unable to install the flash player 10 debugger from terminal. I keep getting this error

[: 258: closing paren expected

ERROR: Your glibc library is older than 2.3.
       Please update your glibc library.

I need to install the Flash debug player to work -Can any one tell me how to deal with this problem

---

### Post by wvxvw on 2010-05-06
I think you would figure this out by now. Posting this for the future reference:
It appears to be an error in installer script, for more details see here: [http://bugs.adobe.com/jira/browse/FP-4478](http://bugs.adobe.com/jira/browse/FP-4478)
As a workaround you can copy the .so file to the install folder. If you need to figure out what's the install folder, install the player through web installer (FireFox will offer to install the player if you navigate to a page containing SWF).

---

