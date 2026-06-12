---
title: "Setting up syncing with laptop and desktop"
date: 2008-10-05
forum: General Help
---

### Post by mattgaunt on 2008-10-05
Heya

I'm planning on using Ubuntu on my laptop and desktop for university work, but I would like some sort of way of doing work on my desktop, then have it on my laptop for when I go to University, so then between lectures and when doing work away from home (Meetings for group projects) I can work on the latest version on my desktop and then when I get home have it update the stuff on my desktop with the new stuff from my laptop.

Is there anyway I can achieve this? Both desktop and laptop will be running linux.

I dont really want to use something like ssh as I would like to leave my desktop off while I'm out, any help would be great

---

### Post by unutbu on 2008-10-05
Suppose the data is in a directory called ~/Documents:

To copy laptop data to the desktop, run on the laptop:
```
rsync -a --delete ~/Documents/ user@desktop:Documents
```

To copy desktop data to the laptop, run on the desktop:```

rsync -a --delete ~/Documents/ user@laptop:Documents

```
The -a flag means "archive mode"
--delete means "delete files in the destination directory which are not in the source directory"

The format of the rsync command is 
```

       rsync [OPTION] SOURCE DESTINATION
```

Especially because of the --delete flag, it would behoove you to try this on a test directory before taking it prime time.

---

### Post by mattgaunt on 2008-10-05
Thats pretty much what I'm looking for thank you, and I'll take your advice and have my own manual archives etc alongside rsync to see how I get along.

I assume there is no way to make this automatically sync when the laptop and desktop are both on the network?

Just thought I'd throw it out there lol

But thank you for your help ill give it a ago :-)

---

### Post by unutbu on 2008-10-05
It is possible to modify the rsync command so that it runs once every 15 minutes (or any other amount of time you desire).
[B]
On the desktop:[/B]

Save this in a file called d2l
```

#!/bin/bash
watch -n 900 rsync -a --delete ~/Documents/ user@laptop:Documents/
```

"watch -n 900" means run whatever follows once every 900 seconds (15 minutes).

And save this in a file called l2d
```

#!/bin/bash
watch -n 900 rsync -a --delete user@laptop:Documents/ ~/Documents/

```
[B]
On the laptop:[/B]

Save this in a file called d2l
```

#!/bin/bash
watch -n 900 rsync -a --delete user@desktop:Documents/ ~/Documents/ 

```
And save this in a file called l2d
```

#!/bin/bash
watch -n 900 rsync -a --delete ~/Documents/ user@desktop:Documents/

```
Make all 4 scripts executable:
```

chmod +x d2l l2d

```
Now make launchers for the scripts:

Right-click on the root (empty background) window.
Select "Create Launcher"
For the Command, type in the path to the d2l or l2d script. 
Make d2l and l2d launchers for the desktop and the laptop.

Then when you have both connected to the network, you can simply click on the appropriate icon, on either laptop or the desktop and the rsync'ing will happen behind the scenes without you having to do anything.

By the way, rsync is pretty smart about not copying things when it doesn't have to (from the rsync man page):
> 
       The  rsync  remote-update protocol allows rsync to transfer just the differences
       between two sets of files across the  network  connection,  using  an  efficient
       checksum-search  algorithm  described  in  the technical report that accompanies
       this package.

---

### Post by mattgaunt on 2008-10-05
Thank you soo much for help, greatly appreciated!!

Ill have a go with it all:)

---

