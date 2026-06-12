---
title: "Help attaching running screen"
date: 2008-09-28
forum: General Help
---

### Post by victorbrca on 2008-09-28
I have a little script that takes a list of torrent files in a folder and opens a new screen with ctorrent for each of those files (max of 3).

I wanted to write another script that would create a new screen, split it in 3 and attach to those running screens. I have not clue where to start of if that's even possible. Any ideas?

This is my script:

```
$ cat run_tor
#!/bin/bash

## Last edit: Set the folder for download - 2008-08-31

_tor=0
_port=( 10 11 12 )

_tor2=`ls $HOME/downloads/tor/*.torrent | tail -n 3`

for i in $_tor2 ; do
	cd $HOME/downloads/tor
	/usr/bin/screen -d -m /usr/bin/ctorrent $i -p ${_port[_tor]}
	_tor=$(( _tor + 1 ))
done

```


Thanks!

Vic.

---

