---
title: "Desktop / notebook email sync"
date: 2008-12-04
forum: Hardware
---

### Post by jeffsa12 on 2008-12-04
Running Ubuntu 8.04 x-86 on my desktop and 8.10 amd64 on my new notebook. 

I use Evolution mail, POP3 via gmail. I'd like to be able to use my Evo mail on my notebook and have all the same, up to date folder info as my desktop.

I have set up Evo mail on my notebook by importing a backup, etc.
Now when I open Evo on the notebook, it has only the email dated from the backup...no newer email's show up.

I tried to google for info for this, but really didn't find anything to "sync" as I am trying.......Is synchronizing what I am after here....Most sync I find relate to hand held devices sync to computer, etc.

I came up with an idea to try to use rsync w/ gui, grsync to sync my notebook to sftp://192.168.0.4/home/jeff/.evolution/mail/pop/jeffrs12@pop.gmail.com/cache over my network using ssh to /home/jeff/.evolution/mail/pop/jeffrs12@pop.gmail.com/cache.

I get the following error message.

>  ssh: sftp: Name or service not known

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(454) [sender=2.6.9] 


Possibly a file permission issue here as I had to "sudo" grsync to try this? Is this going to work? Is there a better/different way to do this?

Thanks...

---

### Post by timcredible on 2008-12-04
i have 2 machines and found it easiest to just access my email via the web browser, no worry about syncing anymore.

---

### Post by jeffsa12 on 2008-12-04
Yea,

I never really used pop mail till I switched to Linux full time. 
Now that I have used Evo mail....its great, and I really don't like gmail's interface. If I can't get this to work, I'll just use my yahoo web mail when I need email on my notebook.

Have you used hss and rsync or grsync for any other network file sync??

---

### Post by estamand on 2008-12-04
Why not use IMAP instead of POP3?  With IMAP your emails will stay on the server, be available to any email client you use and also be available via the webinterface when you are away from your computer

[http://mail.google.com/support/bin/answer.py?hl=en&answer=75725](http://mail.google.com/support/bin/answer.py?hl=en&answer=75725)

---

### Post by jeffsa12 on 2008-12-05
Thanks for the input and info estamand,
Sounds like IMAP is what I'm looking for exactly.

I googled for more info and came across bug reports regarding Evo mail and IMAP.

You use Thunderbird, Evolution, or another email client using IMAP?

---

### Post by estamand on 2008-12-07
I mainly use Thunderbird, webmail and Outlook when on my work Laptop.  0 problems with Imap here.

---

