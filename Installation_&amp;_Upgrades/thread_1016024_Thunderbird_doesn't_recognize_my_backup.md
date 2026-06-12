---
title: "Thunderbird doesn't recognize my backup"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by Sorgin on 2008-12-19
I had to format my hd so I made a copy of /home/user and when ubuntu was up again I copied it back, firefox is working perfectly, all the markers etc., but Thunderbird is not, it doesn't ecognize the previous backup, anybody has an idea? It's VERY important for me to recover all that.
Thanks!

Sorgin

[http://rebelarte.ourpoject.org](http://rebelarte.ourpoject.org)

---

### Post by 73ckn797 on 2008-12-19
> **Sorgin said:**
> I had to format my hd so I made a copy of /home/user and when ubuntu was up again I copied it back, firefox is working perfectly, all the markers etc., but Thunderbird is not, it doesn't recognize the previous backup, anybody has an idea? It's VERY important for me to recover all that.
Thanks!

Sorgin

[http://rebelarte.ourpoject.org](http://rebelarte.ourpoject.org)

I have found that just copying T'bird info/directories straight over does not work. The program needs to know the info is there. It creates a profile such as "5s1m3xoa.default" under the .mozilla-thunderbird directory.
The previous installation assigns a different *.default name. You will need to open "profile.ini" in the .mozilla-thunderbird directory in text editor and change the *.default name to match your previous install. 

/home/*yourname/.mozilla-thunderbird/*profile.ini example: (you will need to enable viewing hidden files to see the directories.)

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
**Path=5s1m3xoa.default**
Default=1

[Profile1]
Name=Default User
IsRelative=0
**Path=/media/disk-1/Documents and Settings/myname/Application Data/Thunderbird/Profiles/5s1m3xoa.default**
```See if that will fix your problem. I gather by your description that you are trying to do a drop-in replacement to the new install.

---

### Post by Sorgin on 2008-12-19
thanks a lot 73ckn797!
it worked perfectly! :)

---

### Post by 73ckn797 on 2008-12-19
> **Sorgin said:**
> thanks a lot 73ckn797!
it worked perfectly! :)

Glad I could help. I actually have my T'bird directory shared with WinXP. Need to change that.

---

### Post by 73ckn797 on 2008-12-19
I have recently started using Evolution. It has a good back-up function that will restore itself also. It saves to a file, all of the info. I backup to a flash stick. Evolution comes default in Ubuntu.

---

### Post by 73ckn797 on 2008-12-21
> **Sorgin said:**
> I had to format my hd so I made a copy of /home/user and when ubuntu was up again I copied it back, firefox is working perfectly, all the markers etc., but Thunderbird is not, it doesn't ecognize the previous backup, anybody has an idea? It's VERY important for me to recover all that.
Thanks!

Sorgin

[http://rebelarte.ourpoject.org](http://rebelarte.ourpoject.org)


Please mark this thread as solved. Do that from the "Thread Tools" selection at the top of the page. It could be a help to someone else with the same issue.

---

