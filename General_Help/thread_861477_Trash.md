---
title: "Trash"
date: 2008-07-16
forum: General Help
---

### Post by Kwitu on 2008-07-16
Hi there. I have a problem. I cannot delete files which are in my trash. I tried as root, but I can't find the trash. I looked trough google.. It says permission denied. Could anyone tell me what to do, or how to get to trash by console (where it is located) so I can change permissions as root. 

Thanks.

---

### Post by aysiu on 2008-07-16
Type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username*:*username* /home/*username*
``` Where *username* is your actual username.

Then try to empty the trash again.

---

### Post by sisco311 on 2008-07-16
~/.local/share/Trash/
[http://ubuntuforums.org/showpost.php?p=5084092&postcount=2](http://ubuntuforums.org/showpost.php?p=5084092&postcount=2)

---

### Post by Kwitu on 2008-07-16
Chown has no access to /home/bakadesu/.gvfs permission denied.

---

### Post by Kwitu on 2008-07-16
Sisco thanks man, I'm gonna change permissions now..

---

### Post by Kwitu on 2008-07-16
did not work..

---

### Post by quantum-positron on 2008-07-16
If that does not work you can use the terminal command "gksudo nautilus" and navigate to your users trash "/home/positron/.local/share/Trash/files" for 8.04 I believe it is "/home/positron/.Trash/files for previous versions.
on an unrelated note, Aysiu how do you use that nifty little code block to put commands in. I feel awfully silly having to quotation mine?

---

### Post by sisco311 on 2008-07-16
> **aysiu said:**
> Type this command in [the terminal]("http://www.psychocats.net/ubuntu/terminal"): ```
sudo chown -R *username*:*username* /home/*username*
``` Then try to empty the trash again.
very good solution

but how about:
```
sudo chown -R $USER. $HOME
```

---

### Post by sisco311 on 2008-07-16
> **Kwitu said:**
> Chown has no access to /home/bakadesu/.gvfs permission denied.
you can ignore that error

---

### Post by aysiu on 2008-07-16
> **Kwitu said:**
> Chown has no access to /home/bakadesu/.gvfs permission denied. If that's the only error message you got, it's possible you now have ownership over everything except the *.gvfs* file, which is fine. Try emptying the trash now.

> **quantum-positron said:**
> on an unrelated note, Aysiu how do you use that nifty little code block to put commands in. I feel awfully silly having to quotation mine? Use the code tags: [noparse]```
code you want in the block
```[/noparse]

---

### Post by Kwitu on 2008-07-16
Aysiu it was still saying I have no permission. I did the thing with gksudo nautilus. Will remember that forever, thank you:)

---

