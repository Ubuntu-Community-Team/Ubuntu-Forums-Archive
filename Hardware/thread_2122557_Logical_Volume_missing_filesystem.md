---
title: "Logical Volume missing filesystem"
date: 2013-03-05
forum: Hardware
---

### Post by kermtfrg on 2013-03-05
[COLOR=#000000][FONT=Arial]Using Ubuntu 12 server, I have 5 partitions totaling around 9TB that are in lvm2 format. These are part of the volume group mediaserver and the logical volume /dev/mediaserver/homeserver. The LV status is "NOT available". I tried to mount it and get[/FONT][/COLOR]
```

root@mediaserver:/home/jon# mount /dev/mediaserver/homeserver 
/mediamount: you must specify the filesystem type
```[COLOR=#000000][FONT=Arial]I'm at a loss of what to try. All I want is to get the data that is on those drives (about 4TB's) and then I don't mind reinstalling the server. They are all external drives and I can take them to another Ubuntu computer. Is it possible to hook them up one at a time on another computer and get to the data?[/FONT][/COLOR]

---

