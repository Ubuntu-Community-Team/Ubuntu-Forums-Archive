---
title: "Check progress on file copy?"
date: 2008-07-30
forum: General Help
---

### Post by helwitch on 2008-07-30
I started about 50GB of data copying from a drive into a directory, but it didn't give me a copy progress indicator. How can I check the progress of the copy, other than constantly checking the size of the directory the data is going into? Is there some way to find out which running process is the copy, and query it as to its progress?

---

### Post by coffeecat on 2008-07-30
How did you do the copy? I thought that if you did a drag and drop copy you got a progress bar. That's certainly true with nautilus/gnome and I thought it was so with kde/konqueror as well. I know you're using kde, but which file manager are you using, or were you using the terminal?

If from the terminal with 'cp', you could use the -v flag which gives you something of a running commentary. If you do use 'cp' make sure you use the -p flag to preserve permissions and metadata like timestamps. Also check out 'cp -a' in man cp. I usually use that option.

---

### Post by bodhi.zazen on 2008-07-30
You can use zenity

```
(cp source destination) | zenity --progress --title="Coping files" --text="Copying files ..." --auto-close
```

you need to put the entire cp command in ( ) 

See man zenity for further information.

---

### Post by helwitch on 2008-07-30
> **coffeecat said:**
> How did you do the copy? I thought that if you did a drag and drop copy you got a progress bar. That's certainly true with nautilus/gnome and I thought it was so with kde/konqueror as well. I know you're using kde, but which file manager are you using, or were you using the terminal?
I'm using konqueror, and I just select alled in the original drive, control+C, opened the destination directory, and control+V. Normally this would have given a progress dialog box. Hence my confusion when it didn't, but the files started appearing in the destination directory anyway!
> **bodhi.zazen said:**
> You can use zenity

```
(cp source destination) | zenity --progress --title="Coping files" --text="Copying files ..." --auto-close
```

you need to put the entire cp command in ( ) 

See man zenity for further information.
I needed to do it without the --auto-close. And it seemed to indicate the copy was complete, judging from the progress bar it showed, while judging from comparing directory sizes, the copy is NOT complete. Thanks tho.
Further info, in case it's relevant, the original drive being copied FROM is from a mac, so formatted whatever mac filesystem is. The destination drive is my home directory formatted ext2.

---

### Post by coffeecat on 2008-07-30
> **helwitch said:**
> I'm using konqueror, and I just select alled in the original drive, control+C, opened the destination directory, and control+V.

I usually do ctrl-a, and then right-click+mouse on one icon and drag the whole shooting match over. I wonder if because you did ctrl-a, ctrl-c, ctrl-v it's some konqueror oddity. In fact it may be a gnome oddity as well. I'll do some experiments later out of interest. I'm using my Mac atm so I can't check now. :)

> **helwitch said:**
> Further info, in case it's relevant, the original drive being copied FROM is from a mac, so formatted whatever mac filesystem is. The destination drive is my home directory formatted ext2.

The filesystem is HFS+ and it can be read from but not written to by Ubuntu. I've done copies from a hfs+ formatted drive to Linux and the only problem I came up with is that my UUID in my Mac is different from my Ubuntu UUID and HFS+ supports Unix permissions (of course). Eventually, I had to 'sudo cp' the whole lot over and then 'sudo chown' them so that I could get at them. :roll:

---

### Post by helwitch on 2008-07-30
> **coffeecat said:**
> I usually do ctrl-a, and then right-click+mouse on one icon and drag the whole shooting match over. I wonder if because you did ctrl-a, ctrl-c, ctrl-v it's some konqueror oddity. In fact it may be a gnome oddity as well. I'll do some experiments later out of interest. I'm using my Mac atm so I can't check now. :)

The filesystem is HFS+ and it can be read from but not written to by Ubuntu. I've done copies from a hfs+ formatted drive to Linux and the only problem I came up with is that my UUID in my Mac is different from my Ubuntu UUID and HFS+ supports Unix permissions (of course). Eventually, I had to 'sudo cp' the whole lot over and then 'sudo chown' them so that I could get at them. :roll:
I've done ctrl+a, ctrl+c, ctrl+v plenty of other times on this system without this problem. It's my standard copy method.
And yeah, I figured out the can't be written to thing, but didn't much care. (drive was from boyfriend's old mac, system is dead but drive has much music and files which are still wanted, so read only access isn't an issue.) And the permissions were weird, but I have a konqueror as root shortcut in my system menu, cos it's wildly convenient, so just used that to do the copy from. I'll do a chown after the data's moved. :)

---

### Post by bodhi.zazen on 2008-07-30
> **helwitch said:**
> I'm using konqueror, and I just select alled in the original drive, control+C, opened the destination directory, and control+V. Normally this would have given a progress dialog box. Hence my confusion when it didn't, but the files started appearing in the destination directory anyway!

I needed to do it without the --auto-close. And it seemed to indicate the copy was complete, judging from the progress bar it showed, while judging from comparing directory sizes, the copy is NOT complete. Thanks tho.
Further info, in case it's relevant, the original drive being copied FROM is from a mac, so formatted whatever mac filesystem is. The destination drive is my home directory formatted ext2.

oic, well zenity will work, but you may need to do some tweaking to it then,

cp | tee > zenity 

Take a look at man zenity or 

[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

Also I see you use KDE, take a look then at KDE dialog :

[http://techbase.kde.org/Development/Tutorials/Shell_Scripting_with_KDE_Dialogs#Progress_Dialogs](http://techbase.kde.org/Development/Tutorials/Shell_Scripting_with_KDE_Dialogs#Progress_Dialogs)

---

### Post by helwitch on 2008-07-30
So the copy finally did finish, as judged by file sizes and counts.

---

