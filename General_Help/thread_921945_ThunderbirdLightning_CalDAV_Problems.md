---
title: "Thunderbird/Lightning CalDAV Problems"
date: 2008-09-16
forum: General Help
---

### Post by lipinski on 2008-09-16
After much work, I have a partially working Thunderbird/Lightning integration with CalDAV hosted by the DCS Calendar Server.  

I'm still having some problems that I was wondering if anyone could help with.

I can subscriber to calendars on my local CalDAV (DCS Calendar Server) through Lightning and events & tasks are listed, I can create them, modify them, etc.

The problems that I'm still having however are:
- Upon starting Thunderbird/Lightning, it will not automatically retrieve my CalDAV calendar events or tasks.  I have to click on Reload before the events & tasks will be displayed. 
- On the main "Mail" page, the Task list is not populated at all.  The only way to get it populated is to go to the Task view and then click Reload again.  (Or create a new task on a CalDAV calendar subscription, which will also refresh the Task view).
- My most serious problem, however, is that even though I have stored my login/password in the Password Manager, I get prompted for login/password every time Lightning does an auto refresh (default 30 min).  I get a login/password prompt for each Calendar I am subscribed to.  So, essentially with 4 calendars, I get 4 login/password prompts every 30 min.  If I leave Lightning up overnight, I have upwards of 64 prompts to respond to (4-calendars * 2-per_hour * 8-hours).  This annoyance has me almost ready to ditch Thunderbird and Lightning altogether in favor of Evolution - which I'd rather not do because of all the complaints about Evolution on these boards and the amount of time I have spend to get DCS completely integrated into Ubuntu.

Once I get past these issues, I will have a complete end-to-end network shared calendar solution.  It took me many hours of work to find all the workarounds, and I'll be happy to post them, but I don't know if I should until I figure out what is causing me this last set of major headaches.

FYI - I'm running Ubuntu 8.04 with Thunderbird 2.0.0.16 & Lightning 0.8 (I upgraded from Lightning 0.7 to see if that would correct this problem)

---

### Post by gnimsh on 2008-12-07
Well I can't really solve the problems you're currently having, but I can offer an alternative.  I have set up the same thing but using Gcal and caldav, and it works perfectly.  

To do this simply go to gmail, click the calendar link on the top left, and then once that loads there will be a link on the top right about integrating it with lightning.  They provide all the steps you need to get if functioning properly.  Just make sure to set the lightning timezone properly or the times between your system and gcalendar won't sync correctly.

---

