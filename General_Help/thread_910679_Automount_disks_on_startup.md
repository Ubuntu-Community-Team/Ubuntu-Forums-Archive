---
title: "Automount disks on startup"
date: 2008-09-04
forum: General Help
---

### Post by RolandFlagg on 2008-09-04
I used to have automount disks on startup with the fstab, but then it randomly had some problems where I couldn't mount the drives at all, so I deleted the entries in fstab. Now I want to have automount using a different way.
Would it work, or if it worked, would it screw up anything, if I put in the mount commands in sessions instead of editing fstab? It's just a thought.

---

### Post by RolandFlagg on 2008-09-04
bump

---

### Post by bingoUV on 2008-09-05
Unless there is an entry in fstab, there is no way a non-root user can mount a disk. If "put in the mount commands in sessions" means that you add it to gnome startup commands, they will not run with root privileges and hence not able to mount.

But if it does mount, it will keep working. Don't be afraid of hidden issues.

---

### Post by RolandFlagg on 2008-09-05
cool... thanks, I'll try that

---

### Post by pl@yer on 2008-09-05
> **RolandFlagg said:**
> I used to have automount disks on startup with the fstab, but then it randomly had some problems where I couldn't mount the drives at all, so I deleted the entries in fstab. Now I want to have automount using a different way.
Would it work, or if it worked, would it screw up anything, if I put in the mount commands in sessions instead of editing fstab? It's just a thought.

I don't know why you would **not **want to use fstab (that is what it's  for). There are many ways to mount a drive without using fstab ie. create your own sysv init type script, rc.local, use pmount and .bash_profile to call a mount script...

---

### Post by drs305 on 2008-09-05
Are these external drives? If so, they should automount. There are two settings in gconf-editor that you could check.

Open "gconf-editor" and Edit, Find for "automount". There are 3 settings that might help you:
/desktop/gnome/volume_manager/automount_drives
/desktop/gnome/volume_manager/automount_media
/apps/nautilus/preferences/media_automount_open

If you highlight the setting you can read about what each one does.

If you are really lazy and just want to turn all these options on, then just run this:
```

gconftool-2 --type bool --set /desktop/gnome/volume_manager/automount_drives "true" 
gconftool-2 --type bool --set /desktop/gnome/volume_manager/automount_media "true"
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount_open "true"

```

---

### Post by RolandFlagg on 2008-09-05
I used to use fstab, but apparently if I shut off my computer improperly it gets screwed up and I can't even mount the drives manually (it said "you don't have the necessary privileges to mount drive" or something). So I experimented a little and deleted those 2 lines in fstab, and boom, I could manually install. So that's why I don't like fstab... So maybe if you could suggest a way to make fstab more stable... XD

---

### Post by pl@yer on 2008-09-09
> **RolandFlagg said:**
> I used to use fstab, but apparently if I shut off my computer improperly it gets screwed up and I can't even mount the drives manually (it said "you don't have the necessary privileges to mount drive" or something). So I experimented a little and deleted those 2 lines in fstab, and boom, I could manually install. So that's why I don't like fstab... So maybe if you could suggest a way to make fstab more stable... XD

As long as a user has rights to the mount point and in /etc/fstab "users" option is used I think you would be set. Have a look at this post [http://ubuntuforums.org/showthread.php?t=910913](http://ubuntuforums.org/showthread.php?t=910913)

---

