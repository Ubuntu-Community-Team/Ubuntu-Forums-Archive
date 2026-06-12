---
title: "Trouble using external FAT32 drive"
date: 2008-11-22
forum: General Help
---

### Post by Frogbarf on 2008-11-22
I have a spiffy new 320Gig USB external hard drive containing files rescued from a dying hard drive on a Win98 machine. The drive is formatted FAT32 for compatibility with my other machines and at the moment contains only one directory where all the rescued files live. I had no trouble mounting this drive and copying the rescued files to my HDD.

Now I'd like to back up data to this drive, but can't get to first base. When I try to create another top level directory on the drive using ctrl+shift+N, I get an error box reading "error while creating directory untitled folder"/There was an error creating the directory in /media/EXTERNAL. Show more details reveals "error removing file: read-only file system."

"Create folder" in the file menu is grayed out.

Drive properties are: group=root, owner=myuserid, permissions drwx------

The one existing directory has the same properties.

If I unmount it, then go to my admin privileged id and remount it, I get group=root, owner=root, permissions=drwx------

Also, this drive seems to be permanently auto-mounted under my privileged id since the "mount" option is never functional, only "unmount".

To call me confused and puzzled is an understatement.:confused:

How can I mount this drive so all users have full r/w access to it automatically? I'd like to be able to mount it while logged in as a normal user instead of having to switch to my admin user id.

As for the theory of external drives, let me ask: Where is Ubuntu getting the permissions and the read-only status of the drive from? What is the reasoning behind treating a FAT32 partition that way? FAT32 doesn't support permissions other than a simple read-only bit on files.

---

### Post by cariboo on 2008-11-22
You have to change the permissions on the drive. The  easiet way  to do it is to open a Applications-->Accessories-->Terminal and at the propmt type:

```
sudo chmod -R 777 /media/EXTERNAL
```

this will make your drive world read/writeable.

Jim

---

### Post by Frogbarf on 2008-11-22
> **cariboo907 said:**
> You have to change the permissions on the drive. The  easiet way  to do it is to open a Applications-->Accessories-->Terminal and at the propmt type:

```
sudo chmod -R 777 /media/EXTERNAL
```

this will make your drive world read/writeable.

Jim

Tried it and it's still bitching "read-only". Can't write to the drive at all.

I should add that when I executed the command you suggested, it evidently traversed the entire directory tree and altered the permissions on each and every file & directory. And then started getting I/O errors regarding non-existent directories. Unmounting & remounting brought me back to the starting point.

Should I be editing /etc/fstab?

**_Further:_** followed instructions for mounting windows partitions at help.ubuntu.com/community/, creating a directory & mounting to it (all via admin id), but when I try to access it via unprivileged user id it's still read-only.

I'm missing something here!

**_Yet further:_** I shut down and rebooted, then plugged in my little digital camera to see if it worked. It did: auto-mounted perfectly, was able to copy files off it, and (more importantly) delete them afterwards. Turned on the accurse external drive and it appears in the file browser if I go to "computer". But when I try to mount it (using an ordinary user id), I now get the message "Cannot mount volume 'EXTERNAL'"; under details it says  "mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)."


**_Even more:_** I did dmesg and lo and behold what do I see:
```

[ 3611.565387] FAT: Filesystem panic (dev sdb1)
[ 3611.565394]     invalid access to FAT (entry 0x90909090)
[ 3611.565397]     File system has been set read-only

```

Which implies the FAT is screwy. Oh dear.

---

### Post by Frogbarf on 2008-11-22
> **cariboo907 said:**
> You have to change the permissions on the drive. The  easiet way  to do it is to open a Applications-->Accessories-->Terminal and at the propmt type:

```
sudo chmod -R 777 /media/EXTERNAL
```

this will make your drive world read/writeable.

Jim

Tried it and it's still bitching "read-only". Can't write to the drive at all.

I should add that when I executed the command you suggested, it evidently traversed the entire directory tree and altered the permissions on each and every file & directory. And then started getting I/O errors regarding non-existent directories. Unmounting & remounting brought me back to the starting point.

Should I be editing /etc/fstab?

---

### Post by Frogbarf on 2008-11-22
> **cariboo907 said:**
> You have to change the permissions on the drive. The  easiet way  to do it is to open a Applications-->Accessories-->Terminal and at the propmt type:

```
sudo chmod -R 777 /media/EXTERNAL
```

this will make your drive world read/writeable.

Jim

Tried it and it's still bitching "read-only". Can't write to the drive at all.

I should add that when I executed the command you suggested, it evidently traversed the entire directory tree and altered the permissions on each and every file & directory. And then started getting I/O errors regarding non-existent directories. Unmounting & remounting brought me back to the starting point.

Should I be editing /etc/fstab?

---

### Post by Frogbarf on 2008-11-23
I was able to correct a bunch of errors in the FAT by using dosfsck, and get the thing sort of working, but I still don't know how to get it to work like my digital camera does, namely:

[LIST=1]
[*]I plug in the drive and turn it on
[*]It automatically mounts at a known location
[*]All users (privileged admin id or not) can read, write, and delete files and create and delete directories without any further fussing around. I'd like it to "just work."
[*]I don't have to switch to my admin id and do a bunch of sudoing to get this behavior.
[/LIST]

The latest problem is one I've seen before: I try to mount the drive after turning it on and having it pop up on a desktop and get "mount_point cannot contain these characters".

By now, I've googled and searched so much, and tried so many suggestions that I've probably manually corrupted the system! I've done dmesg, I've done sudo chmod, I've done sudo mount, I've done gconf-edit, you name I've tried it.

Is there ANYBODY who really knows (no guesses!) how to get a USB, FAT32 external hard drive to behave the way I'd like it to?

It's like there's something fundamentally screwy in Hardy.

---

### Post by drs305 on 2008-11-23
The intent was not to use fstab for USB devices, but you can certainly do it. Make a mountpoint and change the ownership to yourself. Make the folder/contents accessible to everyone (that's what you want). Add the entry to fstab:
```

sudo mkdir /media/yourmountpoint
sudo chown -R yourusername: /media/yourmountpoint  # permissions actually set at mounting but this won't hurt anything
chmod -R 777 /media/yourmountpoint
sudo cp /etc/fstab /etc/fstab.backup
sudo blkid # with your usb device connected
gksudo gedit /etc/fstab

```

Add this line. Find the UUID from the previous command:
```

UUID=xxxxxx-xx /media/yourmountpoint vfat auto,users,uid=1000,umask=000,utf8 0 0

```
Save the file.
Mount the drive:
```

sudo mount -a

```

---

### Post by Frogbarf on 2008-11-23
Not to sound snarky about it, but why is all this complication necessary?

The contrast between how Hardy deals with my little digital camera (which "just works") and the hoops I have to jump through with this external drive...well, I just don't understand how two accessories so similar in function can result in such widely different behaviors by the system.

After all, they're both USB. I think the camera uses a FAT system, but I'm not sure.

I'll tell you what I think is actually happening (though this is a guess and violates my own dicta:)): the FAT errors that caused problems when I first used the drive have been noted in a configuration file somewhere and the system doesn't realize that those errors are gone now.

But that's just a guess. Bad me.

---

### Post by drs305 on 2008-11-23
A USB device *should* just work, I agree. Remember though that this is not a linux format and the problems may not have been generated by a linux process. Even so, I again agree it would be nice if it just worked. 

My previous post allows things to happen which you requested and are not necessarily the default:
1. Allowing any user to do anything to any of the files.
2. Always mounting it at a known location.
3. Not having to do a bunch of sudo-ing (at least after the initial setup)

---

