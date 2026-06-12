---
title: "I have to sudo to run locate on my laptop"
date: 2008-09-28
forum: General Help
---

### Post by ldfj3jf on 2008-09-28
Hi,

I don't get this - on my laptop running ubuntu eee I do:

- locate firefox
"locate: can not open /var/lib/mlocate/mlocate.db"

- sudo updatedb
"" (no output, normal)

- locate firefox
"locate: can not open /var/lib/mlocate/mlocate.db"

- which locate
(it's the usual usr/bin/locate which is a symlink to /etc/alternatives/locate, itself a symlink to mlocate) - normal

- sudo locate firefox
... (normal results)

BUT - on my desktop - I can  locate without sudo -> how can I fix this?

---

### Post by Cool Surfer on 2008-09-28
I think some files must be corrupted.
Let the bosses answer, i am also interested in this.

---

### Post by ju2wheels on 2008-09-28
You should have the following permissions on the db (this is what mines is and ive never used it so it should be at its default and I can use locate without sudo):

```

-rw-r-----  1 root mlocate 8312425 2008-09-28 01:17 mlocate.db

```

So just run this and you should be all set:
```

sudo chmod 640 /var/lib/mlocate/mlocate.db

```

Also if it does not show root and mlocate for owner/group do the following:
```

sudo chown root:mlocate /var/lib/mlocate/mlocate.db

```

---

### Post by northern lights on 2008-09-28
```
/var/lib/mlocate/mlocate.db
```is by default owned by root, who's got read/write access and the group 'mlocate' has read rights.

Most likely the user you log-in with is not part of the 'mlocate' group.

You can either change the permissions of 'mlocate.db' and give read access to anybody for instance, or, which would be slicker, add yourself to the mlocate group.

```
sudo useradd -G mlocate USER
```where USER is your username, should accomplish this.

Alternatively, you can take the GUI route through "System > Administration > Users & Groups" in the gnome menu.

---

### Post by Yannick Le Saint kyncani on 2008-09-28
mlocate is sgid, so you don't have to be in the mlocate group :

-rwxr-sr-x 1 root mlocate 35848 2008-03-08 19:23 /usr/bin/mlocate

---

### Post by ldfj3jf on 2008-09-28
Mmmm.... thank you for the replies but that's not it...

"ls /var/lib/mlocate/mlocate.db -l"
-rw-r----- 1 root mlocate (etc).

(SGID with the correct permissions set)

No idea what's going on here....

---

### Post by ldfj3jf on 2008-09-29
> **ldfj3jf said:**
> Mmmm.... thank you for the replies but that's not it...

"ls /var/lib/mlocate/mlocate.db -l"
-rw-r----- 1 root mlocate (etc).

(SGID with the correct permissions set)

No idea what's going on here....

<bump?>

---

### Post by abecedarius on 2011-08-09
I have the same problem, running Ubuntu 11.04:

$ locate foo
locate: can not open `/var/lib/mlocate/mlocate.db': Permission denied

The permissions on mlocate and mlocate.db are what posters here have said they should be. This is on a new System76 laptop with everything preinstalled. (Well, I've installed some packages in the week since it arrived, that's all.)

I guess I should open a bug on some Ubuntu bugtracker? I'm new here, been off in OS X-land this past decade.

---

### Post by remotusesse on 2011-09-07
Above suggestions did not work for me. The file permissions and owner and group where as described. I simply changed permissions to allow world readable. 

$ chmod 644 mlocate.db

After that I can use locate as normal, hope that helps some.

---

### Post by audunpoi on 2012-07-29
I have this problem on a fresh install of 12.04. I also did a fresh install on another machine withouth this happening.
The workaround from remotusesse ($ chmod 644 mlocate.db) allowed me to use locate again.

---

