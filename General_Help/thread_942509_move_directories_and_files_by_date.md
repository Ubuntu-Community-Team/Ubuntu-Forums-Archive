---
title: "move directories and files by date"
date: 2008-10-09
forum: General Help
---

### Post by seanster on 2008-10-09
Can't quite get the move command correct when finding by date. 

Need to move directories and files older than three years from a directory called /home/samba/users to a new directory in root called /sambaarchive.  Directory structure must be preserved.  I can fix permissions when successful.  Can anyone help?
Thanks!!

---

### Post by jigsaws on 2008-10-09
Only problem with find is to preseve direstory structure. But I have an idea. You can tar old files (no problem?) and untar it at /sambaarchive. It can preserve directory structure and permissions and it is easy to script.

Is it good idea?

---

### Post by mixmaster on 2008-10-09
cd /home/samba/users
for i in `find . -mtime +1095`
do
mv $i /sambaarcive/$i
done

---

### Post by jigsaws on 2008-10-09
The only problem is to preserve directory structure. 

mv aaa/t.txt /sambaarchive/aaa/t.txt
returns error, I think (have to create /tmp/aaa/ first)

---

### Post by mixmaster on 2008-10-09
cd /home/samba/users
for i in `find . -type d`
do
mkdir -p /sambaarchive/$i
done
for i in `find . -mtime +1095`
do
mv $i /sambaarchive/$i
done

Gross but it should work.  You may end up with some empty directories

---

### Post by Idefix82 on 2008-10-09
This is how you archive things preserving their directory structure:

```
sudo find /home/samba/users -mtime +1095 -print | xargs tar -rf /sambaarchive/archive.tar
```

To then extract the archive contents with the directory structure preserved:
```
sudo tar -xf /sambaarchive/archive.tar
```

Hope this helps. Ask away if you need certain bits explained.

---

### Post by mixmaster on 2008-10-09
I thought about using tar ... you can use the 
tar -cf - `find_command` | tar -xf - 
syntax to do it all in one go.  But you then have to go back and remove the original files.  Or at least I assume this because the original question was to move, not archive, the files.

---

### Post by Idefix82 on 2008-10-09
> **mixmaster said:**
> I thought about using tar ... you can use the 
tar -cf - `find_command` | tar -xf - 
syntax to do it all in one go.  But you then have to go back and remove the original files.  Or at least I assume this because the original question was to move, not archive, the files.

Good catch. The modified command should look like this:
```
sudo find /home/samba/users -mtime +1095 -print | xargs tar -r --remove-files -f /sambaarchive/archive.tar
```

---

### Post by seanster on 2008-10-09
> **Idefix82 said:**
> Good catch. The modified command should look like this:
```
sudo find /home/samba/users -mtime +1095 -print | xargs tar -r --remove-files -f /sambaarchive/archive.tar
```

Thanks!  Did not think of using tar.  Move is critical goal. Will do backup first then will post results when run and archive untarred. Cannot do right away, but will test first and let you know if I am successful.

---

