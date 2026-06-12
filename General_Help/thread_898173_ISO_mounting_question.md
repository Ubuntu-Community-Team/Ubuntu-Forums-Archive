---
title: "ISO mounting question"
date: 2008-08-23
forum: General Help
---

### Post by Greenbean209 on 2008-08-23
Well i'm trying to mount an ISO for a game using the command line I'm using the code 

```
sudo mkdir /media/cdimage
sudo mount -o loop ''myfile''.iso /media/cdimage
```

But when I use the second part like this
```

sudo mount -o loop diablo2playdisc.iso /media/cdimage
```

I get this in return 
```

diablo2playdisc.iso: No such file or directory
```

Yes the name is typed correctly. I've encountered this problem when ever I use command line based programs so I don't know what or if i'm doing something wrong. If anybody has experience with this code please respond. Also I'm looking for a good guide for using the linux command line. I've been using ubuntu for a good year but I still feel like a noob when working around command lines.

---

### Post by Diabolis on 2008-08-23
For the CLI: [Linux Command Directory]("http://www.linuxdevcenter.com/linux/cmd/")

For the ISO: [Mount and Unmount ISO images with GUI Tool in Ubuntu Linux]("http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html")

According to a comment on that page, it is already in the repository. So you can just:
```
sudo apt-get install furiusisomount
```

And there is also another tool called **gmount-iso**.

---

### Post by mb_webguy on 2008-08-23
Are you in the directory where the iso is located?  If not, use the "cd" command to change to the directory containing the iso file, and then type the command you were using to mount the file.

---

### Post by Loaded.len on 2008-08-23
I've always done this to mount ISO's and it's never failed for me..

```
sudo mount -o loop -t iso9660 /[dir]/[filename.iso] /cdrom
```

---

