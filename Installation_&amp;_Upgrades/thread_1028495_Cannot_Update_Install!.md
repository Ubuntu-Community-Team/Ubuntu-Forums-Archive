---
title: "Cannot Update/ Install!"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by Canadaxcel24 on 2009-01-02
I am having trouble with the update/ install programs on my computer.I get the error message "W: Failed to fetch [http://mirror.imbrandon.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://mirror.imbrandon.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to guardian.oru.edu 8080:" I have been searching the forum for possible solutions, but I can't find anything that matches or fixes my problem. Any help is greatly appreciated!:D

---

### Post by gamerchick02 on 2009-01-02
I looked at the site you posted, and I got a 404 error.  I guess the package isn't there anymore?

In any case, I'd try removing it from your list of repos, and then try the update.

Amy

---

### Post by oldos2er on 2009-01-02
Have you tried a different server?

---

### Post by Canadaxcel24 on 2009-01-02
I think that the problem is the guardian.oru.edu part. I go to ORU (university), but I am not there now, so I need to tell my computer to stop going there. I tried changing my internet and network settings, but it doesn't change the settings for the update/upgrade programs. I am not sure if I need to change some root setting, or if these programs have some sort of setting I need to change.

---

### Post by Canadaxcel24 on 2009-01-02
How do I change the server?

---

### Post by oldos2er on 2009-01-02
> **Canadaxcel24 said:**
> How do I change the server?

 Via the menus System, Administration, Software Sources, click the 'Download from' tab, 'Other,' 'Select Best Server.'

---

### Post by Canadaxcel24 on 2009-01-03
It is still not downloading the repositories, even with the "best server". By the way, thank you all for your help so far. I love Ubuntu and the support system we have.:D

---

### Post by gamerchick02 on 2009-01-03
Is it a server problem or a repository problem? I'd remove that repository from your list.

Go to System-Administration-Software Sources, put in your password, then click on the "Third-Party Software" tab.  There you will see a list of all the third party software sources (NOT included with the install of Ubuntu).  Find the ofending one and uncheck the box (this will keep it from updating), or click "Remove" (deletes it from the list).

What I think is happening is that the repository is not being updated anymore or that it was taken down.  I had a similar problem and removing the offending repositories fixed it.

What software were you downloading that required a different repo?  I know that gwibber and last.fm do.

I hope this helps you out; at least somewhat!

Good luck,

Amy

---

### Post by Canadaxcel24 on 2009-01-03
It is doing that with all the repositories though. I just put that one because the whole list of bad repositories would take up the whole page.

---

