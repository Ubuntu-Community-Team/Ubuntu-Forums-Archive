---
title: "Enable compiz on Dell Studio 1535?"
date: 2009-04-25
forum: Hardware
---

### Post by redeyez on 2009-04-25
Hello

I just installed a fresh copy of 9.04 64bit on my laptop went to install all of the necessary components for compiz fusion. When I went to enable the extra effects I received a a message that simply said that it could not be enabled. After doing some research I found Bug #366169 stating something about not being able to enable it if you had a intel graphic card. However, I have an ATI HD3450. How would I go about enabling compiz on my laptop?

Oh, and thanks for your time.

---

### Post by jonathank89 on 2009-08-03
I have the same laptop as you. I wrote an artical on how to get the ATI drivers installed on Ubuntu 9.04. See the problem is that ATI's current drivers don't support the version of xserver the Ubuntu team put in 9.04 so basically what you need to do is roll back you xserver to 1.5 which is supported by the ATI drivers. It worked great for me.

Check out the forum post I made [here]("http://ubuntuforums.org/showthread.php?t=1229145") and leave any comments there if it worked or not.

Here's a link to the actual [guide]("http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/"):

[http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/](http://friendlytechninja.vndv.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/)

---

### Post by szczym on 2009-08-03
But you might get problems with video playback, i spend whole morning trying to get desktop effects working normally, like before the downgrade. 
here is the story: [http://ubuntuforums.org/showthread.php?t=1230317](http://ubuntuforums.org/showthread.php?t=1230317)

But it might work you, who knows :popcorn:

---

### Post by jonathank89 on 2009-08-03
I wrote a follow up article fixing the video  playback issues [here]("http://friendlytechninja.vndv.com/2009/08/03/howto-fix-ati-video-playback/"):

[http://friendlytechninja.vndv.com/2009/08/03/howto-fix-ati-video-playback/](http://friendlytechninja.vndv.com/2009/08/03/howto-fix-ati-video-playback/)

It's pretty simple to fix

Best of luck

Jonathan

---

