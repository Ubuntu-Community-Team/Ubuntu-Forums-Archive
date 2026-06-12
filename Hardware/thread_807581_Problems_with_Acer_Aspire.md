---
title: "Problems with Acer Aspire"
date: 2008-05-25
forum: Hardware
---

### Post by Trixilver on 2008-05-25
Hey people. I have Ubuntu 8.04 installed on my Acer Aspire 5602.

Whenever I try to boot up now it takes about 10 minutes just to get to the login screen. I don't know why, but it just hangs at the loading part (where the black bar fills up) and doesn't do a thing.

I think it has something to do with my webcam because sometimes I get another problem with booting up where I'd get "Failed to configure camera" over and over again - probably about a hundred times - before it would continue to boot up.

Is there any fix for this? Or even if I could completely disable the camera (because I didn't really want it in the first place), that would be great.

---

### Post by mcarni on 2008-07-22
hi,

I've been running ubuntu for a few months with both Gutsy and Hardy on a acer 5601 and everything went fine until yesterday when after having a skype video call at te next reboot I had the progress bar to get stuck and basically the compuetr doing nothing for several minutes.
the only hint was that one of the messages I got was " failed to connect to camera"
on ubuntuforum I found two solutions, 

1 
[http://ubuntuforums.org/showpost.php?p=5290635&postcount=1026](http://ubuntuforums.org/showpost.php?p=5290635&postcount=1026)

> **daveappendix said:**
> Well, that solved it! I flipped the camera round to the alternate orientation, and then back again. Next time I booted, there were no complaints. It might explain why I've been having camera trouble in windows too. Shoddy hardware + it's over 2 years old now.

Cheers,
Dave.

I know it is not going to sound very scientifc, but I solved the problem by rotating the camera back and forth a couple of times.

Next time I booted everything was fine.

2
ALternatively you can blacklist the camera as described in the following post:

[http://ubuntuforums.org/showpost.php?p=3600684&postcount=10](http://ubuntuforums.org/showpost.php?p=3600684&postcount=10)


> **erktrek said:**
> As an aside I was able to get around the issue by blacklisting gspca..

I added this entry:

```

# Disable auto-loading of gspca module
blacklist gspca

```

to



Hope this helps?

E.


hope it works also for you

M

---

