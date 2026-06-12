---
title: "Questions about shared /home partition between XP and Ubuntu..."
date: 2008-11-03
forum: General Help
---

### Post by Wally_dog on 2008-11-03
Hi all ):P

I just installed Windows XP on my hard drive along with Ubuntu. Since I wanted to share files between the two easily, I moved my /home to it's own partition that is formatted as NTFS so it can have read/write support between Ubuntu and Windows. Now, everything is fine, except for some minor annoyances. First, the Windows files have moved over onto my Ubuntu desktop, such as Desktop.ini and Thumbs.db, and I would like those to be hidden so I don't see them everytime, and I know deleting them would cause problems in Windows. I tried adding the "." in front, but soon realized that that would affect Windows. Is there any way they can be hidden or atleast modified so they aren't apparent in Ubuntu?

---

### Post by dcstar on 2008-11-04
> **Wally_dog said:**
> Hi all ):P

I just installed Windows XP on my hard drive along with Ubuntu. Since I wanted to share files between the two easily, I moved my /home to it's own partition that is formatted as NTFS so it can have read/write support between Ubuntu and Windows. Now, everything is fine, except for some minor annoyances. First, the Windows files have moved over onto my Ubuntu desktop, such as Desktop.ini and Thumbs.db, and I would like those to be hidden so I don't see them everytime, and I know deleting them would cause problems in Windows. I tried adding the "." in front, but soon realized that that would affect Windows. Is there any way they can be hidden or atleast modified so they aren't apparent in Ubuntu?

You should **not** have /home on a non-Linux filesystem. Many things depend on security settings that only native Linux filesystem can provide.

If you want shared partitions, then set them up separately and do not touch system created resources.

---

### Post by Wally_dog on 2008-11-04
Well see the thing is, I have the Windows partition at 6GB, and the Linux partition as 10GB. I need to have the giant shared partition to store my files between the two OS's. If I shouldn't use NTFS, then what should I use? FAT32? I heard that FAT32 was a very bad filesystem format, so I naturally went with NTFS. And keep in mind the format can't be a format that can't be detected by Windows, because I will have to move the My Documents folder over to the partition.

Thanks

---

### Post by snowpine on 2008-11-04
You should create a separate NTFS partition for sharing data with Windows, apart from your Linux /home partition. You don't need to put your shared files in /home, but you definitely need to have a safe and secure /home for the program configuration files that are stored in it.

---

### Post by Wally_dog on 2008-11-04
Oh, ok I get what you mean. So basically you're saying move only the documents/videos/music/pictures etc. to the shared NTFS partition, but keep the /home partition in ext3. That clears things up a bit. Now my only question: How do I move my /home folder back to the main Ubuntu partition so that I can format the old home partition (one home is on right now) with ext3?

---

### Post by jdackle on 2008-11-04
Well... 
First of all, if you still want to share a folder between Ubuntu and Windows (say "Documents") you have to leave that folder as NTFS...

You would then move all non-documents AND all non-windows-system files and folders from that shared-home partition to a home folder on Ubuntu (say /home/wally_dog). This would be setup as the new home-folder in Ubuntu.
When that's done, the /home/wally_dog/Documents should be mounted to point at the shared-documents partition.

This is basically the easiest way to do it, I guess. 
I'll be doing the same soon (after I install Ubuntu) but I'm still considering the choices on that. Using symlinks is one. Hardlinks I think cannot be on a non Linux-native fs, so no way there (unless you can... lol).
Also, I may want to share other stuff beyond my documents: Firefox profile, MAIL FOLDER, GIMP profile maybe, ...

Also, there is the Images, Music and Video folders... These are separate folders in Ubuntu (8.04 at least, haven't tried 8.10 yet) but really are shortcuts in Windows.
The problem in this scenario is that you would have different partitions to be mounted for each, for Ubuntu. And this would boggle Windows.
The best here would be to "transform" these Ubuntu folders (Images, etc) into symlinks pointing at corresponding folders *inside* the Ubuntu Documents folder (which I have done in 8.04 without even sharing anything in Windows which was broken beyond repair).

Hope that helped! :lolflag:

---

### Post by jdackle on 2008-11-04
Hey Wally_dog, you may be interested in the following topic:
[http://ubuntuforums.org/showthread.php?t=469666](http://ubuntuforums.org/showthread.php?t=469666)

It does not completely setup the sharing (namely what precautions you should have concerning security et al) but gives a couple very easy ways to both access files in Windows from Linux AND (this I app did not know) to access files in Linux from Windows!

Now I'm not to sure about that latest part - it's like opening the door of the secure linux to the unsafe windows...
Specially bear in mind that file permissions (i.e. user/group ownership) is NOT kept with that program! I.e. it's like any user at all in Windows got more access to your files and folders on Linux than say another user in your Linux install!
You can, apparently, set it up so as to only provide access to a given folder on the ext2/3 partition but I believe any user on your Windows will get that access.
NEVER assign a Windows letter (H:, I:, ...) to your Linux root-folder: /
Do read the program's FAQ before you proceed. I myself will most likely play it safer.

Cheers!

---

