---
title: "zoneminder on Dell XPS 1330: the webcam VANISHED!!!"
date: 2008-07-24
forum: Hardware
---

### Post by herger on 2008-07-24
Hi all.
I was installing zoneminder on my Dell XPS 1330 with Gutsy 32 bit.
My webcam worked very well with skype.
I was curious to install zoneminder.
I found a tutorial that explained how to install zoneminder, apache2, mysql-server-5.0 and php5.
Then the tutorial said that if zoneminder didn't show any image from the webcam, I would have done

```

sudo chmod 666 /dev/video0

sudo chmod 475 /usr/bin/zmfix

```

I did it and, when I restarted my laptop, the file /dev/video0 had vanished and the webcam was not accessible any more!!!! 

If I write 

```

sudo zmu -q -d /dev/video0 -v

Error, failed to open video device /dev/video0: No such file or directory

```


 :confused::confused::confused:

What happend?
What can I do?

Thanks and regards

Herger

---

### Post by ELMIT on 2009-09-20
I have similar problem. 
Any try to use zmu will be answered with (video0~2):
Error, failed to open video device /dev/video0: No such file or directory

What could be the reason, and how can I track/solve that?

Zoneminder 1.22.3
Ubuntu 8.04 LTS on AMD/64
Noname cameras. which are working with xawtv (but only always 2 out of 3)

bye

R.

---

### Post by subcontact on 2010-10-09
Hi,

I have the exact same problem.
I have a Dell XPS 1330 running Ubuntu 10.04

The camera works fine with Cheese (webcam software)

I installed zoneminder via apt-get and it's running fine but I cannot see anything being captured after I setup the camera.
One thing is that I wasn't sure what format to set it as (PAL, NTSC etc etc)

Has anyone made any progress with this???

Thanks

---

