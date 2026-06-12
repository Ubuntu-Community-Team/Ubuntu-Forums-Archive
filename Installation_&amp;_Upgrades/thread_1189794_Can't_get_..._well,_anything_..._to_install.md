---
title: "Can't get ... well, anything ... to install"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by W-Unit on 2009-06-17
Hey guys, I'm a brand new Linux user trying to repurpose my old computer as a media server for my family. I've been anxious to learn about Linux for a long time, but now that I've finally taken the step and installed it I'm finding it rather frustrating, to make an understatement. I'm determined to learn, though ;)

The first thing I did was try to set up the media server using MediaTomb. I first installed it by going to Applications>Add/Remove and selecting it. This installation seemed to work when I ran it but as it was just about the first thing I did after installing Ubuntu on my computer I was really confused by the interface and decided to try following a tutorial on setting it up. The only tutorials I could find were ones that walked through the setup process using apt-get, so I uninstalled MediaTomb via Applications>Add/Remove and reinstalled it as instructed by the tutorials. I say tutorial**s** because I tried 2 different ones, after the first one failed. I can't find the ones I used again, but when I got to the end of the last one, it instructed me to restart MediaTomb via some command I forgot, and when I did so, I got a message to the effect of "starting upnp server.... [fail]," which needless to say is not very helpful diagnostically.
After all this, I tried once again uninstalling/reinstalling MediaTomb via Applications>Add/Remove, however I fear during the course of the tutorials I messed up something that reinstalling the package failed to fix, as the MediaTomb server refused to run this time around.

So ok, the hell with MediaTomb I said. I found [this tutorial]("http://www.ubuntugeek.com/howto-setup-itunes-compatible-media-server-in-ubuntu.html") on setting up a different type of media server which claims to be itunes compatible, which is cool. Again, though, the only problem with it is that it doesn't seem to work. After following all the instructions in the tutorial, the final step, running the server, again fails. Here's the output when I try:
```
will@Wills-Old-PC:/$ sudo mt-daapd -f
Firefly Version svn-1696: Starting with debuglevel 2
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so: undefined symbol: avcodec_decode_audio
Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load
Plugin loaded: rsp/svn-1696
Plugin loaded: daap/svn-1696
Starting signal handler
Starting rendezvous daemon
Client running
Initializing database
Full reload...
Starting mp3 scan
opendir: No such file or directory
Query: create index idx_path on songs(path,idx)
Error: index idx_path already exists
Aborting
```So anyways, all my request comes down to is this: can somebody please help me successfully get a media server of some kind up and running?

Much appreciated,
Will

P.S. Incidentally, I tried following [this tutorial](http://rubbervir.us/projects/ubuntu_media_server/) and everything seemed to go OK. I can now SSH into my Ubuntu box from other computers on the network. However this seems to be very different from turning my computer into a media server... SSH seems to be something completely different and utterly useless with regard to creating a media server. Am I wrong here?

---

### Post by celticbhoy on 2009-06-17
It is not something I have done before but have a look here :-

[http://rubbervir.us/projects/ubuntu_media_server/](http://rubbervir.us/projects/ubuntu_media_server/)

and here :-

[http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/](http://www.geek.com/articles/chips/feature-linux-media-server-using-ubuntu-810-2009065/)

I would probably have a read through both first before doing anything to see if they do what you want.

---

### Post by W-Unit on 2009-06-17
Alright, so I followed the instructions on the second link you gave me and got MediaTomb up and, I thought, fully running. My PS3 now discovers the MediaTomb server and sees some of the media in it.

Currently, I have two media files that I put in the directory which MediaTomb scans for media: one song and one picture. When I access MediaTomb via [http://127.0.0.1:49152/](http://127.0.0.1:49152/), I can see both the music file and the picture file, however I cannot click on them (they are plaintext, not links). They both have a "+" button next to them, which I have tried clicking and which appears to do nothing.
Earlier (although I cannot reproduce this) I was able to click on both files, however I would then get a 404 Not Found error. During this time, there wasn't a plus button, but an edit and a delete button next to the files. Restarting the server after installing ffmpeg brought this condition to an end.
My PS3 sees the music file, but cannot play it because "it may have been deleted from the server."
My PS3 does not see the picture at all. I suspect this is a Sony eccentricity though and not MediaTomb's fault (I read that the PS3 will only discover media in a narrow range of formats)
The music and the picture both play/display fine locally. It seems that MediaTomb just isn't handling them correctly.
Attached is a screenshot of what it looks like.

---

### Post by celticbhoy on 2009-06-17
As I said earlier this is not something I have ever done before so I cant help from experiance, but perhaps if you post your problem on the media tomb forum you may get more help :-

[http://sourceforge.net/forum/?group_id=129766](http://sourceforge.net/forum/?group_id=129766)

I hope it works out for you, and from the sounds of it you cant be that far away.

---

### Post by celticbhoy on 2009-06-17
Another option would be to leave a note for the how-to author on the bottom of the web page explaining your problem. This might be the best idea, as he is the one who gave instruction, and uses this setup himself, also on a PS3.

---

### Post by celticbhoy on 2009-06-17
Reading up on this it seems it may be worth checking whether you have firestarter firewall running, and if so setting it to allow the PS3 access.

---

### Post by celticbhoy on 2009-06-17
This thread may supply what you need :-

[http://ubuntuforums.org/showthread.php?t=1040458&highlight=media+tomb](http://ubuntuforums.org/showthread.php?t=1040458&highlight=media+tomb)

---

### Post by celticbhoy on 2009-06-19
Dont know how you got on, hope it all went OK. If not here is a how-to for another web based media server other than media tomb, its called Jinzora

[http://maketecheasier.com/how-to-install-and-setup-jinzora-media-server-in-ubuntu/2008/08/25](http://maketecheasier.com/how-to-install-and-setup-jinzora-media-server-in-ubuntu/2008/08/25)

---

