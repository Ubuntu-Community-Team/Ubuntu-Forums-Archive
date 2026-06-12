---
title: "Syncing with tomboy usint Private directory"
date: 2008-10-28
forum: General Help
---

### Post by silux on 2008-10-28
I am using Ibex beta and have my .tomboy directory in the ubuntu Private directory with a symlink pointing .tomboy -> ~/Private/.tomboy.

When I sync my notes sync successfully and an icon appears on my desktop called sync-sshfs.  I can't sync after the initial try and I can't unmount without sudoing in order to do it.

If I run:
> sudo umount ~/.tomboy/sync-sshfs 

then I can sync again.  My .tomboy.log file has the following error messages which lead me to believe that tomboy/fuse is having a problem unmounting because of the symlink...

The only errors I see in .tomboy.log are:

> 
10/28/2008 10:33:08 PM [DEBUG]: Error calling /usr/bin/sshfs
10/28/2008 10:33:08 PM [DEBUG]: Exception while creating SyncServer: An error ocurred while connecting to the specified server:

fusermount: failed to access mountpoint /home/olsenm/Private/.tomboy/sync-sshfs: Permission denied

  at Tomboy.Sync.FuseSyncServiceAddin.MountFuse (Boolean useStoredValues) [0x00000] 
  at Tomboy.Sync.FuseSyncServiceAddin.CreateSyncServer () [0x00000] 
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] 

10/28/2008 10:50:40 PM [DEBUG]: Mounting sync path with this command: /usr/bin/sshfs -p 22 [email]myuser@vegangeek.info[/email]:tomboy_sync /home/olsenm/.tomboy/sync-sshfs
10/28/2008 10:50:41 PM [DEBUG]: Error calling /usr/bin/sshfs
10/28/2008 10:50:41 PM [DEBUG]: Exception while creating SyncServer: An error ocurred while connecting to the specified server:

fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

  at Tomboy.Sync.FuseSyncServiceAddin.MountFuse (Boolean useStoredValues) [0x00000] 
  at Tomboy.Sync.FuseSyncServiceAddin.CreateSyncServer () [0x00000] 
  at Tomboy.Sync.SyncManager.SynchronizationThread () [0x00000] 



Permissions on the sync dir are:

> 
drwxr-xr-x 1 olsenm olsenm 4096 2008-10-28 22:52 sync-sshfs


---

