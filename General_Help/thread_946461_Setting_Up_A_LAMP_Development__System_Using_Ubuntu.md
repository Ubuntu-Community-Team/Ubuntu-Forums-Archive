---
title: "Setting Up A LAMP Development  System Using Ubuntu"
date: 2008-10-13
forum: General Help
---

### Post by ebstr on 2008-10-13
I am new to this and would like to set up a LAMP development system.
Which is the best version of Ubuntu to use for this? The Desktop or Server version? I need something with a good GUI.

Project will eventually move from the development system to my live sites.

Thanks in advance.

ebstr

---

### Post by Sam on 2008-10-13
> **ebstr said:**
> I am new to this and would like to set up a LAMP development system.
Which is the best version of Ubuntu to use for this? The Desktop or Server version? I need something with a good GUI.

Project will eventually move from the development system to my live sites.

Thanks in advance.

ebstr

If you need a GUI don't use the server version.

Read this: [uhelp]community/ApacheMySQLPHP[/uhelp]

---

### Post by ebstr on 2008-10-13
Thanks Sam!
Will check it out

ebstr

---

### Post by Greslore on 2008-10-14
I use just the regular Ubuntu Desktop (8.04) and XAMPP for all my web development.  Works great.  And, XAMPP is very easy to delete and re-set up depending on your development needs.

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by ebstr on 2008-10-15
Thanks Greslore!
I heard about XAMP but never tried it.
I will look into this also.
This is great info! Thanks again

ebstr

---

### Post by mssever on 2008-10-15
I think that XAMPP is more trouble than it's worth. If you run ```
sudo tasksel
```you can get a full LAMP stack using packaged software from the repos. And it will work right.

---

### Post by ebstr on 2008-10-15
Thanks,
Could you give me some examples
of "packaged software"

Thanks,

ebstr

---

### Post by mssever on 2008-10-16
> **ebstr said:**
> Thanks,
Could you give me some examples
of "packaged software"
apache, php5, mysql, etc. By "packaged software," I meant software that's in the Ubuntu repositories that has been adjusted as necessary to integrate it with the system. Essentially, anything you find in Synaptic falls into that category.

---

