---
title: "Files in root trash that will not delete"
date: 2008-08-11
forum: General Help
---

### Post by Comhra on 2008-08-11
gksudo nautilus '/root/.Trash/'

This command won't even reveal the Root/.Trash folder.

Entered Root as Administrator using gksudo nautilus and made the hidden files visible. I navigated to .local/share/Trash.  The files and info folders are bulging with rubbish, **but** I am unable to delete them.  Tried fiddling about with permission and even manually moving them to the Ordinary Trash folder on my desktop, all to no avail.  I can't get rid of them.

Tried: sudo -i
cd .Trash

No such file or directory

Can anyone think of a way of deleting this root trash?

It's an odd one, you would think that navigating to the .Trash folder as admin would be all that's necessary but there is no delete option in the right click context menu.

Boy oh boy!

---

### Post by Comhra on 2008-08-11
Never mind, solved it myself.

---

### Post by captainskyhawk on 2010-02-12
> **Comhra said:**
> Never mind, solved it myself.

Well, what did you do?  Having this same problem myself. :P

---

### Post by plucky on 2010-02-12
> **captainskyhawk said:**
> Well, what did you do?  Having this same problem myself. :P

Read [this](http://ubuntuforums.org/showthread.php?t=898573)

Good Luck

---

### Post by theronb on 2010-10-03
Thanks!! That link saved my sanity.

---

