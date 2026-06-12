---
title: "Error occured while mounting ext4"
date: 2016-09-22
forum: Hardware
---

### Post by kelvinrentwise on 2016-09-22
Hi, everytime I boot up Ubuntu it keep prompt this error and the option to press S to skip, M to manually recover. Attachment is the blkid information and fstab file information. Any help would be appreciated.

---

### Post by Bashing-om on 2016-09-22
kelvinrentwisel Hello; Welcome to the forum.

In your /etc/fstab file are the entries /dev/disk/by-uuid/XXXXXXX, do these devices exist at startup of the system - in other words are these attached so the system finds them ??
The output of 'blkid' say they are not.

[INDENT][INDENT]monkey see,
[INDENT][INDENT][INDENT]so monkey can do ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kelvinrentwise on 2016-09-22
I am not sure thou what they do. But it seems both of the UUID is not attached to any of my partition. Is there a way to check it ?

---

### Post by Bashing-om on 2016-09-22
kelvinrentwise; Well;

I can suggest to run terminal command:
```

ls -l /dev/disk/by-uuid/

```
And if those UUIDs are not in the list .. to comment out the entries in the /etc/fstab file.
Might also have a gander at what is set to be mountable:
```

ls -al /mnt/

```
to jog the memory .

If you do not know, best is not try to use it .

[INDENT][INDENT]just my thought on the matter
[/INDENT][/INDENT]

---

### Post by kelvinrentwise on 2016-09-22
I tried the following code and the attachment is my result

---

### Post by Bashing-om on 2016-09-22
kelvinrentwise; OK;

We can dig just a bit deeper .
Now, to preclude errors I copy and paste from your responses . I need that you employ "code tags".
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Post back between code tags:
```

ls -l /dev/disk/by-uuid/
ls -al /mnt/

```
And we start and see if we can follow the bread crumbs .

[INDENT]a->b->c
[INDENT][INDENT]see where we end
[/INDENT][/INDENT][/INDENT]

---

### Post by kelvinrentwise on 2016-09-22
cant reply with the code thingy. I get this error [h=1]Forbidden[/h][COLOR=#000000][FONT=&quot]You don't have permission to access /newreply.php on this server.[/FONT][/COLOR]
[HR][/HR]Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443

---

### Post by kelvinrentwise on 2016-09-22
got an error forbidden when trying to reply

---

### Post by Bashing-om on 2016-09-22
kelvinrentwise; yuk ,

> **kelvinrentwise said:**
> got an error forbidden when trying to reply

It do make it the more difficult . try again to post,  we are presently having glitches on the forum.
You are encouraged to make the report of the failure to post:
[https://ubuntuforums.org/showthread.php?t=2331266](https://ubuntuforums.org/showthread.php?t=2331266)

[INDENT][INDENT]them little things
[INDENT][INDENT][INDENT]can mean so much
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kelvinrentwise on 2016-09-23
Thanks alot for you time and reply. I manage to fix the problem myself. Apparently the problem is at the fstab file which missing the / beside the ext4. Without the / ubuntu unable to mount the ext4 correctly therefore cause an error when mounting ext4

---

### Post by Bashing-om on 2016-09-23
kelvinrentwise' Great .

Pleased and glad you found the fault .
The formatting and syntax in the fstab file must be exact .

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]onward and upward
[/INDENT]

---

