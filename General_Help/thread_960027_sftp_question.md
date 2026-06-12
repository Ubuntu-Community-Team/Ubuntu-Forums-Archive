---
title: "sftp question"
date: 2008-10-27
forum: General Help
---

### Post by MaindotC on 2008-10-27
If someone is sending me a file via sftp, is there a way for me to view the current status and transfer rate?  I know I can just "ls" the filename in the directory they're ftp'ing to, but I'd like to see the current rate of transfer.

---

### Post by ciscosurfer on 2008-10-27
> **strAlan said:**
> If someone is sending me a file via sftp, is there a way for me to view the current status and transfer rate?  I know I can just "ls" the filename in the directory they're ftp'ing to, but I'd like to see the current rate of transfer.You could use a **loop**.  You could install **iftop**.  You could install **iptraf**.  You could use **watch**.  The possibilites are endless.  Well, there's probably an end somewhere :-)

---

### Post by MaindotC on 2008-10-27
Is there some way other than just installing more programs?

---

### Post by ciscosurfer on 2008-10-27
> **strAlan said:**
> Is there some way other than just installing more programs?iptraf is only 744 kB installed, iftop is 104 kB installed.  If you want other methods, like programming methods (like using a **loop** as I mentioned previously), you could post a similar question in the Programming area of the forum if you want more detailed explanations.  You could learn about using **watch** by running **man watch** in your terminal.

---

### Post by MaindotC on 2008-10-27
Yeah true - I'll just install one of those and be done w/ it.  Thanks!

---

### Post by MaindotC on 2008-10-29
I tried iftop and it didn't really provide what I was looking for but it looks like it's the direction I want to take.  Perhaps I didn't start it properly or used the wrong configuration, but it showed all active network connections and I'd like it to just so file transfers.  I'm researching this more but if you know the precise option or configuration I'm looking for feel free to contribute.

---

### Post by ciscosurfer on 2008-10-29
```
man iftop
```Or, this'll keep you busy for a while: [http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

