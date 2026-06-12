---
title: "[SOLVED] How to make application open in an assigned desktop?"
date: 2008-11-01
forum: General Help
---

### Post by rjs987 on 2008-11-01
I have vmware server installed on my Kubuntu 7.10 system.
I have searched for this all morning and can't find anything on it in the forum other than within compiz. I don't have compiz and I know it is possible without it. I know I found it before since I did set my vmware to start in desktop 4 many months ago, but now I want to change that and can't remember where it was I set it to begin with. I am thinking there was a file to change a setting in.

Anyone?

Many thanks in advance.

---

### Post by rjs987 on 2008-11-02
Bump...

I was sure I got the information about what file or option to change to do this on these forums but just can't find it now. Maybe it's a setting in a vmware config file or in a kde config file but I haven't found it yet.

---

### Post by editrix on 2008-11-03
I don't recall 100% how it's done, but essentially you open the window on the desktop you want, then click the icon on the top left and choose Configure window behaviour.

You'll get a window which asks you to give a name to the configuration. Use something like **vmware on desktop 3**.

There's a button at the bottom of the window you're looking at that says Detect. Click that.

Then, go to Geometry and where it says Desktop, click that.

---

### Post by rjs987 on 2008-11-05
Thanks editrix.
It wasn't exactly as you said but I was able to get there. vmware server that I have doesn't have the icon you mention, in the upper left corner or anywhere else. But I decided to look at the one in this Firefox window and found the "Window-Specific Settings" for all applications that have any special settings assigned. There was both a "Window settings for vmware" and a "Application settings for vmware" that I had to make the change in. When I click on Modify, the Geometry tab is found. I think there used to be such an icon in my vmware window but in my messing around with it to clean up the display and make it uncluttered and simple as possible I may have removed that permanently.

After looking some more I found the option in the System Settings. In the Look & Feel section there is Window Behavior option. That is where I think I may have originally made the settings I want to change. I don't know why I missed that.

Thanks again!

---

