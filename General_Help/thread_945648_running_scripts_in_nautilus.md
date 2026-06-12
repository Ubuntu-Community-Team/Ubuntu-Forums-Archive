---
title: "running scripts in nautilus"
date: 2008-10-12
forum: General Help
---

### Post by cong06 on 2008-10-12
I have an external that is shared out.
The easiest way to have no problems with read/write permissions for me was to have everything set at 777, full read, write execute permissions for the network.

The problem for me now is that I have plenty of text documents on this drive that I simply want to be able to open and edit. Each time, however I'm prompted incase I want to run these text documents.

I will never want to run a text document this way (I'd instead run it from command line). Can I turn it off?

---

### Post by spiderbatdad on 2008-10-12
you can do so graphically or by command in specific directories containing .txt docs: first cd into the directory...for example cd Documents. Then run: chmod 666 *.txt

---

### Post by Sam on 2008-10-12
[This](http://ph.ubuntuforums.com/showthread.php?t=829855) might help you (post #2 or #3).

---

### Post by cong06 on 2008-10-12
sorry, I was referring more to the whole pop-up.
Is there a way to make it default to "display" instead of even prompting me?

ie: If I'm double clicking on it, I always want to display/edit it.

---

### Post by Sam on 2008-10-12
> **cong06 said:**
> sorry, I was referring more to the whole pop-up.
Is there a way to make it default to "display" instead of even prompting me?

ie: If I'm double clicking on it, I always want to display/edit it.

Ah ok. Open nautilus, menu "Edit / Preferences", tab "Behaviour", and select "View executable text files when they are opened".

---

