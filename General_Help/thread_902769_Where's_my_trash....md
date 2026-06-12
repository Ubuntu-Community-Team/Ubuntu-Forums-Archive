---
title: "Where's my trash...?"
date: 2008-08-27
forum: General Help
---

### Post by Yart on 2008-08-27
Hello.

Somehow I've deleted many files that my non-root user doesn't have any permissions to, but it sent them to my non-root user's trash. Now I can't empty my trash or put the files back and they're just stuck there taking up much needed space.

I'm using gnome. I'm trying to use gnome-terminal to access the trash directory as root, but I can't find the directory anywhere. People have led me to /home/(my username)/Desktop/.trash, or /home/(my username)/.trash but I'd only get the File or Directory not found error.

Does anyone know where I can find my trash bin? Apparently it's in "trash:///"... but I don't even know where that is! (For all I know it could just be a mapped name)

---

### Post by Too Late on 2008-08-27
Assuming you're using Ubuntu Hardy:
```
/home/username/.local/share/Trash
```

edit: Actually, the files are stored in a 'files' subfolder:
```
/home/username/.local/share/Trash/files
```

---

### Post by Yart on 2008-08-27
Alright! I found it there. I removed the trash and it's all good to go!

Thanks a lot!

---

