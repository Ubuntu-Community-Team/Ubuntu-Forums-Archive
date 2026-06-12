---
title: "[SOLVED] Backup Gmail with Labels"
date: 2008-10-13
forum: General Help
---

### Post by diafygi on 2008-10-13
Howdy all,

I am trying to create a method for automatically archiving my gmail account while preserving labels. I have been unable to find a Evolution or Thunderbird way of doing this. I can access the messages through IMAP, but I can't find a way to backup/cache the messages in the IMAP folders. I understand that since you can have multiple labels for one message, you have the possibility of duplicate messages in different folders, but that's ok with me.

I did find a way to [download messages]("http://pengdeng.blogspot.com/2008/03/backup-gmail-via-imap-using-getmail_16.html") based on labels using getmail. Basically, the method uses getmail to retrieve messages from a certain label using the IMAP protocol, storing them in a specific mbox file. If you want to download multiple labels to multiple mbox files, you can do that easily enough with a script. Your labels have to be known in advance, and you have to import each file individually into Evolution/Thunderbird, but that's ok. At least I'm backed up with labels.

However, this getmail method runs into a problem when I try to automate the task. When you run the getmail command again, it downloads the entire list of messages again and appends them to the mbox file. This creates duplicate messages for previously archived messages in the mbox file, which mostly doubles the size of the file.

My questions:
-Is there another way to backup gmail with labels besides getmail?
-Can getmail recognize duplicate messages and not retrieve them?
-Is there a way to remove duplicate messages from mbox files?

---

### Post by diafygi on 2008-10-22
> **diafygi said:**
> -Is there another way to backup gmail with labels besides getmail?
Not that I've found.

> **diafygi said:**
> -Can getmail recognize duplicate messages and not retrieve them?
Yes, I needed to include the "read_all = false" option in the rc file. However, there is a bug with the getmail version (4.7.8) in the Ubuntu repository (Intrepid) that prevents multiple labels from remembering their messages. Version 4.8.2 of getmail fixes this bug. I've confirmed it does work. Here is the discussion on the [mailing list]("http://comments.gmane.org/gmane.mail.getmail.user/3293").

> **diafygi said:**
> -Is there a way to remove duplicate messages from mbox files?
Not that I've found, but irrelevant because above question is solved.

I am in the process of creating a script that will back up gmail accounts. Will post anything I come up with, and I seem to have all the tools to actually finish this project! Woot.

---

