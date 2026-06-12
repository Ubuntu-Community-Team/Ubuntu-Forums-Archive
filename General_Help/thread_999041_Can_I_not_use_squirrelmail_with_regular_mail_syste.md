---
title: "Can I not use squirrelmail with regular mail system?"
date: 2008-12-01
forum: General Help
---

### Post by Phases on 2008-12-01
I'm hoping someone can help me. They will need super l33t skillz to weed through my own confusion and help me figure myself out.

I've been working on this for days. I have followed flurdys guide for setting up a mail server using postfix but can't get squirrelmail to work for the life of me.

Here is what (I think) I know.

Mail works. You know, I type "mail" it tells me my new mail, i can read, reply, etc. I can recieve and send to wherever, using a comcast server as a relay.

[email]phases@superstickphase.com[/email]

It users the regular unix mail dir, var/spool/mail for new mail, seems to store non-new mails in /home/phases/mbox

I've been tailing mail.log and mysql.log during all this.

What I want to do is use squirrelmail for this! Can I? Or must I use the virtual directory that squirrelmail keeps looking for when I try to log in. It doesn't find it and IMAP drops my connection:

/var/spool/mail/virtual/phases

there is a vitual folder, but no phases inside.

I've added a phases folder, played with sym links to /var/spool/mail/phases, messed with dir's it points to in phpmyadmin when it authenticates, I just can't get it to work.

Anyone have any insight? I just want to setup squirrelmail to work with the standard unix mail system. (I guess?)
__________________

---

### Post by Phases on 2008-12-04
Pretty please?

---

### Post by Phases on 2008-12-05
This thread was my third or 4th reach out for help with this issue over a couple weeks.  

...anyway, figured it out. 
Thanks.

---

