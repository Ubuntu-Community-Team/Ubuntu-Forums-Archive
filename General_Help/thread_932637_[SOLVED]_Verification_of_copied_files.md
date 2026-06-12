---
title: "[SOLVED] Verification of copied files?"
date: 2008-09-28
forum: General Help
---

### Post by GhentK on 2008-09-28
Hi all,

I'm backing up some of my files (in fact my entire /home partition). Last time I knew the cp command did not verify the integrity (I'm not at all sure that's the correct word) of the target files, unlike Windows' copy command with the V switch. Am I wrong? If not, is there a way to do so -- preferably as quickly as possible due to a possible imminent drive failure?

Thanks in advance. :)

---

### Post by The Cog on 2008-09-28
You can use **diff -r** to compare the directories after performing the copy.

---

### Post by jerome1232 on 2008-09-28
You could also tar it up with the -W flag to verify the archive.
example:

```

#tar [options] destination source
#c = create
#f = read/write to a file insteald of standard input/output
#W = verify integrity of the archive
tar cfW /destination/backupofhome.tar ~/
```

---

### Post by prshah on 2008-09-28
> **GhentK said:**
> Last time I knew the cp command did not verify the integrity of the target files, If not, is there a way to do so -- preferably as quickly as possible due to a possible imminent drive failure?


You should use rsync; it's almost as though this was built _for_ this situation.

Salient points:
[indent]1) rsync will copy only files that either don't exist or need to be updated on the target
2) rsync will only copy the "bits" (nothing to do with bit/byte) of the files are are chamged; eg, it will use a checksumming feature to figure out how to make the remote file "match" the current file. This will considerably speed up network transfers.
3) rsync will _automatically_ (no need for special switches) check the destination file for "integrity" to ensure that the copy has occurred successfully.
4) It can be used to transfer / archive / backup files either locally (same machine) or across the network.
[/indent]

That's the good part. The "bad" news is that both machines must have rsync installed and configured. It's very versatile, and by inference, complicated, but pretty simple to use if you do not want any advanced features.

There are too many options, so ```
man rsync
``` is the best place to start; or if you want to dive right in```
rsync -u * somemachine:somepath/
``` Replace machine names and paths as suitable, and look out for permissions!

---

### Post by GhentK on 2008-09-29
Thanks all for your ideas. :)

Rsync was the solution I went with in the end, but it's always nie to know several different approaches to this problem -- especially the archive may prove useful for me in some cases. :)

---

