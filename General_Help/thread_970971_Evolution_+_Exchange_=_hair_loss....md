---
title: "Evolution + Exchange = hair loss..."
date: 2008-11-04
forum: General Help
---

### Post by dlstyley on 2008-11-04
I've been trying to use Ubuntu as OS for my work laptop.  I am 90% of the way there.  The biggest exception is an alternative for Outlook/Exchange.  

Everything I read says that Evolution works well for this, but I run into a lot of frustration.  I wanted to see if other people have these same issues or if it's just my setup:

Very Slow Checking Recipient Names
==================================
Evolution has the same feature as Outlook in that when you type i nthe "To:" field, it automatically startings suggesting names from your address book and/or your Contacts stored on the Exchange server.  Sometimes (and I'm not sure what causes it), I get huge lags where Evolution locks up during this process.  It might take just a few seconds, or up to several minutes to get control back.  

Stops Automatically Refreshing Inbox
====================================
Normally as email comes in, the Inbox of Evolution refreshes automatically.  At some point (usually when left up overnight), this stops happening and I have to manually refresh the folder.  When I do this, again, Evolution locks up and may take several minutes to return.  When it does, it still will not continue to update with me manually refreshing.  I have to shut it down and restart to get it working automatically again.

"Date" Sort Order
===============
In Outlook, when you click "Received" header, the default sort is most recent at the top.  In Evolution, with the "Date" header, it is the opposite.  i realize this is more of a "preference" than a bug, but it sure seems like Outlook's default makes more sense.

Weird "Sent" Dates
==================
Sometimes messages come in with strange dates that don't appear to reflect reality (I think this is a separate issue with certain mail systems and the way they do date formatting).

"From" Sort Order
===============
The "From" sort order seems like it is case sensitive.  So if I don't know where someone's display name is capital or not, I have trouble finding messages from a certain person.

"Lost" Email
============
I'm not sure why this happens, but I think it has something to do with automatic archiving from Outlook (I use a VM with Outlook sometimes when I don't trust Evolution).  When archiving runs, for some reason my Evolution mail file gets corrupted and all my mail is deleted.  It is still on the server, but I have to purge my Evolution configuration and rebuild it to get my mail back.  


I realize that it is possible that there is something wrong on the server, however Outlook works fine for me and other people.  Also, OWA works fine, and iPhone sync works perfectly (if Apple can do it, why can't Evolution?)

I do sometimes have Outlook hooked up to my account at the same time as Evolution, which might cause a problem, but I have made efforts to keep Outlook turned off and still run into these same issues.

---

### Post by dlstyley on 2008-11-06
I upgraded to Intrepid Ibex which includes Evolution 2.24.1.  All of these problems seem to persist (at least the ones I can verify easily, for others, time will tell).

One additional issue - when sorting by "From", it would make life a lot easier if the messaged grouped by a partcular name were sorted additionally by date.  Otherwise it is diffuclt to go through a bunch of messages from a single person that are in a random order.

---

### Post by Coreigh on 2008-11-06
I am using Evolution 2.12.1 on Ubuntu Desktop 7.1 with an Exchange 2000 mail server on a Windows network.

The delays (mine aren't as bad as yours) and the periodic need to restart I can confirm are "the way it is."

The weird sent times/dates I have not seen, and I think you are right these are a mail system/server issue.

I do not use auto-archiving. I archive manually and only at specific time for specific reasons. Perhaps related to this, I do not cache that mail on my computer, it stays on the server. If I am not on the local network then I have no mail. If I *really need* it then I can pop on to web-mail. But where I work email outside the office is frowned upon for security concerns.

Finally the sort order issue is easy. Those buttons are toggles. If you click and do not get the sort-order you want/need then click it again, it sorts the other way.

---

### Post by dlstyley on 2008-11-06
I guess I should have given info on the server config:

Exchange Server 2003 on Windows Server 2003

Thanks for confirming the lag issue.  Maybe I'm on a slow network or perhaps just a volume issue in terms of numbers of email address records.

Note that the sorting issue you mentioned is just a minor annoyance.  Clearly I can click the "Date" button a second time, but I would still contend that most recent first would be the most logical choice for the  way it sorts on the first click (minor issue though).  The bigger issue is when you sort by "From" and the messages grouped by a particular sender are in a random order.  That's really annoying when you have a few dozen messages from one sender.  

Also, the case sensitivity issue on the sort in the "From" field is really annoying.  That seems like an easy bug to fix.

---

### Post by mesolaser on 2008-11-17
Complete solutions on hair loss.[Mesotherapy ]("http://www.mesolaserclinic.com/")help you every thing in hair loss including their treatment.

---

