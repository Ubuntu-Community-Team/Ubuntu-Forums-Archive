---
title: "Express Install is not supported on this operating system."
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by hellonishad on 2009-08-19
Dear Friends,

I am using flash player for our FLEX3 application and it was working fine before. Recently I upgrade the flash player to version 10,0,32,18 and our flex application is not working now, but youtube is working quite fine. When I am loading the FLEX3 application the flash player showing me this message.
------------------------------------------
** Express Install is not supported on this operating system. _To upgrade please visit Flash Player Download Center._**
------------------------------------------

I searched quite a lot in google, but didn't get a satisfied answer. Any kind of help will be appreciated.

Thank you for your help.
Best Regards,
Nishad Nanethan Aliyar

---

### Post by jdaniells on 2009-08-24
I had the same problem, and though my operating System is Fedora, I tell you what I've done to solve it because probably the problem is the same or related.

My problem was that I had 2 versions or flash plugin installed on the firefox. One was 10,0,32,18, but the other one was 9.0.105. 

The javascript code to detect the flash version, searched for navigator.plugins["Shockwave Flash"]. Both installed versions matched the query, but the 9.0.105 was retrived and the detection failed.

What I did was to found all the libflashplayer.so I had on filesystem (locate libflashplayer.so), and removed all except the one I was sure was version 10,0,32,18.

You can also modify the javascript code for version detection, to search for all matching plugins, except the first one found.


I expect this helps you in resolve your problem.

---

### Post by hellonishad on 2009-08-29
Thanks for your reply [jdaniells]("http://ubuntuforums.org/member.php?u=899228").

This commands fixed my problem in Ubuntu.

------------------------------
rm -rf /usr/lib/flashplugin*

------------------------------

Please let me know if you have any problem.

---

### Post by hellonishad on 2010-07-26
Hello,

Even if you install new version of flash player firefox load previously installed libflashplayer.so file until you remove it manually from your plugins directory.

You can remove it by using following commands.
----------------------------------
cd ~
rm .mozilla/plugins/libflashplayer.so
----------------------------------

Regards,
Nishad Nanethan Aliyar

---

