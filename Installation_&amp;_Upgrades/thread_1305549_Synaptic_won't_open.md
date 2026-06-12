---
title: "Synaptic won't open"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by emackey3k on 2009-10-29
Hello,

I just upgraded to 9.10.  Synaptic will not open from either the administration menu or from a terminal.  This is the error given when trying from terminal.  terminate called after throwing an instance of 'Xapian::DatabaseModifiedError'
Aborted (core dumped)

---

### Post by dvlchd3 on 2009-10-29
```

sudo update-apt-xapian-index

```

---

### Post by emackey3k on 2009-10-30
Thank you very much that worked.  I really appreciate the helpfulness of the community.

---

### Post by lionstone on 2009-12-02
didn't work for me, synaptic still dead. But I didn't get an error message from terminal, either - just total silence.

---

### Post by Izziedee on 2010-01-19
Just a comment: I arrived here because I found the message:

**terminate called after throwing an instance of 'Xapian::DatabaseModifiedError'**

in my .xsession-errors file after Synaptec crashed. I had just added the google picasa package to the package list. 

I used the command line: **sudo apt-get install picasa**

It seems to be working with Picasa 2.
Ubuntu 9.10

Rose

---

### Post by chuckh1958 on 2010-10-18
> **dvlchd3 said:**
> ```

sudo update-apt-xapian-index

```

Thanks. Worked for me too in Ubuntu 10.10.

---

