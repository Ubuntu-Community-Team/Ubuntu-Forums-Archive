---
title: "How to migrate old user accounts"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by Denigris on 2009-04-22
Hi all

I was using feisty, and decided to upgrade to ibex 8.10 . I thought that I could simply upgrade by putting the live disk in and installing. I figured it would detect fiesty and offer to upgrade the system while leaving the existing user accounts intact. No such luck.

I discovered that the best I could do was to have the intrepid ibex graphic installer partition the hard drive, leaving feisty intact and using the new partition for the ibex installation. Bummer. I also know of no way to take my account and my wife's account from the feisty installation/partition and put them into ibex installation/partition. Ibex said it could "migrate" the accounts, but that only gave the admin account some common settings from feisty.

Quite simply: how do I take two user accounts from the feisty installation and put them into the new dual boot Ibex installation.

Thanks! :)

---

### Post by lemming465 on 2009-04-23
Your upgrade try ran into two issues.  First, Ubuntu only supports two upgrade paths: from one release to the next, and between LTS releases.  Feisty -> Intrepid is right out; you'd have to go through 7.10 and 8.04 as waystations.  Second, you can't do upgrades from the live desktop CD's; if you want to upgrade via CD you have to get the *alternate install* CD instead.  I think the desktop CD installs by cloning its live (compressed) filesystem; to upgrade you instead need to have all the .deb files to run dpkg against, which is the strategy the alternate install uses (basically like installing Debian; Ubuntu is a Debian derivative, after all.)

> how do I take two user accounts from the feisty installation and put them into the new dual boot Ibex installation.

Short answer: mount the old partition containing /home and copy files.

The long answer varies, depending on your goals.  Just copying the entire home directory tree is one option, but there are likely to be glitches with configuration files for applications which mutated in the meantime.  These can be overcome, but would be a nuisance and would require really good troubleshooting skills; I don't recommend it. Copying all the visible data files is quite safe; the configuration subdirectories conventionally all start with ".".  If there are specific applications such as web or email that you want to migrate stuff from, there are lots intermediates between the two extremes.

Without more details about what your disk layout is and your migration strategy, it's hard to be more specific.  Let me assume that the feisty install was a single large root partition on /dev/sda1, and that you want your visible files plus your firefox bookmarks.  While there are GUI ways to do migrations, it's easier to describe the command line variants.  Consider something along these lines: ```

# become root
sudo -i

# get access to feisty partition with the old /home
mkdir /media/feisty
mount /dev/sda1 /media /feisty
cd /media/feisty/home

# check if you found the good stuff
ls *

# copy the visible files from each home directory
for user in *; do
  pushd $user
  cp -a * /home/$user
  popd
done

# fix up ownerships (optional if uid & gid values didn't change)
cd /home
for user in *; do
  chown -R $user.$user $user
done
```

For firefox, they probably changed from storing the bookmarks in an html file to storing them in an sql lite database.  The most straightforward way is probably to boot up feisty, log into each account, start firefox, and export the bookmarks to  file.  Then back in intrepid, import them.

---

### Post by Denigris on 2009-05-01
Thanks for the info. For simplicity sake, I will just tell you what will do the job for me.

1. I need to backup all the files from 2 different user accounts
2. I want to clean install the newest version of Ubuntu desktop wiping all partitions
3. I want to create two new accounts in the new clean install
4. I want to copy all the files from the old accounts into their corresponding new accounts

I don't care about bookmarks.

My primary problem, really the only problem, is permissions. Who owns the files, and what file permissions they have. These are the changes that need to happen for the old accounts to be "owned" by the new user accounts created for them.

User accounts:

Backup;

clean install;

restore

should be simple. No scripts. Haven't a clue how to do it. :confused:

Cheers, Denigris

---

### Post by lemming465 on 2009-05-06
Sorry to be slow replying to you; I've been fighting with dead clothes washers and dying desktop computers for the last week.

> 1. I need to backup all the files from 2 different user accounts
2. I want to clean install the newest version of Ubuntu desktop wiping all partitions
That means you'll need to back up the files to something external, like a USB hard disk drive or burning a DVD-R.  If you want a GUI approach, you should be able to do this all with drag-and-drop from nautilus ("places") windows.

> 3. I want to create two new accounts in the new clean install
You'll get one of those as a side effect of the install process itself, probably.  The other one you can do with the user account manager tool.  There is a GUI one off Administration->System, I think (I'm on a Redhat box at the office, working from memory on this); the command line tool is "useradd".
> 4. I want to copy all the files from the old accounts into their corresponding new accounts

Assuming you want the visible data files, and are willing to ignore the "hidden" configuration files whose names start with "." (visible if you do "ls -a"), you can just reverse whatever you did during the backup.

The only complication is the permissions issues.  To restore the files you'll either have to be running as root (e.g. "gksu nautilus") or as the user intended to own the files, or temporarily change the ownership of the other users directory to be you.  For example if you are "fred" and the other user is "wilma",```
sudo chown -R fred.fred /home/wilma
```

If you didn't copy the other users files as that user ("wilma" for example), afterwards you'll have to reset the ownership:```
sudo chown -R wilma.wilma /home/wilma
```

The script snippets I offered previously do this more generically for multiple users by use of variables, assuming the convention that home directory names, user names, and personal group names all match.

---

