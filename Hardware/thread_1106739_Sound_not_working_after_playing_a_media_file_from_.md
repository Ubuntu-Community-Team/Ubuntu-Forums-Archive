---
title: "Sound not working after playing a media file from net"
date: 2009-03-26
forum: Hardware
---

### Post by malaka19 on 2009-03-26
Hi all

I am Hardy user. When I played a sound or video file from net and later play a media files from hard disk on those files sounds is not working. Files in the net continuous to work ok. 

Any idea.? what is the problem.?

I thank you in advance

---

### Post by sigmarhophi on 2009-03-26
I have had the same problem, all though i am running intrepid.  I don't know what causes the issue, however I have found this will fix it:  
> sudo alsa force-reload.  

Executing the above command will reload your sound drivers, but it will close out everything attatched to the driver such as your browser, media players, vitual box, ETC.

---

### Post by malaka19 on 2009-03-26
@sigmarhophi  	


Thanks a lot for the reply. It's sad to hear that problem even exist in the never version. 

cheers

---

