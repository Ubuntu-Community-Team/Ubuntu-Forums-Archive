---
title: "Evolution - mail"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by oldnerd on 2006-02-06
I have survived the rigours of installing Ubuntu and estabishing a connection over the LAN (ethernet) with PPPoE and can turn the session on and off! I am having trouble getting my Evolution - mail pop3 connection to work correctly. See message:

Unable to connect to POP server pop3.homemail.com.au.
Error sending password: -ERR Login failed.

and finally...

Unable to connect to POP server pop3.homemail.com.au.
Error sending password: Operation now in progress

Is anyone familar with this scenario?    

Ta

---

### Post by katanacb on 2006-02-06
Howdies...

I had this same problem a few days ago, and couldn't figure out what the problem was even though I KNEW I was entering in the correct password. 

Turns out that what was wrong was when I launched evolution for the first time, it (evolution) auto-filled the user-id field for me in the pop3 setup tab with a default value equal to my login ID on the system (and I didn't catch it).  Unfortunately, my userid for Linux and my pop3 mail server aren't the same, so I was failing on trying to retrieve my mail (and getting the same errors as you) because it truly was using the wrong loigin ID.

Try going through your preferences for mail and make sure that the login ID that evolution is trying to use is the correct one.  Edit --> preferences   then highlight the mail account in question and hit 'edit'.  Head over to the 'receiving email' tab and make sure that the username field is correct...

I did a big DOH after I figured out this was the problem for me...

---

### Post by oldnerd on 2006-02-08
Howdy,

Thankyou very much!

I checked my user name and fiddled with it until the pop3 server was happy. That makes two of us. :D 

P.S. I may not really be an oldnerd, just old.

Ciao

[QUOTE=katanacb]Howdies...

I had this same problem a few days ago, and couldn't figure out what the problem was even though I KNEW I was entering in the correct password. 

Turns out that what was wrong was when I launched evolution for the first time, it (evolution) auto-filled the user-id field for me in the pop3 setup tab with a default value equal to my login ID on the system (and I didn't catch it).  Unfortunately, my userid for Linux and my pop3 mail server aren't the same, so I was failing on trying to retrieve my mail (and getting the same errors as you) because it truly was using the wrong loigin ID.

Try going through your preferences for mail and make sure that the login ID that evolution is trying to use is the correct one.  Edit --> preferences   then highlight the mail account in question and hit 'edit'.  Head over to the 'receiving email' tab and make sure that the username field is correct...

I did a big DOH after I figured out this was the problem for me...[/QUOTE]

---

