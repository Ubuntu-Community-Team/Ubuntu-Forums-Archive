---
title: "Automatic torrent script"
date: 2008-09-17
forum: General Help
---

### Post by van_Zeller on 2008-09-17
Hello all,

I'm trying to make a script that, when run, checks a directory for files with the .torrent extension and if they exist, adds them to transmission and moves them to another directory. I'm a beginner in coding, so how about this:

```
locate *.torrent
```

now all I need to do is to call Transmission with the previous output as argument. Right? I have been reading all over the web about pipes (the | symbol) but I still cant...

Thanks

---

### Post by justleen on 2008-09-17
i'd probably use something like
```

#!/bin/bash

for torrents in `find /home/leen/Desktop -name "*.torrent"`; do
       transmission $torrents     # start the torrent, not sure if this works
       rm $torrents               # remove the torrent file, since its copied to the  
                                  # temp dir og transmission
done

```

mind you, make sure it doenst find any files in the temp dir of tranmission!

the pipes work quite well for redirecting output, put you can only do 1 thing at a time. with a "FOR things IN whatever"  you can do more actions on the found items..

basic syntax 
[code]
FOR variablename IN  sequence; DO
      do stuff
      more stuff
DONE
[code]

as sequence you can you the output a command. bash will inteper anything between `` as a command.
thus, "for files in `ls -1`"  will do something for all listed files

---

### Post by 505 on 2008-09-17
You can use the command 'xargs' for that, together with a pipe. The code would then be
```
locate *.torrent | xargs transmission
```
What is does is add each line of output from the first command as an argument to the second command. So, if "transmission /path/file.torrent" is valid for adding the torrent, it will work. You might need some extra arguments behinds the torrent command, though.

Just a tip, I often use the torrent client rtorrent. It is completely console based, but it supports watch directories, meaning that it will automatically add each torrent that is placed in a certain directory.

---

### Post by hyper_ch on 2008-09-17
rtorrent has watch folders included... maybe transmission has also.

---

