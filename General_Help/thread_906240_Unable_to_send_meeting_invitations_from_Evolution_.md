---
title: "Unable to send meeting invitations from Evolution to Outlook"
date: 2008-08-31
forum: General Help
---

### Post by amppat on 2008-08-31
Iam trying to take  Evolution 2.22.3.1 into use as email client in corporate environment. I can receive meeting invitations, from Outlook users, but Outlook users see my invitations as plain text messages, instead of proper calendar invitations. I tested with Thunderbird + Lightining and it seemed to work. Outlook showed a .ics attachment that could be moved to calendar.
I tried to search around, but did not find much information, I guess for most users sending invitation from Evolution to Outlook works? Any Ideas what could be wrong ? 

Message that outlook displays:

```

Return-Path: 
...
Content-Type: text/calendar; name=calendar.ics; charset=utf-8; METHOD=REQUEST
Date: Sun, 31 Aug 2008 13:55:13 +0300
Message-Id: <1220180113.5933.0.camel@ubuntu-laptop>
Mime-Version: 1.0
X-Mailer: Evolution 2.22.3.1
....
BEGIN:VCALENDAR
CALSCALE:GREGORIAN
PRODID:-//Ximian//NONSGML Evolution Calendar//EN VERSION:2.0 METHOD:REQUEST BEGIN:VTIMEZONE TZID:/softwarestudio.org/Tzfile/Europe/Helsinki
...



```

---

### Post by amppat on 2008-09-01
To clartify Iam not connecting to Exchange. Can anyone confirm that it is possible to send meeting invitation from Evolution to Outlook ? 
If so which version of evolution and Outlook are used ?

---

### Post by cfrye2000 on 2008-12-02
Hi, I am having the same issue.  Did you ever find a resolution?

---

### Post by amppat on 2008-12-04
New evolution 2.24 with 8.10 release seems to have corrected this problem

---

### Post by Grolsche on 2008-12-04
Just to make sure its not somethign as simple as this but, when you send the email using Evolution did you change the option from plain to html?

---

