---
title: "grep bash error"
date: 2008-09-07
forum: General Help
---

### Post by dsbeav on 2008-09-07
I'm working on a bash script to backup to an External hard drive.
I want to make sure that is, mounted before I start backing up. 

SCRIPT:

#!/bin/bash

EX_HD='/media/EXTERNAL fuseblk'
cat /etc/mtab | grep "'$EX_HD'" >> /dev/null
if [ "$?" != 0 ]
then
echo External hard drive $EX_HD is not mounted; echo Exiting.; exit
fi

This part of the script always fails.

If from the command prompt I run:
%echo "'$EX_HD'" 
I get -> '/media/EXTERNAL fuseblk'

When I cut and paste '/media/EXTERNAL fuseblk' and run
%cat /etc/mtab | grep 'media/EXTERNAL fuseblk' 
it returns the true.

What am I doing wrong?

Thanks!

---

### Post by Mister.Vash on 2008-09-08
Try this
```

#!/bin/bash

EX_HD='/media/EXTERNAL fuseblk'
cat /etc/mtab | grep "$EX_HD" >> /dev/null
if [ "$?" != 0 ]
then
echo External hard drive $EX_HD is not mounted; echo Exiting.; exit
fi

```

The "'$EX_HD'" has been changed to "$EX_HD"

---

