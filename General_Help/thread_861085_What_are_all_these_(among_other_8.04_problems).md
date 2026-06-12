---
title: "What are all these? (among other 8.04 problems)"
date: 2008-07-16
forum: General Help
---

### Post by foug on 2008-07-16
[http://img512.imageshack.us/img512/8233/wtfisthisml2.png](http://img512.imageshack.us/img512/8233/wtfisthisml2.png)

What are all of those? There are tons of gvfsd, dbus-daemon,  gvfsd-trash, gnome-vfs-daemon, gvfsd-burn in my process list. I've never seen an abundance of them like that in 7.10, or at all if I remember. There's about 10 of each.

Other problems I'm having is there is a slight lag when I double click a song in my playlist (using audacious) before it plays. Once again, never had this problem is 7.10.

When I try to watch a video on YouTube with Audacious open (song paused/stopped) the video will not play, there is no sound, and either firefox or audacious will crash. I've never experienced any of these problems in 7.10 so I'm not sure what to do, any help will be appreciated.

---

### Post by fedex1993 on 2008-07-16
If you restart x to many times sometimes the process pile up on each other over and over and usualyl freeze. Are that many processes there when you first boot up?

---

### Post by foug on 2008-07-16
Ok, yes, i did restart X a few times, so i rebooted and they went away. I restarted X in 7.10 and never had the processes stack like that. Any explanation for the other problems I'm having?

---

### Post by foug on 2008-07-17
So it seems that everything that could go wrong, is. Now Deluge won't open at all. It pops up for a second then closes instantly. I've removed the packaged and reinstalled it. What is going on?

---

### Post by KeyserSoze93 on 2008-07-17
> **foug said:**
> [http://img512.imageshack.us/img512/8233/wtfisthisml2.png](http://img512.imageshack.us/img512/8233/wtfisthisml2.png)

What are all of those? There are tons of gvfsd, dbus-daemon,  gvfsd-trash, gnome-vfs-daemon, gvfsd-burn in my process list. I've never seen an abundance of them like that in 7.10, or at all if I remember. There's about 10 of each.

Other problems I'm having is there is a slight lag when I double click a song in my playlist (using audacious) before it plays. Once again, never had this problem is 7.10.

When I try to watch a video on YouTube with Audacious open (song paused/stopped) the video will not play, there is no sound, and either firefox or audacious will crash. I've never experienced any of these problems in 7.10 so I'm not sure what to do, any help will be appreciated.

gvfs is the gnome virtual file system which auto-mounts network shares in a directory on your computer, so if you have accessed any network resources, like samba shares, ftp, or ssh, you will probably see gvfs stuff. If you want to see what is mounted, you can type "ls ~/.gvfs" into the terminal.

You can safely kill them, though you may have to kill nautilus as well (pkill gvfsd) which gets rid of gvfsd and all the sub processes like gvfsd-smb etc. and (pkill nautilus) without making the system unstable.

If you access a network share again, the required gvfs will automatically be restarted without you having to restart the process.

---

### Post by foug on 2008-07-17
I have done nothing with network shares at all on this desktop. No Samba, NFS, nothing.

---

