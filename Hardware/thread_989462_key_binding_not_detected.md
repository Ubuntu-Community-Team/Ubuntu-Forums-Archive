---
title: "key binding not detected"
date: 2008-11-21
forum: Hardware
---

### Post by nipenk on 2008-11-21
Hello everyone,
Currently im using HP tx2510 and running Ubuntu 8.10.
Based on tutorial at 
[http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm) (about the rotating the screen), i can binding the key to the DVD and quickplay button which is the XF86Launch0 and XF86Launch1. but while i pressed it, it wont give any changes.

After do some search at the forum i found this post
[http://ubuntuforums.org/showthread.php?t=938698](http://ubuntuforums.org/showthread.php?t=938698), in my case after i do 'xev' command, the console did not even show the XF86Launch0 and XF86Launch1 button event when i pressed it.

can someone help why it is not working or detected and how to fixed it?

Thank you.

Regards,
Niven.

---

### Post by Favux on 2008-12-10
Hi nipenk,

I think the problem you are having is that with 8.10 HAL (hardware abstracton layer) was introduced.  There is a known bug in HAL which breaks single key key binding.

Please see my rotation HOW TO at:

   [http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

which contains info. on key binding and an addendum on activating your keys.

Hope this helps.

---

