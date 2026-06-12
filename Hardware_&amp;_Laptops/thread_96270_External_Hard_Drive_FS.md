---
title: "External Hard Drive FS"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by fadumpt on 2005-11-28
If I were to get an external hard drive, what would be the best filesystem to put on it?  

Fat32 or VFAT seem to be the most compatible between Linux, OS X, and Windows (my target OS's for compatibility) but I'm not particulary fond of using FAT FS.

NTFS of course has limited write support nowadays so i don't want to trust my data on something that might be buggy depending on what computer it's on.

EXT3 has decent windows support as far as i know with e2fs program, so it's a consideration.  Is it compatible on OS X though?

Thanks for any ideas (or experiances)

---

### Post by aysiu on 2005-12-01
FAT32.
Why aren't you fond of it?

---

### Post by fadumpt on 2006-07-18
forgot all about this post :-/

because FAT32 is limited in it's capabilities and not exactly the best filesystem type for your data...even if you run Windows.

---

### Post by Blankman on 2006-07-20
I think this is the right place to put this query.  If not please excuse me; (1) I have just started using Linux and basically know how to find my way round the software (like open office, etc); (2) this is the first time I have used the forums and whilst searching for related issues came across this.  I know of the existence of the "terminal" and how to access it, but what it does I have no idea - I believe it has something to do with programing?!!  I'm the sort of person who turns on a computer and hopes that whatever I have just bought is compatible ... I have learnt the hard way with Linux having bought a Lexmark P6250 printer which I may as well use as a door stop!! As such anything technical really needs explanation on how to fix the problem.  

Query: I have just bought a Toshiba External Hard Drive 3.5" (whatever this means) (320 GB, 298 GB actual).  The computer identifies its existence as "New Volume" but when I try drag files or  copy the files from win_c it won't let me.  Error message reads: Error while copying to "/media/New Volume". You do not have permissions to write to this folder.  I believe this may have something to do with permissions or the hard drive needs formatting from ntls to Fat32, hence my thinking that this muight be the right place to post this query.  Can anyone help?

Thanks

---

### Post by fadumpt on 2006-07-20
first, the terminal is where you can manipulate the operating system in various ways.  It has programs that you can run to perform different functions, but they are of course in a text based or low-end gui format.  There are also commands that peform different tasks.  the terminal exists in all operating systems and is there to make life easier for you because some things are just better off being done in the command line as opposed to a GUI interface program if there is one.  there are programs for the terminal for programming, but that is only one thing you can do with it.

your probably right about the printer, linuxprinting says it's a paperweight as far as printing in linux goes.  sorry there.

3.5" is the size the drive.  3.5" is the standard size for desktop hard drives. 

NTFS has very limited read/write support in linux depending on your version.  The newer versions actually don't have an issue with it for the most part, but for compatibility across the board, you'll probably want to format it as fat32.

---

### Post by Blankman on 2006-07-21
Thanks for that, useful to know.

However, when I connect the hard drive to my laptop and icon "New Volume" appears acknowledging the existence of the hared drive.  But when I try drag files or save files or copy the files from my hard drive (on the computer win_c) it won't let me to any of these functions. A grey box with a no entry sign appears saying with an error message that reads: 

Error while copying to "/media/New Volume". You do not have permissions to write to this folder. 

Does this mean
(1) I have a permissions problem and if so how do I resolve it; or 
(2) the hard drive needs reformatting and if so how do I do this? I think it is currently formatted for ntfs.  Should this be converted to Fat32? 

Please excuse my ignorance on this, I simply do not know how to perform any of these functions.  I have ordered a copy of the new Ubuntu release and I am dreading teh installation process, but we live and learn.

---

### Post by fadumpt on 2006-07-21
I just recieved the same error on my Mac OS X formatted external drive.  Permissions.  it's entirely possible that if you go in windows with the drive and right click on it...select properties....and select the security tab, you might be able to give permission to everyone through that...it's a possibility.

not having permission could also be a generic response.

can you read data from the volume?

what version of ubuntu are you running?  6.06 won't be in your mailbox for awhile, but it might be able to write to NTFS.  If you want to try formatting it...in windows, you can right click on it, and there should be a format option in the menu that you can click and then select Fat32 format the drive.

---

