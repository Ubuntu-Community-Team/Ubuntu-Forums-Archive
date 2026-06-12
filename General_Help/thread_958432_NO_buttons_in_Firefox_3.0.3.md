---
title: "NO buttons in Firefox 3.0.3"
date: 2008-10-25
forum: General Help
---

### Post by Reinbag on 2008-10-25
Dear helpful Ubuntu-ers,
I recently updated my firefox browser and now there are no buttons on the toolbar. This includes the back/forward button, reload, stop. I also have no history and my home page won´t come up. I´ve been using the about:config window to try and figure out what´s wrong, but I´ve had no luck. I also have been having trouble trying to find other posts about this. Just recently got the internet working again on my machine. I´m very happy about that, but now I´ve got this to deal with. BTW, I´m running Hardy.

Thanks y´all

---

### Post by Yellow Pasque on 2008-10-25
Can you add the buttons by right-clicking on the toolbar and choosing "Customize.."?

---

### Post by Dr Small on 2008-10-25
Geesh. That sounds like what my browser looks like :p

---

### Post by mgmiller on 2008-10-25
Right click the blank area to the right of the FiIe Edit View History Bookmarks, Tools, Help.  (just to the right of the Help drop down).

Put a check mark in "Navigation toolbar".  The buttons should all return.

---

### Post by Reinbag on 2008-10-25
Well, I tried both the customize toolbar option and checking the navigation bar. The buttons themselves are there, but they are gray and unresponsive.
Still no luck. Very strange.

Also, none of the right click commands for navigation work either. And the current web address never shows up in the bar (it stays blank or keeps whatever address you last typed into the field.)

Finally, I now realize that none of the menu items work either. Like no menu drops down when I click on them. I´ve tried reinstalling firefox, but that hasn´t made any difference either.

---

### Post by BGrigg on 2008-10-25
Are you running Compiz?

If so, try this experiment. Type Alt-F2 to bring up the Run Application box and enter "metacity --replace" within the run box. Then open Firefox. If the taskbar buttons show back up, Compiz is the culprit. Typing "compiz --replace" gets you back to your start point.

Run Application remembers your commands so I just switch back and forth as my needs dictate.

---

### Post by Perdignus on 2008-10-25
Hi,

I have one of the same issues.  None of my drop down menus in Firefox  like File, Edit, View, etc... work with the mouse.  I can get to them with the ALT-f, ALT-e, etc..., but not with the mouse.  Other things aren't working with the mouse either, like the main menu button in Xfce4.

Other weird behavior started at the same time as the pull-down menu problem, such as when I single left click on a word in Firefox, or in a terminal, the entire word is automatically selected.  I can't select just a single letter or parts of a word.

Hopefully someone can help with this issue, it's starting to become cumbersome to move around.  I'm not using Compiz, have tried both nVidia drivers 177.80 and 177.78, have tried different kernel versions and different mice all without any luck.

Thanks much,
Perdignus.

---

### Post by Perdignus on 2008-10-26
Hello again,

I was able to resolve the problem by editing my xorg.conf file.  The mouse section was rewritten when I created a new xorg.conf file with "xorg -configure".

The problem is detailed here:
[http://ubuntuforums.org/showthread.php?t=783467](http://ubuntuforums.org/showthread.php?t=783467)

Hope this helps you too.

Cheers,
Perdignus.

---

### Post by Reinbag on 2008-10-26
PROBLEM SOLVED!

Wupeee! I´m such a n00b it´s ridiculous. Basically, it was a matter of admin privileges. I guess when I updated the browser, it no longer recognized me, and treated me as a guest. Thus, no buttons. All I had to do was launch firefox from the terminal. Thanks for the help though. sorry, it was something so obvious.

---

### Post by mgmiller on 2008-10-27
Please mark this thread as solved by clicking on the "Thread Tools" at the top of the page.

---

