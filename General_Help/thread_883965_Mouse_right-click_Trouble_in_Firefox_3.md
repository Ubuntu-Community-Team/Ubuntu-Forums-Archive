---
title: "Mouse right-click Trouble in Firefox 3"
date: 2008-08-08
forum: General Help
---

### Post by lukjad on 2008-08-08
I was wondering if this happens to anyone else. I have been having this problem with right clicking ever since I came to 8.04 whenever I try to right click in Firefox about half the time something weird happens and it seems to select at random one of the choices from the drop down box and activate it. I try to right click a link and instead Adblock pops up asking how I would like the filter. Or I wish to block an ad and when I right click it it opens the ad in a new tab or window. If I don't move my mouse and just keep right clicking the same thing will happen over and over again. If I move my mouse and scroll the page down, then sometimes I will get a drop down box. Other times something else will happen. Has any of this happened to you?

---

### Post by swisscow on 2008-08-08
Yes, happened to me as well.

My solution probably won't help. Changed to opera, not been a problem since!

---

### Post by lukjad on 2008-08-08
Ha. No, it won't. Thanks for posting and letting me know that I'm not alone.

---

### Post by LowSky on 2008-08-08
open your home folder hit Ctrl+h and find the .firefox folder, delete the contents and restart firefox

---

### Post by lukjad on 2008-08-08
Wouldn't that delete all of my bookmarks?

---

### Post by Sycron on 2008-08-08
You may save your bookmarks...

---

### Post by lukjad on 2008-08-08
> **scragar said:**
> hold down right click instead of pressing it? it never occurs then.

The problem(if I'm correct) is a slight movement to the left(and maybe down) as you click, which causes Firefox to assume your after the first option(since for some reason the selection and right click menu appear/are activated BOTH on mouse down and mouse up, yeah, go figure logic behind that). Holding down the mouse solves this, although it's not a great solution.



Someone mentioned this solution. I thought someone might want to try this as well.

---

### Post by Ozor Mox on 2008-08-26
I have this problem with Firefox and it is quite annoying. It doesn't happen all the time, but it happens often enough to make me consider a different browser. I hope it gets fixed soon.

---

### Post by lukjad on 2008-08-26
I really hope so. It seems to only happen in Ubuntu as far as I can tell. So, if anyone wants to compile their own, could you tell me if the problem is still there?

---

### Post by mercury80 on 2009-03-28
i got the same problem. 1 laptop (8.04, 8.10 and 9.04 beta) & 1 stationary (8.04 and 8.10). the laptop i have reinstalled the OS a couple of times too... i keep upgrading but there is now change...

---

### Post by IanVonSpeedfreak on 2009-03-28
I have been having troubles with this as well, but shrugged it off as a problem with my mouse or how I was using my mouse.  Has anyone filed a bug report for this yet?  It's a real pain and now that I know I'm not the only one with this problem I'd like very much for it to be solved soon, ha.

---

### Post by lukjad on 2009-03-30
> **IanVonSpeedfreak said:**
> I have been having troubles with this as well, but shrugged it off as a problem with my mouse or how I was using my mouse.  Has anyone filed a bug report for this yet?  It's a real pain and now that I know I'm not the only one with this problem I'd like very much for it to be solved soon, ha.

I'm not sure... I should check. If I do find anything, I'll post here.

---

### Post by nuir on 2009-04-27
This is a very annoying bug. I can't remember where, but in some site I found a workaround that I've been using quite effectively, you just need to install a mouse-gesture add-on to firefox, I think any will do. 

You don't even need to actually use the gestures, just having it installed seems to work, at leas the one I use (all-in-one gestures).

Good luck!

---

### Post by omac on 2009-04-29
> **nuir said:**
> This is a very annoying bug. I can't remember where, but in some site I found a workaround that I've been using quite effectively, you just need to install a mouse-gesture add-on to firefox, I think any will do. 

You don't even need to actually use the gestures, just having it installed seems to work, at leas the one I use (all-in-one gestures).

Good luck!

Thanks, I'll try that one out.  I've also been getting the right click problems in firefox, and initially, I thought it was the mouse.

My temporary solution has been to install Firefox 2 from the add/remove programs menu.

---

### Post by omac on 2009-04-29
Thanks, nuir, that seems to be working! :cheers:

---

### Post by MikeTheC on 2009-05-24
I'm seeing the same thing here. It isn't behavior that I normally see in either Mac OS X or Windows. It is darned annoying!

---

### Post by TheExplorer on 2009-05-24
Yup. I can confirm this too. Strange behaviour when right-clicking a link.
Gonna try to install FF from the official site and will tell you the result.
There's an Ubuntu extension installed within FF by default, you can see it in your Add-ons. Can it be buggy?
Btw this never happened to me on previous versions of Ubuntu and appeared on Jaunty.

---

### Post by mercury80 on 2009-05-24
my solution is to hold the right button until the menu pops up, and selecting a an action by releasing the button (but you can click again)... but it is an annoying bug!

---

### Post by lukjad on 2009-05-27
> **mercury80 said:**
> my solution is to hold the right button until the menu pops up, and selecting a an action by releasing the button (but you can click again)... but it is an annoying bug!
I try that, and usually it works. But sometimes even that fails. :(

---

### Post by Ptero-4 on 2009-05-29
I have it too. Thing I noticed.
1) Doesn't happen under windows/bsd/osx/linux distros running xfree86/xorg 6.8.0
2) Happens in all modern linux distros (xorg +7.0.x) with either distro packaged or vanilla firefox
3) doesn't happen if compiz is disabled or not installed

---

### Post by TheExplorer on 2009-05-29
> **Ptero-4 said:**
> doesn't happen if compiz is disabled or not installed

Nope. I do not use Compiz at all. It is completely cleaned out from the system including configs and all its traces. Still, there is a problem with right-clicking. Seems to be a bug with Xorg. Well, Mouse Gestures extension solves this problem for me. It has to be enabled, but you may remove all the gestures to avoid their actions.

P.S. As I recently trace a lot of complaints/bugs etc. it came to my mind that something is wrong with Xorg actually. Well, it IS INDEED faulty, for e.g. there is tearing in OpenGL apps with ANY Nvidia driver (either beta or the latest final one). In Windoze it's perfect and smooth when playing OpenArena for example. But in Linux I'm having tearing and there is NO fix for that (neither tweaking with xorg.conf, nor with nvidia-settings).

Well, it's just my IMHO as for now.

---

### Post by mwillams73 on 2009-05-30
this on is simple , get the mouse gesture add on for mozilla in ff 3 it fixes this problem, i did it and it worked and ive suggested it to many others abd it worked for them too, I hope this helps!!

---

### Post by TheExplorer on 2009-05-30
Well, that's what I'm talking actually :) Learn to read, people.

---

### Post by Seaniesean on 2009-06-02
Yes yes yes I am so glad I found this thread!  I thought I was the only one!  I thought I had some mouse gestures crud installed, "firefox and ubuntu don't come with mouse gestures" was the reply I got thank god thank god other people have this problem!!!!!!!!!!!!!!!!!!!!!!!!!  This has been literally driving me feather-eating insane and given me exclamationmarkitis as you can see!!!!!!!!!!!!!!!!!

"Mail with evolution"-uh, no, I want to open a new window?! Grr!

"Bookmark page" NOOOOOO!  I WANT TO OPEN A NEW TAB! GRRRRRRRRRRRRRRR!

And the solution is to, er, install a mouse gesture add-on, you say?

Hmmmmmmmmmmm.  Can you do that without having any mouse gestures functioning/enabled and it will still fix it?  I DETEST mouse gestures!  

-Edit, I see that I can, hoorah!

I haven't even read this thread properly I am so pleased!

---

### Post by someguyonvbvntv on 2009-06-17
hey um...when i updated to ubuntu 9.04 my mouse will bug up and wont right click sometimes it wont even left click please help :(

---

