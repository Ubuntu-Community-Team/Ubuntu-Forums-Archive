---
title: "Question about gzip compression"
date: 2008-08-10
forum: General Help
---

### Post by mazz72 on 2008-08-10
Hey all. Quick question...

I know that files that are already compressed (mp3,mpg,png,what-have-you) generally won't get much more compressed (if at all) using gzip or anything else. But I just made a compressed backup of my /home folder, and it did not compress at all. It actually got a little bigger!

Original /home folder = 1.7 GB
Backup of /home using rsync = 1.7 GB (perfect, all files/dirs accounted for)
gzipped backup of /home = 1.8 GB.

:confused:

---

### Post by insane_alien on 2008-08-10
mp3's, mpg, pngs etc are already compressed files. applying a compression algoritm to these does tend to result in a larger file size.

if you gzipped lots of text documents or something then you would notice a huge compression ratio.

---

### Post by mazz72 on 2008-08-10
*bump*

anymore insight?

---

### Post by y@w on 2008-08-10
What does your home directory mostly consist of? If you have a large amount of ISO's, MP3's, videos, etc. it will most likely bloat like that. If there's tons of text files, it should compress down fairly well. Also, did you happen to use any hard links? My guess is gzip is going to follow those and bloat out the file size.

---

### Post by Yannick Le Saint kyncani on 2008-08-10
> **mazz72 said:**
> *bump*

anymore insight?

Well, it's like insane_alien already said, things like png graphics, ogg audio, xvid video, gpg archives will grow in size when compressed with lossless algorithms like gzip, because they cannot be compressed any further (basically).

---

### Post by mazz72 on 2008-08-11
OK, well, I guess I don't really have much in my /home folder that wasn't already compressed, then. I mean, yeah I have a lot of pictures, backgrounds, themes, etc, which I could see not compressing anymore than they already are, but I just thought maybe the software apps might compress. I know the actual apps go into the /bin folder, but I know there are some files related to certain apps that are in the /home folder, but I guess they're already compressed?? 

I don't have a problem with the 1.8 GB, I mainly just wanted to make sure I didn't do anything wrong. 

Thanks all. :)

---

### Post by y@w on 2008-08-11
Yeah.. the config files really shouldn't take up much space (10-20MB).. They'll compress down fairly well, but not enough to make much of a difference on a large directory. Your already compressed data will bloat a bit like that after being compressed.. You probably would be better off just making a tarball of your data and not gzipping it at this point.

---

