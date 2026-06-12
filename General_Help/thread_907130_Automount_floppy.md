---
title: "Automount floppy"
date: 2008-09-01
forum: General Help
---

### Post by Mr.Carramba on 2008-09-01
hi!

I have edited /etc/fstab  and rebooted but the floppy drive is looks empty then I access it,
any sugegstions?


```

/dev/fd0        /media/floppy0  vfat    rw,user,auto,exec 0       0

```

another question would by how to make shortcut appier on the desctop then floppy is mounted?

---

### Post by arch0njw on 2008-09-02
I am consolidating and regurgitating responses from [here]("http://ubuntuforums.org/showthread.php?t=369231") and [here]("http://www.linuxquestions.org/questions/ubuntu-63/automagically-automount-floppy-drive-462097/page2.html").

The quick summary is that autofs doesn't work that way with floppy drives, because a FDD isn't smart enough to tell the computer "hey, a disc has been put in me".  Also note that you should change your fstab to match the one in the quote below -- not sure the way you have it now will work properly all the time.

> Insert a floppy into your drive, click "Places" -> Computer -> Floppy.
It should now start reading the floppy drive and mounting it automatically.

If this doesn't work, check that your /etc/fstab file contains the following line:
/dev/fd0        /media/floppy  auto         rw,user,noauto     0       0

PS: If you mean that you want the drive to mount by itself when you insert a floppy without you doing anything, then I'm afraid this is not possible. Floppy drives cannot sense the presence of a medium inside them, so they cannot mount by themselves like USB devices do for example.and

>                               autofs works this way round:

(eg floppy set op in autofs to mount to /mnt/floppy)

1) you try to access /mnt/floppy
2) autofs makes the directory
3) autofs mounts the floppy
4) when you've not accessed the device for longer than the timeout, autofs umounts the device
5) the directory dissappears

You will not find the floppy unless you navigate to where it should appear


---

