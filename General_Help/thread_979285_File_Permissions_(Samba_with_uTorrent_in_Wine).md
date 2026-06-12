---
title: "File Permissions (Samba with uTorrent in Wine)"
date: 2008-11-11
forum: General Help
---

### Post by DemonWasp on 2008-11-11
I've got an Ubuntu server set up to allow my family to offload overnight and long-running activities to a single machine (to save money, electricity, and wear & tear on the hardware). As part of this, I'm running uTorrent in Wine.

Users should be able to add .torrents by copying them to a shared folder on the server (hosted via Samba), which uTorrent scans for new files. I have this working in one specific case: when the files are copied from a Win-XP computer that happens to have the same username and password as the account on the server that runs uTorrent. That is, uTorrent was run by "jordan" and the file is copied as:

-rwxr--r-- jordan jordan ...... (filename)

Since the uTorrent process is running as jordan, it can read that file and remove it (starting the download along the way.

Whenever anybody else tries it, however, the file appears as:
-rwxr--r-- nobody nogroup ...... (filename)

Since the uTorrent process can't write the file, the torrent is not started. This is the problem. I've discovered that if I run:
sudo chmod o+w (filename)
then uTorrent instantly picks up the file, but I can't be running that every day.

I can think of more than a few hackish solutions to this, such as having a cron job to do the chmod above every 5 minutes or so, but I'd prefer something a little more elegant.

For those who are wondering, samba runs as a service on the machine, while uTorrent is started as follows:
1. The jordan account automatically logs in.
2. Under System->Preferences->Sessions, I have a startup command:
wine "/home/jordan/.wine/drive_c/Program Files/uTorrent/uTorrent.exe"

Is there a better way to start uTorrent (e.g. so that it runs as root and can therefore read those files)?
Is there a hidden option in Samba to write guest (non-authenticated) files with a different set of permissions?

---

### Post by DemonWasp on 2008-11-12
SOLVED:

One of my friends happened to have a similar setup, and he advised me of the following solution:

1. Using system-config-samba, go Preferences -> Server Settings.
2. In the security tab, change Authentication Type to "Share" and set the Guest Account to whatever account you wish (I chose "jordan").
3. Done! Now others can copy in files all they want, and they appear as:

-rwxr--r-- jordan jordan ..... (filename)

and are immediately consumed by uTorrent.

---

### Post by dreamie on 2009-03-29
Hi!

I have a similar problem but I don't want to change my samba permission settings to a specific account (if possible).

Wouldn't it be possible to add Jordan (or whatever account you logon to the serve with) to the nogroup-group, so he could access the folders and files?

I have a folder structure that I want to be accessible from Windows (using samba), through ftp ,and of course locally by the account logged on to the server (downloading files using a bittorrent client). I thought nogroup:nobody was a good solution for this, but the locally logged on user don't have any write permissions to the folders...

Can I add an account to the nogroup group? How is this done (can't find where this is done).

/ PH

---

