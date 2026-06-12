---
title: "start am editor with a text- file from the shell"
date: 2008-09-29
forum: General Help
---

### Post by Generic1 on 2008-09-29
Morning,

i have a special problem, I will start an editor with a textfile so like this:

vi textfile // like this but this command doesnt work!!


so the editor starts with an textfile, is this possible,

All the best,
Generic

---

### Post by Peter09 on 2008-09-29
when you do this why does it not work, do you get an error message or a blank file or what?

---

### Post by cariboo on 2008-09-29
You can use vi in a terminal like this:

```
vi /path_to textfile
```

For example if you wanted to edit /etc/hosts using vi you would enter in a terminal:

```
sudo vi /etc/hosts
```

Jim

---

### Post by Generic1 on 2008-09-29
Hello,

thanks for the replies,
so when I execute the command "vi textfile" then I get a blank sheet and not the textfile, 

What I will do is writing a shellscript to open a textfile with an editor (it must not be the vi) and if the editor is closed I will change the mode with chmod 000, so the textfile is not changeable afterwards,

So my problems are to open the textfile with a command and the to get a response in the shellscript when the editor is closed,

Do you have still any idea, how I can do thie,
Thanks a lot,

All the best,
Generic

---

### Post by Peter09 on 2008-09-29
It sounds to me that you are not setting the path to the file correctly.

in the example 

vi <filename>

<filename> should include the path - where the file is- unless you are in the directory that the file is in.

If you type 

```
ls
```

you should see the file, if not you need either to change to the correct directory using cd (change directory) or put the full path in.

---

