---
title: "Error: splicing file Input/output error while copying to external HDD"
date: 2012-01-31
forum: Hardware
---

### Post by gattz on 2012-01-31
Every once and awhile I get this error while trying to copy things over to an external HDD. It's only certain (very few) files, but they won't copy to either of my externals. They always get hung up at the same point too. The files are varying in size too, and it's always video files. I don't think it's an issue of the drives being corrupt, because they work fine otherwise.

Any tips on this? It's driving me mad and it's really important that I have these files backed up.

---

### Post by gattz on 2012-01-31
Desperation bump.

---

### Post by BitRogue on 2012-02-02
I have no idea if this is relevant, but last month I had similar symptoms. I had formatted my external drive to NTFS using the quick format (in an XP VM). Later in Ubuntu I was trying to copy video files and they ended up getting IO errors or hard drive full errors (but it clearly wasnt).

In the end, I booted up in Win7, gave the drive a proper full format and that sorted it out.

---

### Post by gattz on 2012-02-04
I don't have access to Windows so that would be difficult for me to do. I did format the drive before using it in Ubuntu though. Thanks for a reply though.

After searching through countless threads the only solution I ever came by was to go through a USB hub. I went out and bought one, and the problem still occurs... ANY clues on this? It's really frustrating.

---

### Post by BitRogue on 2012-02-07
Three things come to mind

1. When you formatted it before using Ubuntu - what file system did you format it to? If you are usign FAT, you may hit an issue with copying files greater the 2GB, which some HD movies tend to be.
Also, something Im not too sure about - if you use quick format, I don't know how good Linux's ability to grow FAT and NTFS systems on the fly are and may produce IO errors (re my previous post).

2. Is it possible to format it again using Ubuntu - ext4 probably the best all-rounder at the moment.

3. Does running fsck on the disk report anything unusual?

Just some thoughts. 
Good luck.

---

### Post by mikevikki on 2012-07-31
I had this issue and fixed it as follows (please note data on the drive will be lost):-

1. Start your PC
2. Plug in the external USA or other external drive.
3. Goto Linux disk utility
4. Locate the relevant USB normally near the bottom on the left.
5. Make sure the drive is not mounted. If it is press the unmouth button
6. Press the format button just above the big bar that represents the drive.
7. From the drop down select "dont partition" and press ok.
8. When 7 is done press the format button below the big bar representing the drive.
9. Select NTFS and press format.
10. Remount the drive by pressing the Mount Button.

Note FAT formats will only support files upto 4Gig

NTFS is best as external drives can then be read by either Linux or windows. For me EXT4 on USB drives never seems to work as it creates the Lost+Found on the external drive. I think (i dont know) that linux thinks your external drive is internal.

Hope this helps let me know.

---

