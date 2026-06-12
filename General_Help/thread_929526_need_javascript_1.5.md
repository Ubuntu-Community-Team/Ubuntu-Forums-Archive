---
title: "need javascript 1.5?"
date: 2008-09-25
forum: General Help
---

### Post by hobkirk13 on 2008-09-25
I'm having a problem with javascript 1.5. i'm taking an online class and the page needs 1.5 to run. up until i installed the latest package updates i had no problem viewing the website and using all of the functions but now i can't do anything with it. any help would be great thanks!

---

### Post by jespdj on 2008-09-25
Are you talking about Java**Script** or Java? These are two entirely different things!

---

### Post by hobkirk13 on 2008-09-25
the website is saying javascript 1.5

---

### Post by baju on 2008-09-25
This sounds a bit strange to me,because most pages don't check for a certain Javascript-version. Maybe the Error-Message is wrong.
Can you post a link to the page?

---

### Post by hobkirk13 on 2008-09-25
[http://tychousa11.umuc.edu/WebTycho.nsf/FailJSCheck?OpenPage](http://tychousa11.umuc.edu/WebTycho.nsf/FailJSCheck?OpenPage)
is the link to the popup and it says-
This browser is not configured with JavaScript 1.5 which is required for using WebTycho. Before you may enter class, you must download and install JavaScript 1.5.  JavaScript 1.5 is needed to be able to see course materials, announcements, and conference notes that have been written with the Text Formatting Editor (TFE).  Even if you choose to not compose with the TFE yourself, you must be able to see what others have posted.

This reminder will appear each time you log in to WebTycho with any browser that does not have JavaScript 1.5 installed.

I'm just thinking that maybe if I completely uninstall firefox and then reinstall it maybe this will help, but i'm completely computer stupid so if anyone could help me with what i need to type into terminal to do this, that would be great! thanks!

---

### Post by hankenstein on 2008-09-25
Try opening your browser window and typing "about:config" to bring up your firefox configuration.

In the search bar look up "general.useragent.vendor"  If the value says "Ubuntu", delete it and leave it blank.  Then restart your browser.  It should fix the problem.  

Somehow there is a glitch in webtycho that doesn't detect the right javascript in Ubuntu.

---

