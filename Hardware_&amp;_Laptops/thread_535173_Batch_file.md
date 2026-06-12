---
title: "Batch file"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by will71110 on 2007-08-26
How do I write a file to do this in terminal when I click on it:

hidd --search

My bluetooth mouse disconnects when it's idle for awhile and I have to ter and run this to connect it again. i'd rather just run a file to connect it

---

### Post by Outrunner on 2007-08-26
I think it's something like this:

create the script

```
nano script.sh
```

now write the script as follows:

```
#/bin/bash

hidd --search
```

Exit  with CTRL+X. Now give permission to execute the script:

```
sudo chmod +x script.sh
```

Now whenever you want to execute the scipt, double-click it and select "Run in Terminal"

---

### Post by will71110 on 2007-08-26
where does it save this? I cant find the file

---

### Post by Outrunner on 2007-08-26
it should be in your /home directory. Like

```
/home/username/script.sh
```

---

### Post by will71110 on 2007-08-26
That worked.  Thanks. :)

I also had to chmod 775 script.sh

chmod did not work by itself

---

### Post by Outrunner on 2007-08-26
Oh, of course, what I meant was "chmod +x" but it seems I forgot to put that in. I'll edit it in now in case anyone else needs help with this.

---

### Post by pyre on 2007-08-26
Wouldn't it be easier to just have the script run periodically on its own (like in cron or anacron)?  Or is there some reason that you dont' want it running all of the time?

---

### Post by will71110 on 2007-08-26
Wont work.  My mouse only broadcast when you push a botton.  It disconnects after awhile and when it does, I have to manually connect it agian.

---

