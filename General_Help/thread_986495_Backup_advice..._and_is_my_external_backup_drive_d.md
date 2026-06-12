---
title: "Backup advice... and is my external backup drive dying?"
date: 2008-11-18
forum: General Help
---

### Post by skullmunky on 2008-11-18
Here's my situation:

I have a 500GB home drive and a 500GB external.  In a rush a few months ago I did a super-simple backup, just cp -a.  Now I'd like to get into a better backup routine.  I'm looking at Keep and KDar, because I'm using KDE; also rdiff-backup and of course rsync.

I'd like to amend the existing backup instead of starting over from scratch if possible.  

KDar looks like it only archives into its own backup file format; is that right? 

I looked at Keep, but I've seen some posts on the KDE-Apps page from people complaining about the daemon going haywire and doing things like trying to back up even if the external drive isn't attached, thus filling up the whole root filesystem.  

I then tried rdiff-backup, but since the original backup was not made with rdiff-backup it warned me not to try to back up to that location.  If I go ahead and force it, will it intelligently produce diffs based on the existing files or will it potentially kill my whole existing backup?

Now here's the really important question.  I decided to just go with trusty rsync; I'm not too worried about keeping incremental revisions anyway.  It went ok for a while, but halfway through started spewing tons of errors of the form:

```

rsync: mkstemp xxxxxxxxx failed: Read-only file system (30)

```

I'll get batches of these and then it continues on its merry way.  But I can't tell if it's really continuing, because while it lists the files it's looking at, the majority are unchanged.  Some new files have appeared, so I know the disk wasn't read only.  

Then I looked at dmesg, and there's tons of these:

```

[ 1060.359449] usb 2-7: reset high speed USB device using ehci_hcd and address 4
[ 1060.419747] sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1060.419754] end_request: I/O error, dev sdc, sector 922887

```

Do I understand this right, that there's an I/O error, making the external drive get remounted read only?  Is my external drive, my supposed backup, which has only been powered on about a dozen times total, actually dying?  Or could it be something else like a poor USB cable?

If your backup drive is likely to just die on its own while sitting peacefully on the shelf for six months, what hope do we have?   

Is there a rueful grin emoticon to express the acceptance of the fundamental cruelty of the universe, and the futility of mere mortals attempting to struggle against its capricious whims?

---

### Post by whitegourd on 2008-11-18
I don't think it's anything wrong w/ your external drive.  I had those errors happen to me too.  Found out that I wasn't using the -R option in rsync.  If you don't use the -R option, it won't create the relative paths that you're backing up onto the destination location (your external drive).

#example
rsync -avR /dir/file /destination/bkup

Hope that helps.

---

### Post by skullmunky on 2008-11-19
Awesome, I'll try that out!  I didn't use -R, only -r.

---

