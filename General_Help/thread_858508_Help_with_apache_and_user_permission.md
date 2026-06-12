---
title: "Help with apache and user permission"
date: 2008-07-13
forum: General Help
---

### Post by Sarke on 2008-07-13
Hi, I'm not very up on the permissions and I would like some help with Apache.  I have a public_html folder in /home/(user)/ that I just set up for development (i.e. not public or anything like that), and I am having some problems with Apache/PHP creating files there.

At first it was all "permission denied" because the folder was owned by me and not www-data (which is what Apache is running as).  I tried setting the folder so it's owned by www-data, but then any files I create directly will still be mine, and not modifiable by Apache.

What's the best way of setting it up so both Apache and I can mess with the files no matter if the file was directly created by me or through PHP?  Can I make Apache run as me?  Is that a good idea?  Or is there a better option, like having PHP set me as the owner of the file?

I would appreciate some help as I've already tried searching and there's lots out there about permission but I didn't find anything about this particular issue.  Thanks...

---

