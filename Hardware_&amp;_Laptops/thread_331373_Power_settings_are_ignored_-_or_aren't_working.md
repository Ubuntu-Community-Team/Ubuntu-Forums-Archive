---
title: "Power settings are ignored - or aren't working"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by phowardcom on 2007-01-04
I have Edgy running on a Dell Inspiron 8200 laptop and for the most part everything works fine.

The problem I have is with the power settings. I have set it so that when I close the lid it should "do nothing" but whenever the lid is shut it logs me off and takes me back to the login screen.

Once there it will let me log on but to a blank desktop with no icons or menus.  Hitting Ctrl F1 gives me a blank screen with no logon details and hitting CTRL BAckspace logs me out again but when I log back in I get the same problem.

The only way to fix the problem is to do a hard reset.

Is this a common problem or do I have some freaky hardware that Edgy doesn't like? I can't remember what Dapper did when I closed the lid as it was only on this laptop for a few days before I installed Edgy in its place.

---

### Post by jgubes on 2007-01-04
Found a bug for this, but I don't remember where.  They basically said that it was a known problem that x crashes when you close the lid.  They're working on an official update to fix it, but until then they posted a package that you can install yourself.  It's too big for me to attach to this post.  If you want, I can email it to you...or you can search this list for "x crash lid close bug" or something like that.

After you install it, ubuntu will want to overwrite it with the official version every time you update.  If you update using adept you can tell it not to update that package.

---

### Post by jgubes on 2007-01-05
Here's the link to the bug report:
[https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/61746](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/61746)

Here's the package that has the fix:
[http://librarian.launchpad.net/5065022/xserver-xorg-core_1.1.1-0ubuntu12_i386.deb](http://librarian.launchpad.net/5065022/xserver-xorg-core_1.1.1-0ubuntu12_i386.deb)

---

### Post by RippyMan on 2007-01-05
I'm having this same problem. X crashes when I close the screen of the laptop. It happens on two laptops, a Dell Latitude CSx and a Dell Inspiron 4000. I tried the fix jgubes posted and it did work. However, Ubuntu saying that I need to update X after I install this patch is very bothersome. It's fine for me, but the 4000 is going to be used by my mom and this will serve to further confuse her. I don't want her to write off Linux just because of that. Therefore, both of these computers will remain with Dapper until this is fixed officially. Dapper doesn't have this problem in the slightest, at least on the CSx. Otherwise I do prefer Edgy over Dapper. Also, it is interesting to note that it doesn't happen on all Dells. My Inspiron 1100 had Edgy and it would do just fine when the lid was closed. I hope this will be completely fixed soon, as I would prefer to completely migrate to Edgy.

---

### Post by klato on 2007-01-24
I just noticed yesterday that this happens on my Dell Inspiron 4150...are they going to make this an automatic update or do all Dell laptop owners just have to randomly stumble upon this forum post?

---

### Post by jyotishman on 2007-02-13
> **jgubes said:**
> Here's the link to the bug report:
[https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/61746](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/61746)

Here's the package that has the fix:
[http://librarian.launchpad.net/5065022/xserver-xorg-core_1.1.1-0ubuntu12_i386.deb](http://librarian.launchpad.net/5065022/xserver-xorg-core_1.1.1-0ubuntu12_i386.deb)

Hi -- I tried your suggestion including the one listed in [https://launchpad.net/ubuntu/+source/xorg-server/+bug/61746](https://launchpad.net/ubuntu/+source/xorg-server/+bug/61746) (i.e, installed [http://librarian.launchpad.net/6385251/xserver-xorg-core_1.1.1-0ubuntu12.1%2Bacpifix_i386.deb](http://librarian.launchpad.net/6385251/xserver-xorg-core_1.1.1-0ubuntu12.1%2Bacpifix_i386.deb))  . 

Still I am having the same problem...once the lid of my Inspiron E1405 is closed, I have to resort to hard reboot. Am I doing something wrong or is there an alternative work around? Thanks.

---

### Post by jgubes on 2007-02-19
I just installed the new "...acpifix..." package.  It works great.  I no longer have to ignore the request to update xserver.

jyotishman - what you're describing is a little different from what others have experienced in this thread.  Is your xserver crashing and sending you back to the login screen, or is your screen just not coming back on.  Even after installing these updates, my screen doesn't come back on when I open the lid.  I have to push Fn+F8 (CRT/LCD) to wake up the display.

If this doesn't work for you, try to describe your symptoms in more detail so we can help you troubleshoot this.

---

### Post by jgubes on 2007-04-06
It seems that X-server 12.2 just came out.  This overrides 12.1+acpifix, so we have to start ignoring the requests to update again.  Is it not a priority to get the acpifix into the production build?

---

