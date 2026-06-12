---
title: "Watching Video on TV"
date: 2005-12-02
forum: General Help
---

### Post by Mizutsuki on 2005-12-02
I'm running an IBM Thinkpad T22 which has an S3 Savage IX-8 video card and a 900 MHz P3 proc.  The IX has an s-video out port and I have no problem using the program s3switch to put the desktop out to the TV screen.
I do, however have quit a bit of difficulty getting it to play video right.  The first problem is that when I put it out to TV it has to be at the resolution 640x480 and then when I do that players like gxine and mplayer show only a portion of the video, the rest is all covered in blue.  I managed to get it to work by using two different video playback drivers: xshm and openGL, but xshm makes the video very ugly (the gradients are all gone, it's just one color and then it's a different one, it makes low light scene look awful.) and openGL is unwatchably slow.  Note that, at full resolution on my laptop's display I can watch any video fine and it looks great and has no playback issues.  Is there a way I can download and try more different playback drivers?  I get the feeling like if I just keep trying them maybe one will work out and play it back and it'll look good and decode right.
On other issue, when I use mplayer (from the command line) with the svideo out to the TV the picture goes really strange.  I much prefer mplayer to gxine, but I think there may be a compatability issue.  Does anyone know anything about this?
Thank you,
Stephen

---

### Post by Mizutsuki on 2005-12-03
*bump*

---

### Post by Mizutsuki on 2005-12-03
*bump**bump*

---

### Post by Mizutsuki on 2005-12-03
*bump**bump**bump*

---

### Post by PesVseved on 2006-06-16
I got the same problem. :sad:

---

### Post by oblivious on 2006-07-26
Hello, 
 I'm having the same problem described here, although I'm not running the same version of Ubuntu. I hope my post here isn't  inappropriate, I will post this in the correct section as well. 

 Xv is fast and works well on full screen at 1024x768 (default on my system), but playback is affected at lower resolutions in the same way as described by Mizutsuki.

 Other drivers work fine at low resolutions, but tend to be slow when used with full screen at the default resolution.

 I'm very happy with Ubuntu, and currently this is the only issue that is keeping me away from fully enjoying the Ubuntu experience. Also, it's the only issue that I've been unable to solve by just browsing the forums (and I've had plenty :-D)

 Any help would be greatly appreciated.

---

### Post by Mizutsuki on 2006-11-09
I just bumped into this again and I thought I'd stop by and let you know how I've dealt with it for the last year or so.  The problem is that the video card does not have very good drivers, and video playback (using the Xv decoder) is a no-go for TV out.  What I've been doing is using mplayer like this:
first I change the resolution:
$ xrandr -s 640x480
and then I enable tv-out (mirrored)
$ sudo s3switch tv lcd
and then I launch the player: 
$ mplayer -vo x11 -zoom -fs <other options> <video.avi>

It looks kinda funny on the laptop screen (on account of the crappy display) but it looks good enough, and 95% of the time it plays just fine.  Occasionally I have trouble with slowness in some files.

I hope this helps anyone who might come around with the same question later.

Stephen

---

