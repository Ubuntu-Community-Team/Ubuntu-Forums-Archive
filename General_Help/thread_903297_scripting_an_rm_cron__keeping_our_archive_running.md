---
title: "scripting an rm cron | keeping our archive running"
date: 2008-08-28
forum: General Help
---

### Post by nlz on 2008-08-28
for the archive of our radiostation, we have a script that automatically captures the audio from our soundcard and writes it in one hour chunks to /media/disk/log (in this proces, they are also timestamped/fingerprinted with the date and time).

Now we want to create a script that is used as a cron that should check every hour if there is at least 300 MB of free space left on /media/disk, andif not, delete the oldest file from /media/disk/log. 

Can someone help us out with this short and simple script? 

(PS If someone (radio station or something) is interested in our script for archiving, just post it here, we'll email it to you)

---

### Post by strider1551 on 2008-08-31
Well, I'm normally a python guy, but here is a bash script that should do the job.  I assume that "/media/disk/log" is a directory with the files you may or may not want deleted in it.

```

#!/bin/bash

DIR=/media/disk/log
SPACE=`df ${DIR} | awk '{print $4}' | tail -n 1`

cd ${DIR}
if [ ${SPACE} -lt 307200 ]
then
  #echo ${DIR}
  #echo ${SPACE}
  #echo $(ls -tr | head -n 1)
  rm $(ls -tr | head -n 1)
fi

```

Toss it wherever you will, make it executable (chmod +x file), and set up your cronjob.  Test it out manually a few times first, though, if this is a production environment.  Uncomment those lines ("#echo" => "echo") if you want some feedback when there is something to remove.

---

### Post by nlz on 2008-09-04
> **strider1551 said:**
> Well, I'm normally a python guy, but here is a bash script that should do the job.  I assume that "/media/disk/log" is a directory with the files you may or may not want deleted in it.

```

#!/bin/bash

DIR=/media/disk/log
SPACE=`df ${DIR} | awk '{print $4}' | tail -n 1`

cd ${DIR}
if [ ${SPACE} -lt 307200 ]
then
  #echo ${DIR}
  #echo ${SPACE}
  #echo $(ls -tr | head -n 1)
  rm $(ls -tr | head -n 1)
fi

```

Toss it wherever you will, make it executable (chmod +x file), and set up your cronjob.  Test it out manually a few times first, though, if this is a production environment.  Uncomment those lines ("#echo" => "echo") if you want some feedback when there is something to remove.

WOW! Thanks a lot! We'll be playing with this until we understand exactly what the script is doing. Thanks! We're very grateful!

---

