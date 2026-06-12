---
title: "Bash: run at most 4 instances of script"
date: 2008-10-21
forum: General Help
---

### Post by Breepee on 2008-10-21
I've got a script that convert video's to a format that I can put on my iPod. I use ffmpeg, and I pass the option -threads 4 (I have a quadcore cpu), but it still only uses 2 cpu's. Now, I was thinking of modifying my script to that it actually runs 4 instances of ffmpeg. How can I do this, when passing a list of files (the adress of a directory actually) to run, at most, 4 instances of my script?

---

### Post by geirha on 2008-10-21
Not sure I understand exactly what you mean, but maybe this may help.

Assuming you have a script, /path/to/convert-script, that take a video file as argument and convert it to some ipod format, and assuming the arguments to this script are any number of video files, something like this should start four instances of the convert script, then wait till one of them completes, and start a new one, keeping maximum 4 running at any given time.

```

#!/bin/bash

# function that loops until there are less than num commands running
wait_for_less_than () # num command
{
  local pids=( $(pidof "$2") )
  while [ ${#pids[@]} -ge $1 ]; do
    sleep 10
    pids=( $(pidof "$2") )
  done
}

for file in "$@"; do
  /path/to/convert-script "$file" &
  wait_for_less_than 4 /path/to/convert-script
done

```

---

### Post by Breepee on 2008-10-22
Thanks, but it wouldn't quite work yet.

What I have is a script that converts all video's in a certain folder. If I'd run that script multiple times, I'd imagine I'd convert the video's multiple times, which is not what I want. What I'm looking for is a modification for my current script that keeps exactly 4 conversion processes running at any time (until the files in the source videofolder run out).

My current script is this:

```
#!/bin/sh

DIR="/path/to/source"
DESTDIR="/path/to/dest"
SUFFIX="avi"
DESTSUFFIX="mp4"

for i in "$DIR"/*.$SUFFIX
do
	filename=`echo ${i%%.$SUFFIX} | sed 's#^.*/##'`
	wine ffmpeg.exe -i "$i" -vcodec libx264 -level 13 -s 320x240 -b 192k -bt 192k -bufsize 2000k -maxrate 768k -g 250 -coder 0 -threads 4 -acodec libfaac -ac 1 -ar 24000 -ab 48k "$DESTDIR/$filename.$DESTSUFFIX"
done
```

---

### Post by geirha on 2008-10-22
The same function should work. Try this.

Do note that the function uses arrays which is bash specific, so that turns your script from sh to bash. It's possible to do without arrays too.

But why are you using the windows version of ffmpeg, there's [ffmpeg](apt://ffmpeg) in the repositories ...
```

#!/bin/bash

# function that loops until there are less than num commands running
wait_for_less_than () # num command
{
  local pids=( $(pidof "$2") )
  while [ ${#pids[@]} -ge $1 ]; do
    sleep 10
    pids=( $(pidof "$2") )
  done
}

DIR="/path/to/source"
DESTDIR="/path/to/dest"
SUFFIX="avi"
DESTSUFFIX="mp4"

for i in "$DIR"/*.$SUFFIX
do
	filename=`basename "$i" ".$SUFFIX"`
        wine ffmpeg.exe -i "$i" -vcodec libx264 -level 13 -s 320x240 \
                -b 192k -bt 192k -bufsize 2000k -maxrate 768k -g 250 \
                -coder 0 -threads 4 -acodec libfaac -ac 1 -ar 24000 \
                -ab 48k "$DESTDIR/$filename.$DESTSUFFIX"
	wait_for_less_than 4 ffmpeg.exe
done

```

---

### Post by Breepee on 2008-10-22
Thanks again, but it doesn't work. When I start the script, it only runs one instance of ffmpeg, not up to 4.

And I use a current win32 compile because it has stuff like x264, faac, and the new ALAC encoder. I havn't found a native binary yet, and with wine it runs pretty much at full speed (apart from using all 4 cores), so that's good enough for me.

---

### Post by geirha on 2008-10-22
I guess pidof doesn't print anything for ffmpeg.exe then, which means you might have to check for wine or possibly grep the output of ps instead ...

---

### Post by Breepee on 2008-10-23
That's what I though, but ffmpeg.exe does show up (seperately) in the process list of system monitor. wine does not.

---

### Post by Breepee on 2008-10-25
Anyone an idea?

---

### Post by geirha on 2008-10-25
Try replacing pidof with pgrep. If you run an ffmpeg in one terminal, then in another terminal run ```
ps -ef
``` what does the line for ffmpeg look like?

---

### Post by Breepee on 2008-10-27
brent     8651  8649 99 12:14 pts/1    00:00:23 ffmpeg.exe -i /media/1bieb/video

---

### Post by geirha on 2008-10-27
Then I think pgrep should work. Changes marked in blue.
```

#!/bin/bash

# function that loops until there are less than num commands running
wait_for_less_than () # num command
{
  local pids=( $([COLOR="Blue"]pgrep[/COLOR] "$2") )
  while [ ${#pids[@]} -ge $1 ]; do
    sleep 10
    pids=( $([COLOR="Blue"]pgrep[/COLOR] "$2") )
  done
}

DIR="/path/to/source"
DESTDIR="/path/to/dest"
SUFFIX="avi"
DESTSUFFIX="mp4"

for i in "$DIR"/*.$SUFFIX
do
	filename=`basename "$i" ".$SUFFIX"`
        wine ffmpeg.exe -i "$i" -vcodec libx264 -level 13 -s 320x240 \
                -b 192k -bt 192k -bufsize 2000k -maxrate 768k -g 250 \
                -coder 0 -threads 4 -acodec libfaac -ac 1 -ar 24000 \
                -ab 48k "$DESTDIR/$filename.$DESTSUFFIX"
	wait_for_less_than 4 ffmpeg.exe
done

```

---

### Post by Breepee on 2008-10-27
Thanks, but it doesn't work. It launches only one instance of ffmpeg, and keeps only one instance active, as if the wait_for_less_than routine weren't there.

---

### Post by geirha on 2008-10-27
> **Breepee said:**
> Thanks, but it doesn't work. It launches only one instance of ffmpeg, and keeps only one instance active, as if the wait_for_less_than routine weren't there.

Oh! I thought ffmpeg would automatically go into the background. Add a & at the end of the ffmpeg line to send it directly to the background. Didn't enter my mind earlier.

---

### Post by Breepee on 2008-10-27
Adding the & at the end of the wine ffmpeg.exe line results in ffmpeg taking that & and not knowing what to do exiting. Adding it after wine and before ffmpeg doesnt work either and adding is at the end of the wait_for_less_than 4 ffmpeg.exe line doesnt work either.

I didn't make your life easy using wine, have I ;)

---

### Post by geirha on 2008-10-27
> **Breepee said:**
> Adding the & at the end of the wine ffmpeg.exe line results in ffmpeg taking that & and not knowing what to do exiting. Adding it after wine and before ffmpeg doesnt work either and adding is at the end of the wait_for_less_than 4 ffmpeg.exe line doesnt work either.


Hm, that's odd, the shell should catch that & sign, not wine. Make sure it's not quoted, and add a space in front of it to be sure it won't be treated as part of the last argument.

> **Breepee said:**
> I didn't make your life easy using wine, have I ;)

Hehe, more like the packagers of ffmpeg for not linking ffmpeg against libx264 etc. I would probably have tried mencoder instead of using the windows version of ffmpeg though, but mencoder accepts different options, so you'd have to figure out how to translate the ffmpeg options to mencoder options.

---

### Post by ghostdog74 on 2008-10-27
why are you using wine with ffmpeg when there is ffmpeg for linux.  ?

---

### Post by FakeOutdoorsman on 2008-10-27
You could compile a bleeding-edge version of ffmpeg and x264 yourself quite easily:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

Development for both is quite active and the latest versions may better utilize your CPU(s).

---

### Post by geirha on 2008-10-28
Actually, it appears ffmpeg is linked against libx264 after all. Didn't check close enough last time, but it isn't listed in -formats as the name of the enocder, but rather the name of the standard ... h264. So it seems you might be able to use that ffmpeg line for ubuntu's version by using -vcodec h264 and -acodec aac.

---

### Post by Breepee on 2008-10-28
Even if the ffmpeg in the repo's has x264, it still is a way old version, and it doesn't have the ALAC encoder yet (which is new since late september) with which I wanted to experiment for a bit.

Compiling myself is possible of course, but is kind of a last resort. The beauty of this windows binary is that it a) has everything I want, and b) is totally portable because of wine. So I just take the binary with me and I can convert everywhere in the same manner (and it performs just about like a native version). I havn't seen a website with native Linux binaries.

I checked the &, and I didnt use quotation marks and put a space between it and the rest of the line (of course I did ;)).

Point is, this should be possible right? We're missing something or something isn't working like it should.

---

### Post by sysadmn62 on 2008-11-07
Have you thought about changing how you start the jobs instead of the script?

If you submit the jobs to "batch", they will run as long as the load average is low enough.  Every 60 seconds, batch will check if there is another job it can start.

If you have a quad core processor, you might want to use "-l 3" to set the load average cutoff at 3 (instead of the default 1.5).
Edit /etc/init.d/atd to add the option.

To convert all the .VOB in a directory:
```
$ cd DIR
$ for i in *.VOB
do
echo ffmpeg <options> -o ${i%%VOB}.mp4 $i | batch
done
```

I do something similar, except that I use a heavy duty queueing system (slurm-llnl).  More advanced queueing systems let you run jobs on groups of machines, ration resources, etc.  They are probably overkill for this.

---

### Post by pvdb on 2009-02-18
Hi geirha,

I was trying to solve a different problem, and your suggested solution for breepee's problem put me on the right path to fixing mine!  Thanks,

PVDB

---

