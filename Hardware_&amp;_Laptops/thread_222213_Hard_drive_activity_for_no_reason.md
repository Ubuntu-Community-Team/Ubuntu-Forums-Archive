---
title: "Hard drive activity for no reason?"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by jis on 2006-07-24
Some time when my computer is on and I am not doing nothing special, hard drive starts to do something for several seconds. Why? How can you check what program is using the hard drive? How can you test, if my hard drive is in good condition?

---

### Post by jordilin on 2006-07-24
When something goes on behind the scenes, type
```
top
```
and see which processes are consuming the cpu or using your harddrive. Take into account that there are set up cron jobs by default in Ubuntu, like updatedb which updates the database for locate and a few more. So it's pretty normal what you say 8)

---

### Post by jis on 2006-08-03
Thanks, it seems to be updatedb using my hard drive. I still do not understand, why it must be run.

---

### Post by tomski on 2006-08-03
updatedb is used by the 'locate' command 
to keep a record of the location of all files in the / file tree

so then you can type:

```
locate xorg.conf
```

and it will list all locations that have xorg.conf
if that does not find it you will need to do a manual update:

```
updatedb
```

read this for full explanation:
[updatedb]("http://www.delorie.com/gnu/docs/findutils/updatedb.1.html")

hope this sheds a little more light on it

---

### Post by jis on 2006-10-25
Thanks, but how can you control when updatedb is run in Xubuntu? (There may be times when you don't want it to run.)

---

### Post by esaym on 2006-10-26
> **jis said:**
> Thanks, but how can you control when updatedb is run in Xubuntu? (There may be times when you don't want it to run.)
You could try copying slocate from /etc/cron.daily to /etc/cron.weekly (be sure to delete the one in cron.daily)

I think that would make it run once a week.  Or you could just remove the file from cron and when ever you want to update the database for searching for files you could do: sudo updatedb

---

