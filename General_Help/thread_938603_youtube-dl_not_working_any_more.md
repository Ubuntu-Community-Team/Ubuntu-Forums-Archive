---
title: "youtube-dl not working any more"
date: 2008-10-05
forum: General Help
---

### Post by wormser on 2008-10-05
Is anybody else having problems with youtube-dl?  It use to work just fine.  Did YouTube change there site?

```
youtube-dl http://www.youtube.com/watch?v=JBTvSlhXgiI
```> Retrieving video webpage... failed.
Error: unable to retrieve video webpage.
Try again several times. It may be a temporary problem.
Other typical problems:

* Video no longer exists.
* Video requires age confirmation but you did not provide an account.
* You provided the account data, but it is not valid.
* The connection was cut suddenly for some reason.
* YouTube changed their system, and the program no longer works.

Try to confirm you are able to view the video using a web browser.
Use the same video URL and account information, if needed, with this program.
When using a proxy, make sure http_proxy has [http://host:port](http://host:port) format.
Try again several times and contact me if the problem persists.



---

### Post by wormser on 2008-10-07
Can somebody test this out for me.  

```
sudo apt-get install youtube-dl
```Then try downloading a youtube video.

```

youtube-dl http://www.youtube.com/watch?v=JBTvSlhXgiI

```

---

### Post by todak on 2008-10-07
HA-HA!:biggrin: Some body from Redmond using Ubuntu! If you are using Firefox, add the **Video DownloadHelper** extension or **youplayer** extension and you can grab flash video from most any site that has it embedded.

---

### Post by mcduck on 2008-10-07
..or just open the video address in Firefox, and then go to /tmp and find the file with name starting with "Flash". That's your .flv video. Just copy it anywhere you like..

---

### Post by wormser on 2008-10-08
Thanks for the tips guy.  I already use both of them.  I still would like to know program is broken..

---

