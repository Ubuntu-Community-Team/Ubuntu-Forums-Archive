---
title: "apache2, no png"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by animuson on 2009-01-02
I've researched this and found the bug and I added the EnableSendfile Off thing to the config file but I still can't load PNG files on my website, am I missing something else?

---

### Post by albinootje on 2009-01-02
> **animuson said:**
> I've researched this and found the bug and I added the EnableSendfile Off thing to the config file but I still can't load PNG files on my website, am I missing something else?

Did you restart apache ?

See also comment #5 here :
[http://ubuntuforums.org/showthread.php?t=555804](http://ubuntuforums.org/showthread.php?t=555804)

---

### Post by animuson on 2009-01-02
When I tried restarting the Apache server again, I noticed that it was running through the /etc/init.d/httpd. I stopped the httpd and started apache2 but it switches back to httpd, is it supposed to do this?


And yes, I saw comment #5, my file names are exactly the same.

---

### Post by albinootje on 2009-01-02
> **animuson said:**
> When I tried restarting the Apache server again, I noticed that it was running through the /etc/init.d/httpd. I stopped the httpd and started apache2 but it switches back to httpd, is it supposed to do this? 

Depends..
/etc/init.d/httpd is used by RedHat Linux or RedHat-alike Linux distributions.
In a recent Ubuntu (8.x) distribution you should only have /etc/init.d/apache2 not /etc/init.d/httpd
Did you do some installation from source ?
Or are you using a VPS-based server from some webhosting company, which doesn't use Ubuntu or Debian ?

---

### Post by animuson on 2009-01-02
I'm using a VPS running on Ubuntu 8.04. I'd assume the httpd was installed with DirectAdmin, that's the only thing I can think of.

---

### Post by albinootje on 2009-01-02
> **animuson said:**
> I'm using a VPS running on Ubuntu 8.04. I'd assume the httpd was installed with DirectAdmin, that's the only thing I can think of.

Okay, so what happens when you do /etc/init.d/httpd restart ?
Does that help or not ?
And which apache config file did you edit ?
Apache 2.x has changed from Apache 1.x
In Apache 1.x there were less "generic" config files to deal with.

---

### Post by animuson on 2009-01-02
The /etc/init.d/httpd restart does just fine.

I put the line at the end of both /etc/apache2/apache2.conf and /etc/httpd/config/httpd.conf with no effect (restarted each time).

---

### Post by albinootje on 2009-01-02
> **animuson said:**
> I've researched this and found the bug and I added the EnableSendfile Off thing to the config file but I still can't load PNG files on my website, am I missing something else?

I just searched a bit more, and I can only find a recent bug-report for png and apache here :
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393)
and that is about this issue while using the Ubuntu "Live CD".

Your files are called some_file.png, and *not* some_file.PNG right ?

GL!

---

### Post by animuson on 2009-01-03
I am sure. I started fiddling around with it a little, and the problem seems to be that it won't load the PNG image into the background-image property in CSS, but loads the image in an <img> tag fine in all browsers except IE.

[http://www.animuson.com](http://www.animuson.com)
Below the "Testing Content Left" is a white box which has the PNG image set as the background-image and below the "Testing Content Right" is the PNG image in an <img> tag (with a white background so you can see it).

---

### Post by animuson on 2009-01-03
Nevermind, I think I figured out the problem. I had run the PNG image through AdvantageCOMP (a PNG compressor tool) and it wouldn't show up, but an uncompressed version of the PNG image showed up fine in the background. I guess I'll have to find a different PNG compressor that will work in the backgrounds. I tried using PNGCrush but it wouldn't work.

**Problem Solved**
I wonder why it only happens when you try to set it as a background image...

---

