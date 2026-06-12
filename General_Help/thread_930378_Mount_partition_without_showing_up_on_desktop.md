---
title: "Mount partition without showing up on desktop"
date: 2008-09-26
forum: General Help
---

### Post by sirlancelot on 2008-09-26
Hi,

I'm making a script to mount/unmount an encrypted partition (truecrypt if it matters). I'd like to have the partition be mounted as invisible as possible.

Is there a way to mount a truecrypt partition and NOT have it show up on the desktop? I'm picking a custom mountpoint outside of /media/* but it's still showing up on the desktop :-/

I still want other partitions & media to show up on the desktop, just this specific partition.

Thanks for any help! Here's the script I made:```
#!/bin/sh

VOLUME=/dev/sdb2
MOUNTPOINT=~/.Private

getCryptainer () {
	CRYPTAINER=`truecrypt -t -l 2> /dev/null | grep $VOLUME | awk '{print $3}'`
}

# See if we're mounted
getCryptainer
if [ -z $CRYPTAINER ]; then
	truecrypt --filesystem=none $VOLUME
else
	zenity --question --text="Unmount device?"
	RESPONSE=$?
	if [ $RESPONSE -eq 0 ]; then
		umount $MOUNTPOINT
		truecrypt -d
	fi
	return 0
fi

getCryptainer
if [ $CRYPTAINER ]; then
	mkdir -p $MOUNTPOINT
	mount -n $CRYPTAINER $MOUNTPOINT

	# Background task is supposed to protect certain things
	truecrypt --background-task &
else
	zenity --error --text="Error while mounting partition."
fi

```

---

