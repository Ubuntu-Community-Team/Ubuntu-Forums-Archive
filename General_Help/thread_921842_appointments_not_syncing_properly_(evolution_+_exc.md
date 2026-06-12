---
title: "appointments not syncing properly (evolution + exchange + iphone)"
date: 2008-09-16
forum: General Help
---

### Post by dlstyley on 2008-09-16
I currently use Evolution to get email from our Exchange server.  That is working _ok_, but has it's own flakiness issues.  

The issue is that if I create an appointment in Evolution, in syncs properly with Exchange and I can see it in clients like OWA or outlook, but it never makes it to my iPhone.  However if I create an appointment directly in OWA or Outlook, I do see the appointment on my iPhone.  I can't figure out what's different between the two.

One interesting point is that if someone sends me a meeting request, I do see that in the iPhone.  It seems to just affect appointments I create for myself (not invitations to other meetings).  

Any ideas?

ubuntu 8.04
evolution 2.22.3.1-0ubuntu1
evolution-exchange 2.22.3-0ubuntu2
exchange server 2003
iphone 2.1

---

### Post by McNumara on 2008-09-29
I am in the same boat as you (Evolution + Exchange + iPhone),

Outlook > Exchange > iPhone > Working
iPhone > Exchange > Working
OWA > Exchange > iPhone > Working
Evolution > Exchange > iPhone > _NOT WORKING_

I have made a calendar appointment with outlook (That IS syncing with Outlook/Exchange/Evolution/OWA/iPhone), and Copy/Pasted it with Evolution.  It syncs fine with Outlook/Exchange/OWA, but not with the iPhone.

I wonder if it could be the way that 'exchange-connector-setup-2.22' connects to OWA.
I searched for a MAPI-connector for Evolution, but came up short.

---

### Post by amontero on 2008-11-02
I have the same issue.  It seems that nothing I do on the evolution side syncs with exchange.  If I send an email from evolution, the mail goes out, but it goes into the "Sent" folder on "On this Computer", not in my exchange email account.

When I create an appointment on evolution, it appears in evolution, but it won't sync down to my motorola q.

Also, it appears that if I create an appointment on my motorola q, it shows up in exchange, but evolution will only pick it up if I close and come back in.

Does anyone have any ideas on how to tighten up the syncing between evolution and exchange?

-- Anthony

---

### Post by dlstyley on 2008-11-03
> **amontero said:**
> If I send an email from evolution, the mail goes out, but it goes into the "Sent" folder on "On this Computer", not in my exchange email account.
-- Anthony

I know that this issue can be fixed by changing the configuration for the "Sent Items" folder.  

"Edit-> Preferences" Under "Mail Accounts", select the account hooked up to the Exchange Server and click "Edit".  On the "Defaults" tab, select "Sent Message Folder" and choose the folder you want it to use for "Sent Items".

I have no idea how to fix the issue with calendars not syncing with iPhone.  Frustrating...

---

### Post by c_eric_ray on 2008-12-01
I have a Window Mobil Device and I'm seeing the same problems. Everything syncs great unless I create the appointment/meeting in Evolution. Then it never makes it to my mobile device. 

This is a potential killer for me that may force me back to Windows. I rely too much on my mobile device for scheduling.

Is this a defect or a configuration issue? I'm on Ubuntu 8.10 with all the latests updates.

---

### Post by n8wood on 2008-12-02
The workaround I'm using is to have Evolution publish my Exchange Calender as an iCal and subscribe to that in ical.app. I sync my iphone up on a Mac, but it may not be an option for everybody.

However, ical.app won't import any associated alerts.

---

### Post by mfloris on 2009-06-08
It looks like this is the same bug reported here: [http://bugzilla.gnome.org/show_bug.cgi?id=403903](http://bugzilla.gnome.org/show_bug.cgi?id=403903). It still appears as "unconfirmed"... Maybe posting to that thread can help raise the attention on the bug.

---

