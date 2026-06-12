---
title: "[SOLVED] Binding Directories/Folders with mount"
date: 2008-11-09
forum: General Help
---

### Post by aikiwolfie on 2008-11-09
Ok what I want to do seems fairly simple. But it needs my sudo password to do it. I want to bind a folder in a shared space to a folder in my own privet home directory. The following code works. But I don't want to have to type it in or manually run a script and then type in my password at every login.

```
sudo --bind /media/bigdaddy/music /home/lynchk/Music
```

I have thought about making the following entry to my fstab file, but I'm not sure it will work. It just seems a little too easy and simple.

```
/media/bigdaddy/music /home/lynchk/Music
```

Currently I'm using symbolic links. But Nautilus won't let me add these as bookmarks to the places menu. Which is why I thought of using the --bind option with mount.

---

### Post by ad_267 on 2008-11-09
I'm using symbolic links for something like this and Nautilus doesn't have a problem adding them to the places menu.

See this for how to use fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by sisco311 on 2008-11-09
> **aikiwolfie said:**
> Ok what I want to do seems fairly simple. But it needs my sudo password to do it. I want to bind a folder in a shared space to a folder in my own privet home directory. The following code works. But I don't want to have to type it in or manually run a script and then type in my password at every login.

```
sudo --bind /media/bigdaddy/music /home/lynchk/Music
```

I have thought about making the following entry to my fstab file, but I'm not sure it will work. It just seems a little too easy and simple.

```
/media/bigdaddy/music /home/lynchk/Music
```

Currently I'm using symbolic links. But Nautilus won't let me add these as bookmarks to the places menu. Which is why I thought of using the --bind option with mount.
add this to the fstab:
> /media/bigdaddy/music /home/lynchk/Music auto bind

---

### Post by aikiwolfie on 2008-11-09
Cheers guys!

---

