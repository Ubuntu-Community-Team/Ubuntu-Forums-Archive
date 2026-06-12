---
title: "[SOLVED] How to delete old backups?"
date: 2008-08-07
forum: General Help
---

### Post by shelbyvision on 2008-08-07
I've been having problems with my Linux partition being totally full, which is very disabling. The apparent cause is automatic backups. I'd like to delete the older backups to free up space, but it won't let me, saying I don't have permission to do that. How can I delete those old backups?
Also, I have an external hard drive with tons of extra space that I could backup to, but there doesn't seem to be any way to backup to anywhere except   my regular hard drive, or a network. Is there any way around that?
Thanks,
Steve Shelby

---

### Post by drs305 on 2008-08-07
Assuming you know where these backups are and their names, open nautilus or another file browser with sudo powers, navigate to the folders and delete them.
```
gksu nautilus
```

I think you will have to be more explicit on how you are backing up your system before we can recommend how to change it. You can certainly back up to an external drive if it is mounted and you have permission to write to it. Again, if you explain things more we can give you ways to do it.

Added: Changing the backups to another drive would be a good idea. If you have a problem with your main drive the backup files would be located on a different (operating) drive. ;-)

---

### Post by ConMan318 on 2008-08-07
Sounds like your backups are owned by 'root'.  Since they are automated backups, would it be correct to assume that it saves them all to an isolated directory?  If so, you can use 'chown' with the recursive option to transfer ownership to you.  In the command line, enter
```

sudo chown -R **userName** /path/to/backupFolder

```

Then you should be able to remove all of them with the 'rm' command.

You could also just use 
```

sudo rm **file**

```
on each file.

---

### Post by shelbyvision on 2008-08-07
> **drs305 said:**
> Assuming you know where these backups are and their names, open nautilus or another file browser with sudo powers, navigate to the folders and delete them.
```
gksu nautilus
```

I think you will have to be more explicit on how you are backing up your system before we can recommend how to change it. You can certainly back up to an external drive if it is mounted and you have permission to write to it. Again, if you explain things more we can give you ways to do it.

Added: Changing the backups to another drive would be a good idea. If you have a problem with your main drive the backup files would be located on a different (operating) drive. ;-)

Thanks. that nautilus trick is very helpful. I got rid of all the previous backups, and ran backup manually, and now there is only about 29 mb free space. I've got 5 days until the next automatic backup.
I'm using Simple Backup Suite 0.10.4. The default directory for backups is /var/backup. The alternatives it has for backup destinations are "Use a remote directory (SSH or FTP), or "Use custom local backup directory", which has the following options: root, desktop, myname, other. If I click "other" it goes to a window with the same choices, a search, which doesn't seem to work, and an add button which is grayed out.
The external hard drive is usb connected, and is listed in the directory tree under "Media"
Steve

---

### Post by drs305 on 2008-08-07
You can make some room on your drive by cleaning up the downloaded packages in /var/cache/apt/archive. These are packages which were downloaded and used to install your apps. "sudo aptitude autoclean" will remove all outdated packages. If you need them later all current packages can be downloaded again via synaptic. A more aggressive method would be "sudo aptitude clean", which removes all downloaded packages, outdated and current. Again, you dont' need any of these packages once the apps are installed, but after running 'clean' outdated packages would be more difficult to restore. There is an app called APToncd which can save these packages to a cd if you would like to keep copies of the packages.

You can also empty your trash bins, including root's. This probably still contains the archive files you deleted. To delete the trash files, open nautilus again with root powers:
```
gksu nautilus /root/.share/local/Trash
```
Use the SHIFT-DEL key combo to delete the 'info' folder first, then the 'files' folder.

You can then navigate to ~/.local/share/Trash and do the same to your user trash. ~/ is the shortcut way of indicating your home directory.

I don't use simplebackup. Can you currently read and write to your usb drive? If you go to Places, Removable Media, do you see your usb drive and can you write/add files to it? It's possible you just have to look at it via Places to get it mounted and then simplebackup will see it. 

The other way would be to try to list it in simplebackup's Other menu once you are sure the usb drive is mounted (i.e. you can read files that are currently on it) and writeable. Try clicking on 'Other' and then typing in /media/yourusbdrivename.

---

### Post by shelbyvision on 2008-08-07
> **drs305 said:**
> You can make some room on your drive by cleaning up the downloaded packages in /var/cache/apt/archive. These are packages which were downloaded and used to install your apps. "sudo aptitude autoclean" will remove all outdated packages. If you need them later all current packages can be downloaded again via synaptic. A more aggressive method would be "sudo aptitude clean", which removes all downloaded packages, outdated and current. Again, you dont' need any of these packages once the apps are installed, but after running 'clean' outdated packages would be more difficult to restore. There is an app called APToncd which can save these packages to a cd if you would like to keep copies of the packages.

You can also empty your trash bins, including root's. This probably still contains the archive files you deleted. To delete the trash files, open nautilus again with root powers:
```
gksu nautilus /root/.share/local/Trash
```
Use the SHIFT-DEL key combo to delete the 'info' folder first, then the 'files' folder.

You can then navigate to ~/.local/share/Trash and do the same to your user trash. ~/ is the shortcut way of indicating your home directory.

I don't use simplebackup. Can you currently read and write to your usb drive? If you go to Places, Removable Media, do you see your usb drive and can you write/add files to it? It's possible you just have to look at it via Places to get it mounted and then simplebackup will see it. 

The other way would be to try to list it in simplebackup's Other menu once you are sure the usb drive is mounted (i.e. you can read files that are currently on it) and writeable. Try clicking on 'Other' and then typing in /media/yourusbdrivename.

Thanks for all your advise. I was able to clear out over half of the partition!
I went back to the backup configuration and discovered a way to navigate up to the / directory, so I could then find "media" and then my external hard drive, so I was able to set up a destination folder there. It works! Woo-Hoo!

---

