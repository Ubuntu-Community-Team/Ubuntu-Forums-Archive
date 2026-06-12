---
title: "sudo chown not working ?"
date: 2008-07-28
forum: General Help
---

### Post by BenOfLondon on 2008-07-28
I'm trying to follow some instructions in setting up a SVN system

a step tells me that i should make the file system directory owner of the apache2 running user (which is www-data)

I've tried the command :
    **sudo chown www-data svn**

but i get the following error 

    **chown: changing ownership of `svn': Operation not permitted**

I'm assuming that running as root will give me all rights, and considering the directory was created by root and owned by root, i am not sure of the problem.

the only thing is that i have stored the SVN system on a separate drive (/media/hda5/svn)

can anyone suggest what the problem might be ?

---

### Post by Dr Small on 2008-07-28
What about?
```
sudo chown root:www-data svn/
```

---

### Post by bodhi.zazen on 2008-07-28
sudo chown www-data.www-data /media/hda5/svn

---

### Post by geirha on 2008-07-28
Most likely /media/hda5 is ntfs or fat, which does not support ownership and permissions. This should tell you the filesystem type: ```
stat -f -c %T /media/hda5/svn
```

If you need www-data to own that svn directory you either have to copy it to an ext3 filesystem (or other filesystem that supports ownership), or edit /etc/fstab and add uid=www-data to the options for /media/hda5. The latter will of course give www-data ownership to all files and folder in /media/hda5, not just the svn-folder.

---

### Post by BenOfLondon on 2008-07-29
> **geirha said:**
> Most likely /media/hda5 is ntfs or fat, which does not support ownership and permissions. This should tell you the filesystem type: ```
stat -f -c %T /media/hda5/svn
```

If you need www-data to own that svn directory you either have to copy it to an ext3 filesystem (or other filesystem that supports ownership), or edit /etc/fstab and add uid=www-data to the options for /media/hda5. The latter will of course give www-data ownership to all files and folder in /media/hda5, not just the svn-folder.

yes ... i've just checked, the drive was an old drive that was in my machine. **stat -f -c %T /media/hda5/svn** returns back msdos. its empty anyway, so  i will just reformat it to ext3

Thanks !

---

