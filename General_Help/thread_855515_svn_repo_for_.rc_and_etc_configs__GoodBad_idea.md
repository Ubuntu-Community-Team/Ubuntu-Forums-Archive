---
title: "svn repo for *.rc and /etc/* configs?  Good/Bad idea?"
date: 2008-07-10
forum: General Help
---

### Post by sadohert on 2008-07-10
I'm looking for some experienced thoughts or opinions here.  I would like to keep version history of a bunch of my configs I use/setup commonly on my system (or systems I'm working on).  This will allow me to revert to previous versions if I encounter problems, or had some previous way I did things, and I can easily grab a hold of all these configs from some other system I'm at simply by doing an svn checkout from my home system to the system I'm local to.

So, that's the "why?".  The how is what I'd like to hear thoughts or ideas on.

1. I made a folder in my home directory and copied all the configs I care about into this folder
```

$mkdir ~/.config_svn
$cp ~/.bashrc ~/.bash_aliases ~/.vimrc /etc/fstab /etc/ddclient.conf ~/.configs_svn

```
2. I setup an svn repository in my home directory:
```

$svnadmin create ~/repo

```
3.  I import the configs into the repository
```

$svn import .config_svn file:///home/<username>/repo

```
4.  Now delete the .config_svn directory and then checkout that same directory from the repo
```

$rmdir -fr ~/.config_svn
$cd
$svn co file:///home/<username>/repo/.config_svn

```
5.  So, now I have a working copy of my config repository in my home directory (/home/<username>/.config_svn/).  My next step is to create symbolic links for all these configs from their original location to the working copy. 
```

$sudo rm -f /etc/fstab
$sudo ln -s /home/<username>/.config_svn/fstab /etc/fstab
$sudo rm -f /etc/samba/smb.conf
$sudo ln -s /home/<username>/.config_svn/smb.conf /etc/samba/smb.conf
$rm -f ~/.bashrc
$ln -s ~/.config_svn/.bashrc .bashrc
etc. etc.

```

So now, I can edit these files from their original locations, or from the ".config_svn" directory, and I can commit changes whenever I want from the ".config_svn" directroy. I can also have them all quickly backed up just by backing up the repo (which would happen on my homedir regular backup to Amazon S3 with jungledisk).


To be honest, I haven't actually done step 5 with the /etc files (only my homedir configs).  I'm just about to.  I'm just nervous I'm opening some security hole, or screwing myself up somehow.

Here is a complete list of the files I'm using (and will no doubt grow):
/etc/fstab
.bashrc
.screenrc
/etc/mediatomb/config.xml
/etc/samba/smb.conf
/etc/ddclient.conf
.bash_aliases
.pinerc
.vimrc

Any thoughts?

---

### Post by carcdrcdr on 2008-07-10
As far as my config files are concerned I don't think I would use CVS/SVN to keep a history on them as they are meant for entire code projects... Instead try RCS, its much much much more simple.

For more info: [http://www.onlamp.com/pub/a/bsd/2000/10/19/Big_Scary_Daemons.html](http://www.onlamp.com/pub/a/bsd/2000/10/19/Big_Scary_Daemons.html)

Hey, remember, rcs is only a co, ci away...

---

### Post by sadohert on 2008-07-10
Oh, and the reason I do the symlink thing is so I can have a single "configs" project in the repo where all the files are located.... then again...maybe I don't have to do that...  I don't know.

---

### Post by sadohert on 2008-07-12
I *KNEW* there was going to be a gotcha.  So, because my fstab (and other /etc configs) were symlinked into my home directory the system was sort of hamstrung because it went for an fstab that was in a directory that wasn't yet mounted (duh!).  The system still ended up rebooting, but it was not in a fun state, and I couldn't move the original fstab back into place because the root filesystem had been mounted as read-only.  

After trying a few different things I found the suggestion that I could "remount" the root filesystem as read-write, which then allowed me to put back in place all the config files.  The command I used as superuser was:

```
mount -t ext3 -o rw,remount /dev/sda1 /
```

carcdrcdr, I think your suggestion of using RCS could work for me, so I'm going to give that a shot.  If I end up hamstrung again I'll follow up.

---

