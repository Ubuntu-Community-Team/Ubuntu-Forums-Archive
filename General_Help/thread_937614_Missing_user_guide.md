---
title: "Missing user guide"
date: 2008-10-04
forum: General Help
---

### Post by kgas on 2008-10-04
Hello friends,

  I am using Ubuntu 8.04 in my laptop. When I try to get the help window thro' right click I got the error message

 "There was an error displaying help: Help document user-guide/user-guide.xml not found"

Digging showed that in the /usr/share/gnome/help folder user-guide folder and its sub folders are missing and I hope that is the cause of the error. Trying to copy this folder from another computer may solve the problem but most of the folders containing links and I am getting permission denied error. Is there any work around to solve this issue?

Thanks.

---

### Post by VartanSimonian on 2008-10-06
Try running the following command in Terminal: :-)

```

sudo apt-get install ubuntu-docs

```

---

