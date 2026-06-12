---
title: "Transmission - files reverted to 0%"
date: 2008-09-04
forum: General Help
---

### Post by evymetal on 2008-09-04
I've been downloading some huge data files with the bittorrent client transmission - I got a disk full issue, which was fine after I cleared some space, but now two of my downloads have gone to 0%.

The files are still on disk, and I can't click "verify local data".

I looked at ~/.config/transmission/resume/torrentname.resume, but I noticed that the file looks like this:

d7:corrupti0e11:destination17:/home/foo/Desktop3:[some serialised data]

... the point being that I hadn't been downloading the files to ~/Desktop, but rather a subfolder.


anyone got any ideas? It's taken a day or two to get this far so I really don't want to have to start from scratch (these are around 100Gb each and they're not being seeded well)

---

### Post by wolfen69 on 2008-09-04
go into transmissions settings and make sure the place where things will be downloaded to is where your files are. then it should see the files when transmission is restarted.

---

### Post by bingoUV on 2008-09-04
Copy the files to a new location (keep the same filenames). Stop the earlier torrent. Add the same torrent again (click on Add, select the torrent file). When transmission asks you where to download files from this torrent, tell it the new location. It should automatically start verifying local data, and after a while, start downloading parts that were not downloaded earlier.

---

### Post by evymetal on 2008-09-06
> **bingoUV said:**
> Copy the files to a new location (keep the same filenames). Stop the earlier torrent. Add the same torrent again (click on Add, select the torrent file). When transmission asks you where to download files from this torrent, tell it the new location. It should automatically start verifying local data, and after a while, start downloading parts that were not downloaded earlier.

Thanks - I'll give that a go - had tried editing the .resume file but that didn't seem to work.

---

