---
title: "Overwrite tapes attached to a SCSI device."
date: 2008-11-20
forum: General Help
---

### Post by x C0MMAND0 x on 2008-11-20
So here's the deal.  I have a big box of tapes I am trying to overwrite.  The tape device is attached to my computer, and shows up.  I am able to detect the tape device (/dev/tape/biglongcode).  I have tried the following commands.

```
cat /dev/random > /dev/tape/biglongcode
```

```
cp /dev/random /dev/tape/biglongcode
```

Neither of which have worked.  I did some research and it appears the **fms** command will work ([click here for link]("http://manpages.ubuntu.com/manpages/intrepid/man8/fms.html")), but I am not able to get it to install in 8.1

Any suggestions or solutions to this problem?

---

