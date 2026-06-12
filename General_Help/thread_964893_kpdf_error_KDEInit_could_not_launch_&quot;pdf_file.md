---
title: "kpdf error KDEInit could not launch &quot;pdf file&quot;"
date: 2008-10-31
forum: General Help
---

### Post by Ertxiem on 2008-10-31
This is my first post. Sorry for anything wrong I might be doing.

When I tried to use kpdf to open pdf files in kde konqueror I got the error message error KDEInit could not launch "pdf file".

I'm using Kubuntu 8.04, with kde 3.5.9 and kpdf 0.5.9.

This is a problem that is solved using a solution available (since 2006) in:
[http://ubuntuforums.org/showthread.php?t=223192](http://ubuntuforums.org/showthread.php?t=223192)
but the problem was posted again in 2007 and 2008 in a (now) closed thread:
[http://ubuntuforums.org/showthread.php?t=631103](http://ubuntuforums.org/showthread.php?t=631103)
where a solution does not appear.

Since it has happened to me this week, I thought it might be interesting to post this information again (because I cannot reply in the last thread, as I think it would be best).

When I was using Evince Document Viewer 2.22.2 to open pdf files I had no problem. My problems started when (this week) I right clicked a pdf file and choose
Open With > Other... > kpdf.
After this, when I left clicked a pdf file I got the following error:
KDEInit could not launch "pdf file"

The solution to this, from [Jucato](http://ubuntuforums.org/member.php?u=65488) in the thread from 2006 is:
1 - Open konqueror;
2 - Go to the menu: **settings** > **configure konqueror**...;
3 - Choose **file associations** > **Find filename pattern**: write **pdf** in the box;
4 - Click **+application** > **pdf**;
5 - In the box application preference order appeared to me 2 times "kpdf". Click the **second** one and choose **Edit...**;
6 - There should appear the kpdf icon and in location the address should be something like: /usr/share/applications/kde. This means this is working link to the kpdf. Click **cancel** to leave it like this;
7 - Now click the **first kpdf** and choose **Edit...**;
8 - There should be a green question mark instead of the correct icon and the location is something like /home/"user"/ (etc.). This is the wrong link. Click **cancel** to go back to the previous window;
9 - Choose the **first kpdf** and click **Remove**;
10 - Move up to the first place the working **kpdf**.
After this, when I left clicked a pdf file it would open correctly with kpdf.
It worked for me.

I suspect that the problem appeared because either I did something wrong when assigning the kpdf to the pdf files or there is some bug in konqueror. Perhaps *there can be only one* kpdf link and the second to appear is erroneously created. Can anyone explain to me why this happened? I'm curious.

---

