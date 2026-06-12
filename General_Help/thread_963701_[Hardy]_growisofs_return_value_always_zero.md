---
title: "[Hardy] growisofs return value always zero?"
date: 2008-10-30
forum: General Help
---

### Post by vof on 2008-10-30
Apologies if this is in the wrong forum.

I have a shell script which produces a server backup DVD if a blank DVD-R is left in the drive overnight. It used to work well on dapper but has various problems on hardy.

On dapper, I used mkisofs/cdrecord and they returned values depending on whether the iso/DVD creation activities were successful. In particular, I could tell whether a disk had been successfully written so then ejected the disk ready to be removed the following day.

On hardy, I must now use growisofs which seems to return a zero value whether or not the drive contains writable media. This may be because growisofs appears to spawn an independent genisoimage process which runs asynchronously as a result of which growisofs appears to terminate before genisoimage completes. The script therefore always believes a DVD has been successfully created and thus ejects it. Unfortunately, the genisoimage process has not completed by then so the disk is immediately reloaded before it is eventually written successfully (most of the time).

Has anyone else seen these effects and have any thoughts about how to use growisofs effectively in a script such as mine?

vof

---

