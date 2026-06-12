---
title: "bulk re-naming mp3s"
date: 2008-09-02
forum: General Help
---

### Post by rob1984 on 2008-09-02
hello.

i'm sorting out my music collection (thousands of mp3s)  and i could do with cleaning up the filenames.  i reckon i could do this pretty easily with a few simple commands or a small shell script, but i don't really know where to start.

can anybody give me any tips or guide me through doing something like this?  stuff like getting rid of underscores, replacing characters, removing the artist name from files orginized into albums etc..

any help will be great.

---

### Post by brian_p on 2008-09-02
> **rob1984 said:**
> hello.

i'm sorting out my music collection (thousands of mp3s)  and i could do with cleaning up the filenames.  i reckon i could do this pretty easily with a few simple commands or a small shell script, but i don't really know where to start.

can anybody give me any tips or guide me through doing something like this?  stuff like getting rid of underscores, replacing characters, removing the artist name from files orginized into albums etc..

any help will be great.

The rename command is already on your system.

```
man rename
```

---

### Post by Luke771 on 2008-09-02
I use prefixsuffix for bulk renaming, it's in repos, it has a GUI and it's easy to use, but, it's kind of limited, it basically does prefixes and suffixes only, which would be good if you want to change your filenames from <songname>.MP3 to <songname>.mp3 or from Led Zepplin - <songname>.mp3 to Led Zeppelin - <songname>.mp3

To add band names at the beginning of filenames, I haven't found anything better than going alphabetical, e.g. replace prefix a with bandname - a will add the band name to all the songs with titles beginning in A. repeat operation for B, C, etc (anyone found a better solution?)

---

### Post by rob1984 on 2008-09-03
ah cool.  i'll check out the man page for rename.  i wasn't aware of it, i'd been using mv.  i'll have a look at prefixsuffix too.

thanks

---

### Post by barboachtraner on 2008-09-03
Amarok can rename files in user specified format and organize them into new directories, both using ID3 tags. EasyTag is another option, although I just stick to Amarok for organization since it's my audio player of choice anyway.

---

### Post by Zorael on 2008-09-03
I use krename for renaming files and exfalso for batch-changing id3 tags. Both are in the repositories with those package names.

---

### Post by Trail on 2008-09-03
> **barboachtraner said:**
> amarok can rename files in user specified format and organize them into new directories, both using id3 tags. Easytag is another option, although i just stick to amarok for organization since it's my audio player of choice anyway.

+1

---

