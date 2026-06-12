---
title: "about decompression"
date: 2009-09-27
forum: Hardware
---

### Post by replikanxxl on 2009-09-27
hey people , im new around . just a question bugged my mind so i wanted to share . and im too lazy to make a test :D 

while decompressing a file , if u extract it to another hard drive , so not the source drive , would it mean less travel of harddrive heads so it improves timing ? or is there already some special algorithms embedded in the disk controllers for this ?

---

### Post by replikanxxl on 2009-10-28
what a forum :D no ideas  , its been months

---

### Post by bribera on 2009-10-28
Heh.

Yes, that's theoretically sound. If you have one drive performing all of the reads and the other performing all of the writes, it should boost speed somewhat.

This is a similar idea to the performance tuning you see in [some database systems]("http://www.linuxjournal.com/article/4791") that moves logging to a separate drive to reduce head movement.

But be sure it's a separate drive, not merely a different partition. ;)

---

### Post by replikanxxl on 2009-12-16
ah yes . as we are social creatures , having someone agree is a lot more important than knowing its true :D thank you . yes i was talking about seperate devices. nice day !

---

