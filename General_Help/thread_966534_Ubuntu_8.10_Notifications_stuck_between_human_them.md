---
title: "Ubuntu 8.10 Notifications stuck between human theme and darkroom theme."
date: 2008-11-01
forum: General Help
---

### Post by YonyonJohn on 2008-11-01
Hi, everyone. I'm having a small issue with notifications in 8.10. when the notification shows up, part of it seems to be using the human theme, while the rest is using dark room. It's kind of hard to explain so I attached a screen shot. I was wondering if anyone else was having this problem and if there is a solution. thanks in advance for any help :) (the screenshot is of a banshee notification but the same thing happens with any other notification.)

---

### Post by kurtpete on 2008-11-06
You can change the theme using the configuration editor (gconf-editor).  Under the branch /apps/notification-daemon there is a name/value pair named theme.  It's probably currently 'ubuntu' for you.  You can change this to darkroom.  Unfortunately, you'll probably not want to do this once you see how hard the darkroom notification items are to read...  :(

---

