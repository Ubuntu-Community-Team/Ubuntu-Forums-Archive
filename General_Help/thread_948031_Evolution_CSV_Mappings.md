---
title: "Evolution CSV Mappings"
date: 2008-10-14
forum: General Help
---

### Post by rockin_goliath on 2008-10-14
I was having some import trouble with a .csv file of mine to import some contacts into Evolution. Evolution was making mistakes with reading the headings of the CSV file, so I figured out what header names Evolution *expects*, renamed the headings in my file, and everything imported perfectly.

I found this out my using a terminal command that I had no idea existed:
```
evolution-addressbook-export --format=csv
```
Upon doing this, it listed the header names. I put those into a cvs file and attached it in this thread, sot hat you may enjoy its benefits. Open the file up in OpenOffice and copy over your contact data into the appropriate column. Enjoy!

---

### Post by soulenslaver on 2009-07-28
Thanks for the mappings, very useful when trying to import 500 mails from a sql query to the evolution ;)

---

### Post by TRaction on 2010-12-07
Hi R_G... I'm dreadfully new to Karmic 9.11 with Evolution 2.28. (in fact, this is my first post- I've read lots, but not posted)

I Can see the potential for what you have done as a great boon. :p

I am trying to export my Evolution contacts to CSV for backup (have used Evolution backup from menus with great success) *caveat* BUT: I want to tidy my contacts up using a spreadsheet because they are still messy from the original import I did from Outlook a year ago.

1) Can you tell me which file you mean you edited please? path/filename
2) When I use evolution-addressbook-export I get a huge error and being new to the forums, I figure that belongs on another post so I'll go post that where it seems appropriate, and come back to put a link there for you here:confused:
Thanks, Adam

---

