---
title: "How to stream media from Ubuntu to Windowz"
date: 2008-09-09
forum: General Help
---

### Post by generic_idea_machine on 2008-09-09
I've been able to play my movies/media ( intranet @ home) between two Ubuntu boxes (sftp!)

Now I would like to stream my movies from my Ubuntu box over to my XP machine. Is Samba the best possible choice for this?

---

### Post by generic_idea_machine on 2008-09-09
anyone?:-\":-\":-\"

---

### Post by mb_webguy on 2008-09-09
Well, acessing the files via a samba share is probably the simplest way to share files on a Linux macine with a Windows machine, but it's not really "streaming".

If you actually want to stream media from one to the other, VLC is one option.  I don't think that's really what you're asking, though.

---

### Post by generic_idea_machine on 2008-09-09
I didnt know that a server side version of VLC could be implemented. 

let me give that a try

thanks!

---

### Post by mb_webguy on 2008-09-09
If streaming is really what you're after, you might find these links for setting up VLC for streaming useful:

[VideoLAN Streaming HowTo]("http://www.videolan.org/doc/streaming-howto/en/streaming-howto-en.html")
[How-To: Stream almost anything using VLC]("http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/")

---

### Post by generic_idea_machine on 2008-09-10
> **mb_webguy said:**
> If streaming is really what you're after, you might find these links for setting up VLC for streaming useful:

[VideoLAN Streaming HowTo]("http://www.videolan.org/doc/streaming-howto/en/streaming-howto-en.html")
[How-To: Stream almost anything using VLC]("http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/")

thanks man!

I am off to Quebec shortly. I will give this a try once I get back. 
:guitar:

---

### Post by generic_idea_machine on 2008-10-04
The easiest workaround that I could find was to:

- sftp into the media server (Also ubuntu)
- Load up Nautilus and browse to the network share. 
- and then streaming is seamless! :guitar:

---

