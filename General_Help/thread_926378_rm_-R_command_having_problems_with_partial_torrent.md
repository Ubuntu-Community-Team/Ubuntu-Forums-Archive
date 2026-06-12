---
title: "rm -R command having problems with partial torrent files"
date: 2008-09-21
forum: General Help
---

### Post by bluepowder7 on 2008-09-21
so i was downloading some files using transmission, and something weird happened.  first, trans seized, so i had to kill it.  restarted, and it went through the file checking stuff.  i aborted that and removed all the torrent entries, and closed trans.  then i went to the drive (which is actually on my file server) to blow away the partially-downloaded files - but i can't!  i'm ssh'ing over to the file server, and using terminal typing **rm -R Directory_Name** for the directory that i wanna blow away.  no dice.  it just sits there, and freezes.  minutes go by, and i can't even Ctrl-C out of it.

if i then close and restart the terminal and make my way over to the same place, and i do a **cd Directory_Name**, it works, but if i then do **ls**, it freezes again.

how do i fix this?  oh, this is all using 7.04 Server.

---

### Post by ju2wheels on 2008-09-21
Are you sure you killed the actual Transmission process and not just the window?

Run this to see if transmission is still running:
```

ps aux | grep transmission

```

Before you delete those files you should always make sure you completely terminate the process thats using them...

---

### Post by bluepowder7 on 2008-09-21
well, i've killed transmission and rebooted both the desktop pc and the file server before doing all that, so yeah it's no longer running.  i think.

your command tells me:
```

greg      6587  0.0  0.0   5164   844 pts/0    R+   22:54   0:00 grep transmission

```

wait - does that mean it's STILL running?  i assume the 0.0 0.0 ad 0:00 mean that it's not running anymore.

---

### Post by Mister.Vash on 2008-09-22
You may have too many files in the folder ( 10,000 to millions )  so it's being slow and may eventually error out on the command.

change the directory_name that holds all the files, and try starting with
ls 1*
ls a*

and give them a few minutes to process.  The more files that you have in a folder, the longer if take for file operations

---

### Post by bluepowder7 on 2008-09-22
well, i don't have thousands of files in the directory so that shouldn't be an issue.  i mean, overall on the hard drive, yes i could have a few thousand, but not millions - but they're in folders and subfolders, so at any given level i wouldn't expect more than 500 files.

ok, so at the top level, if i do **ls**, it USUALLY works and shows me the 15-20 files and folders there.  5 of them i want to blow away, and let's call them SSP2 to SSP6.  somehow, i managed to **rm -R** SSP1 without issues.  just now, i also managed to get SSP4 to get **rm**'d, so i'm down to 4 folders.  i did **rm -Rf SSP3** about an hour ago, and it's still stuck doing it.

maybe i need to do **rm -Rfv** to get it verbose and tell you what it's saying along the way?  would that help?

in any case, the SSP2 to SSP6 folders don't have more than 10 files each, but they are all interrupted torrents, so maybe the files didn't get closed properly and even a reboot didn't "fix" that.  would running a **fsck** possibly fix a thing or two?

---

### Post by bluepowder7 on 2008-10-03
ok, evidently all i needed was time.  lots of it.  took at least an hour to **rm -Rf** each folder, and they were all less than 2G each.  something went wonky on my system.  again.  i mean, again as in just like a few months ago.

---

