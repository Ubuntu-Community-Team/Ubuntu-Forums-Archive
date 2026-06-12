---
title: "Shared Folder Permission Issues"
date: 2008-11-19
forum: General Help
---

### Post by jlozinski on 2008-11-19
Ok. Not sure if anyone will be able to help.  Let me outline the "use case"

My wife and I use a computer, both having our own logins, but we want shared access to one of the drives, this contains our photos and other stories..  (ext3 mounted /data/)

How can we both access, read, write to this drive to our hearts content, but not other users (should we add one for our daughter.., perhaps she gets read only).

I created a user and group for the purpose, say "grownups", 

chown grownups: /data/ -R

husband and wife and in group "grownups" too.

Great, so we can both read and write (chmod 770 /data/ -R)..  However:

husband uploads some new photos to /data/photos/, creates a new folder "weddings", and another "the smiths" in /data/photos/weddings/

/data/photos/weddings/.... now OWNED by husband... :(

now wife can't upload photos for "the joneses" in weddings, because "weddings" is owned by husband.

What I want is to "squash" the permissions, or sticky or whatever so that if husband creates files or folders in /data/.... they get the group and user "grownups" and are read/write to members of that group..

Here are my solutions:
[LIST=1]
[*]format /data/ drive VFAT, and use umask, solve the problem, but lose other lovely linux stuff like symlinks or whatever
[*]mount /data/ drive to /mnt/data/ then:
[LIST]
[*]export the /mnt/data to local host with squashuser to "grownups"
[*]mount localhost:/mnt/data to /data/ and then all writing works as desired
[/LIST]
[*]every time the computer mounts /data/ do chown grownups: -R on it (i.e. get to feel the pain of vista style boot times)
[/LIST]

I am currently doing the 2nd and it works a treat, but I really want a way to do this without the need to mount again via network as it adds read/write overheads..  Is there any way that a straigt mounted Linux FS can allow what I'm after.  I basically want to set umask on a mount, or per dir (not per user)..  (Some actions via this route take up to 5 times as long)

Any help really welcome..  I am basically toying with reformatting to VFAT to get my speed back :(

---

### Post by KeyserSoze93 on 2008-11-19
Well, what about a cronjob to chown everything on the drive every few hours, or something like that. You can also specify the UID and GID in fstab. AFAIK, symlinks WILL work on other filesystems, since they are just files (unlike hard links, which are all tied up to the filesystem).

---

### Post by jlozinski on 2008-12-03
I have it!

ACLs

Apparently mount ext3 with acl as an option and now I can set extended acls which let me specify default create permissions on  a per user basis.

We don't even need a group..

How is this fact hidden??  ACLs are installed by default in ubuntu (as far as I can tell, I never installed them), but the drive needs to be mounted with acl as an option.

This is awesome..  I will play with this when I get home..

---

