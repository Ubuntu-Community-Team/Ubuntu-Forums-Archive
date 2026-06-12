---
title: "ffmpeg bash script question"
date: 2008-10-16
forum: General Help
---

### Post by rotomd on 2008-10-16
I'm in the early stages of writing a script that loops through all files of the same extension in a directory and converts them to mp4 using ffmpeg. For some reason the loop seems to continue to execute while ffmpeg is converting, causing the first file in the loop to be converted, but none of the other files. I would think that the script would wait with ffmpeg is running, when the first file is done converting it loops to the second file and so on. Any suggestions on what I could change to accomplish this? Thanks!

```

#!/bin/bash

ext=$1
enc=$2

if [ $enc = 'xvid' ]
then
        ls *.$ext | while read file
        do
                ffmpeg -i "$file" -f mp4 -vcodec xvid -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -aspect 4:3 "$file".mp4
        done
else
        echo "Invalid extension"
fi

```

---

### Post by repsol on 2008-10-16
'What happens if you take the done statement out?

---

### Post by rotomd on 2008-10-19
When that happens, I get this error:

```

line 12: syntax error near unexpected token `else'
line 12: `else'

```

---

### Post by ian dobson on 2008-10-19
Hi,

You need to wait for ffmpeg to finish before starting the next, so why not just add a do loop that waits until ffmpeg is finshed, something like:-


```

#!/bin/bash

ext=$1
enc=$2

if [ $enc = 'xvid' ]
  then
    ls *.$ext | while read file
    do
      cmd=`ps -A| grep ffmpeg`
      while [  "$cmd" -ne "" ]; do
        sleep 10;
        echo waiting
        cmd=`ps -A| grep ffmpeg`
      done
      ffmpeg -i "$file" -f mp4 -vcodec xvid -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -aspect 4:3 "$file".mp4         
    done
else
    echo "Invalid extension"
fi

```

The while loop just waits until ffmpeg ends.

Regards
Ian Dobson

---

### Post by rotomd on 2008-10-19
Ian, you read my mind. I was just looking into how to check and see if ffmpeg is running. Let me give this a shot and see how it goes. Thanks!

---

### Post by geirha on 2008-10-19
The shell can list the files itself, no need for ls, so I would use a for loop instead of that while loop. And using pidof will make the code checking if ffmpeg is running a little bit shorter.
```

    for file in *.$ext; do
        while pidof /usr/bin/ffmpeg; do sleep 10; done >/dev/null
        ffmpeg -i "$file" -f mp4 -vcodec xvid -maxrate 1000k -b 700k \
               -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac \
               -ab 192k -s 320x240 -aspect 4:3 "${file/%$ext/mp4}"
    done

```

---

### Post by kingtiger01 on 2008-10-19
Funny thing is i was looking for a Script to do just that! thank you guys for the help!

---

### Post by rotomd on 2008-10-19
Sweet. The script seems to be doing what it should now. Not sure if it was changing the ls to a for statement or if adding the >dev/null statement. Either way, thanks for the help!

---

### Post by phaemon on 2011-07-06
Actually, adding < /dev/null to the ffmpeg command should fix it, as it's probably the problem described on this page: [http://mywiki.wooledge.org/BashFAQ/089](http://mywiki.wooledge.org/BashFAQ/089)

---

### Post by ian dobson on 2011-07-06
> **phaemon said:**
> Actually, adding < /dev/null to the ffmpeg command should fix it, as it's probably the problem described on this page: [http://mywiki.wooledge.org/BashFAQ/089](http://mywiki.wooledge.org/BashFAQ/089)

Hi,

What's the point replaying to an almost 2 year old thread? Post count not high enough? or do you just want to premote "Greg's Wiki". And no you don't have to answer that one.

Regards
Ian Dobson

---

### Post by phaemon on 2012-05-21
> **ian dobson said:**
> What's the point replaying to an almost 2 year old thread? Post count not high enough? or do you just want to premote "Greg's Wiki". And no you don't have to answer that one.
I'm travelling back from Proxima Centauri. As you can tell, I'm getting closer...

---

### Post by nothingspecial on 2012-05-21
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

