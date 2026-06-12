---
title: "Fedora3 -&gt; Ubuntu 4.10"
date: 2005-01-29
forum: Installation &amp; Upgrades
---

### Post by hindiogine on 2005-01-29
I am presently running a Fedora 3 Intel Pentium III PC and I would like to migrate to Ubuntu.

I have the following migrations requirements:

1. Kontact -> Evolution.  I need to migrate my mail (all folders), contacts and appointments from Kontact to Evolution.  Is it possible?

2. I would like to display the timestamp of my emails in 24hr format.  It is easy to do so in Kontact.  Can it be done in Evolution?  I strongly detest the AM/PM.

3. I need to keep my bookmarks in Firefox 1.0.  How can I do so?

Looking forward to joining the Ubuntu community.

Enrico

---

### Post by Jspired on 2005-01-29
The only question I can answer is your third.  Open your Firefox bookmarks and click on "export."  Save the bookmarks to "whatever" and then all you need do is import them into your Ubuntu Firefox.

---

### Post by AMP on 2005-01-29
#1 For your contacts save them as vCards, and the load them in Evoultion, that could work, or copy all your contacts into a document and copy and paste when you make new contacts.

---

### Post by flyfishin on 2005-01-29
Do the migration on your FC3 box to make sure you don't lose anything.  I recently moved all my mail and contacts from KMail to Evolution without any problems but with a few quirks.  If I remember correctly nested folders in Kmail won't move into evolution.  Make everything a top level folder to import it.  As AMP said you can export your contacts as vcards and Evolution will import them.  When you export them from Kmail export them as one big vcard.  If you don't you get a separate vcard for every contact.  Of course if that is what you want then do it that way.

---

### Post by Adrenal on 2005-01-30
As for Firefox, right click on your bookmarks folder, select folder preferences, File, export, save as .html. 
Then, in Ubuntu, click import, select the .html file, and your set

---

### Post by hindiogine on 2005-01-30
Thanks you all for the help!  I succeded in exporting -> importing Firefox bookmarks, vCalendar, vContacts.

I still am not able to import the email from KMail.  I think that Kmail does not use mbox.  Evolution is able to import an mbox file, but Kmail stores all email as single file in folders.

Enrico

---

### Post by hindiogine on 2005-01-30
I can reply to my own question now.  Kmail has 2 formats for its email: mbox and maildir.  The default now must be maildir, because that is what I have even though I did not choose it.

Well, Evolution needs mbox and does not import maildir.  

Workaround:   create a new folder in mbox format and copy the emails that you need to that folder.  It will be something like /home/myself/Mail/migrate.  Evolution can import this without problems.

Enrico

[QUOTE=hindiogine]Thanks you all for the help!  I succeded in exporting -> importing Firefox bookmarks, vCalendar, vContacts.

I still am not able to import the email from KMail.  I think that Kmail does not use mbox.  Evolution is able to import an mbox file, but Kmail stores all email as single file in folders.

Enrico[/QUOTE]

---

