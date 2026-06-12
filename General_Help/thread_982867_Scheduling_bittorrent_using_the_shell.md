---
title: "Scheduling bittorrent using the shell"
date: 2008-11-15
forum: General Help
---

### Post by chrismyers on 2008-11-15
A script to schedule nightly bittorrent downloads using the shell.

I needed this, because my Internet service provider limits my downloads outside the hours of midnight & 8:00.

The following script will start/stop bittorrent downloads nightly until the download is complete.

First we need bittorrent:

```
sudo apt-get install bittorrent
```create a directory in your home folder & change directory into it:

```
mkdir ~/torrents ; cd ~/torrents
```create the following files:

```
touch schedule.sh ; touch reschedule.sh
```make them executable:

```
chmod +x schedule.sh ; chmod +x reschedule.sh
```Edit schedule.sh & paste the following:

```
#!/bin/sh
echo "btlaunchmany ~/torrents > ~/torrents/torrent.log" | at midnight
echo ~/torrents/reschedule.sh | at 8:00
```*Note: Use your own time for starting/stopping.*

Edit reschedule.sh & paste the following:

```
#!/bin/sh
killall btlaunchmany
if grep 100% ~/torrents/torrent.log > /dev/null
then
echo "Torrent has completed." | mailx -s "Torrent Complete" you@you.com
else
~/torrents/schedule.sh
fi
```*Note: The 'Torrent is completed' email line is optional & will only work if mailx is configured.*

Now you can drop your .torrent file into the torrents directory & to start, run:

```
~/torrents/schedule.sh
```*Note: This script has only been tested for a single bittorrent download at a time.*

I hope this helps someone.

:)

---

