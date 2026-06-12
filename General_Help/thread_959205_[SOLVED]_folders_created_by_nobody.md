---
title: "[SOLVED] folders created by nobody"
date: 2008-10-26
forum: General Help
---

### Post by mosaic2s on 2008-10-26
Pl see the screen shot of the folders that I am using.
It has 4 folders - sent by a user from win xp. I can not delete them or their contents.
How to change permissions?
How to change settings that permissions are not needed in future too?

---

### Post by Zill on 2008-10-26
Open Nautilus as superuser (ie. root) and then change permissions or delete files as required.
```
gksudo nautilus
```
Caution:  Be very careful - you can cause great damage when you are the superuser!!!

---

### Post by Elfy on 2008-10-26
It's to do with the way that files are copied form windows I believe - permissions different - so even if you cahnge them now - next time you did the same you would have the same problem.

You can run nautilus as root ```
gksudo nautilus
```
navigate to your /home/Desktop through filesystem

or delete from the command line

```
sudo rm -r ~/Desktop/foldername
```

You can use tab to autocomplete the folder names - eg seat<tab>

---

### Post by mosaic2s on 2008-10-26
managed to do using 
chown
and
chmod

got stuck with spaces in the folder name. tried putting * after - and _. it worked. so i can now change permissions in the data folders as i wish.

thanks anyway.

---

### Post by geirha on 2008-10-26
Here's a couple of useful commands. The following will "find in your homedir($HOME) all files(-type f) or(-o) directories(-type d) not(-not) owned(-user) by you($USER) and list them as with ls -l"

```
sudo find $HOME \( -type f -o -type d \) -not -user $USER -ls
```

A minor change on that command will run chown on the files and directories in question:

```
sudo find $HOME \( -type f -o -type d \) -not -user $USER -exec chown $USER:$USER {} \;
```

As for the reason the files were owned by the nobody user, is probably because that's the default in samba when a user connects as a guest user in samba. You can change it to a different username in /etc/samba/smb.conf by setting "guest account = username". You could also change the "inherit owner" variable. From the man-page of smb.conf:
```
       inherit owner (S)
          The  ownership  of new files and directories is normally governed by
          effective uid of the connected user. This option  allows  the  Samba
          administrator to specify that the ownership for new files and direc&#8208;
          tories should be controlled by the ownership of  the  parent  direc&#8208;
          tory.

          Common  scenarios  where  this behavior is useful is in implementing
          drop-boxes where users can create and edit files but not delete them
          and  to  ensure  that newly create files in a user’s roaming profile
          directory are actually owner by the user.

          Default: inherit owner = no

```

Read the man-page of smb.conf

---

