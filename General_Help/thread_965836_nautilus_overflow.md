---
title: "nautilus overflow?"
date: 2008-10-31
forum: General Help
---

### Post by ethoxyethaan on 2008-10-31
I have a folder containing 138,200 items, totalling 41.1 GB, (pictures), when i open the folder with 64 bit ubuntu there is no problem loading the folder. but when i try it on 32 ubuntu it fails Miserably.
(the reason i use 32 bit is for java and flash support).

Now i know that opening a folder containing 138K images is allot to ask for nautilus. But the reason i need it to open it is because i Have to manually split the images into 100 MB folders and upload them to my Server (without using archives).

i started writing a Bash script to do it for me but i simply can't find the right syntax to do it for me or can't find the needed documentation.

i did one small thing myself:
```
mv /place/*.png /otherplace/
```
and that moved about 10% of the images. but now i would like the other images moved out of there aswell,

Can someone help me out on this one :D?

---

### Post by ethoxyethaan on 2008-11-01
re-up and hope for the best :(.

---

### Post by nikgare on 2008-11-02
> (the reason i use 32 bit is for java and flash support).

64bit has java and flash support - why are you still using 32 bit?

---

### Post by ethoxyethaan on 2008-11-02
64 bit java uses the icetea plugin and it won't work for what i need it, Flash takes up 100% cpu on 64 bit because it uses the 32bit wrapper there is not 64 bit version available right now.

anyhow on topic:

this is how i temp solved it:

ls /directory/* > file.txt

then in python i did:

for the first 1000 lines in file.txt do:
print to file.sh >> "mv /directroty/"+ LINE +"/otherdirecotry/"

can someone please explain me how to do this without having to make a 40 MB .sh file and executing it.

---

### Post by Landara on 2008-11-03
138k images? You have either been to more weddings than anyone alive, or that's the most pr0n I've ever heard of being in the same place at the same time! ;)

---

### Post by geirha on 2008-11-07
This script should move the files into a different directory, one by one. When the directory exceeds 100MB, it creates a new directory and moves the next images to that directory. I haven't tested this, so try running it with the echo's I've marked in red. It should only print what it wants to do, but not move/create anything. If you're satisfied it looks correct, remove the parts marked in red.

```

#!/bin/bash

photodir=/directory
subdirbase="$photodir/sub"

# Start off with /directory/sub001
i=1
subdir="${subdirbase}`printf %03d $i`"

# Create the dir if it doesn't exist
[COLOR="Red"]echo [/COLOR]mkdir -v "$subdir" 

size=0

for photo in "$photodir"/*; do
  # skip processing "$photo" if it is not a file (e.g a directory)
  [ -f "$photo" ] || continue

  # Append the filesize of the photo
  size=$(( size + `stat -c %s "$photo"` ))
  
  # move the photo to the subdir.
  [COLOR="Red"]echo [/COLOR]mv -v "$photo" "$subdir/"

  # Check if we have exceeded 100MB
  if [ $size -ge 100000000 ]; then
    # Increment the counter and create a new subdir
    : $((i++))
    subdir="${subdirbase}`printf %03d $i`"
    [COLOR="Red"]echo [/COLOR]mkdir -v "$subdir"
    
    # Reset size
    size=0
  fi
done

```

---

### Post by jamesstansell on 2008-11-08
> 64 bit java uses the icetea plugin and it won't work for what i need it

If you don't mind getting off-topic again, I wonder if you are using the current icedtea6-plugin package in ubuntu 8.10 (intrepid)?  How does it fail for you?

---

### Post by jamesstansell on 2008-11-08
> for photo in "$photodir"/*

For 100k+ files that's asking a lot from a shell script.  Can it really handle that many files?

Otherwise the script looks pretty reasonable to me, for a quick-n-dirty job.

Some alternatives would be to set up an xargs recipe or a perl or python script, but if this script works then I won't bother puzzling out the others.

---

### Post by ethoxyethaan on 2008-11-13
Wow thanks for the replies, Ive been busy for a while and solved it with python but again thanks!.
Also its not Pornography but Images that i crawled from 2ch 4chan pinochan 7chan in the anime Sections. (using wget).

@ Jamesstansell, Icetea works, But has lower performance than the JDK plugin. (you might have noticed the link in my signature). I host a clan website and i'm one of the leaders and we play a **java Based Game**, JDK just gives better performance. (don't get me wrong id love to support icetea but i would also like to support my clan by playing once in a while.)

I wish the Icetea packagers/developers good luck :D.

---

