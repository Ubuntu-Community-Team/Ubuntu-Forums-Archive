---
title: "Really bad problem with user account and sharing a printer..."
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2005-07-26
I wanted to share a printer connected to my linux box with the network, so I read that I needed to access the CUPS web admin page by going to:

[http://localhost:631/admin](http://localhost:631/admin)

So, I went there and found out I couldn't log in. Then I went here and read that I needed to add my user account to the lpadmin group:

[http://www.cups.org/articles.php?L237+I10+TMine+P1+Q](http://www.cups.org/articles.php?L237+I10+TMine+P1+Q)

The problem now is that I still can't log-in and my group is messed up. I can't run any sudo commands. When I do I get the following:

chiddy is not in the sudoers file.  This incident will be reported.

Is there a way to edit a config file and put my user account into its old group? For example, temporarily add myself as I am now to the sudoers file, boot into Ubuntu and move myself back into my old group and then reset the sudoers file? Or even better is there a config file where I can just change my group directly? I can boot using Knoppix and access the root drive that way. I have no access from my current user since the sudo command won't work.

And after this is all fixed, can someone tell me how to share the printer?

---

### Post by audax321 on 2005-07-26
Okay I fixed the group problems by just editing my /etc/group file (used another hoary installation on my laptop as reference).

Now, how to share the printer............   :?

---

### Post by audax321 on 2005-07-26
Ok, done.. just had to enable cups support in smb.conf.

---

