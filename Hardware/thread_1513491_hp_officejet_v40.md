---
title: "hp officejet v40"
date: 2010-06-19
forum: Hardware
---

### Post by mystmaiden on 2010-06-19
My printer quit recently so I dug out an old hp officejet v40 this weekend and was going to hook it up but I'm having a bit of difficulty. According to [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) I'm supposed to put the following commands in the terminal

```
cd desktop
sh hplip - 3.10.2 run

```but when I do I get:
```
mystmaiden@hal:~$ cd Desktop
mystmaiden@hal:~/Desktop$ sh hplip-3.10.2 run
sh: Can't open hplip-3.10.2

```The little logo on the file looks like the ones I have to use with wine so I'm a bit befuddled now. If anyone can point out my mistake or some different instructions, I'd be most grateful.

ps. Nothing at all happened when I tried to open it with wine

Thanks-

mystmaiden

---

### Post by 11hjpphty76lkjj on 2010-06-19
This is my personal view, I am no longer working on the HPLIP project.

But anyway, you have a space and version incorrect.

Should be something like

```
sh hplip-3.10.5.run
```

Where the 3.10.5 is the actual file/version you downloaded.

A

Edit: You don't want to run the file with wine. Although in theory the hplip that is in the repo's should work as the v40 is rather old. You could also try:

```
sudo apt-get install hplip-data hplip-gui
```

or  better yet just run:

```
sudo hp-setup
```

as the version that comes with lucid should support your device.

---

