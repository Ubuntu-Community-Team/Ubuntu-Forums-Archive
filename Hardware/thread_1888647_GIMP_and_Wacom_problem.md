---
title: "GIMP and Wacom problem"
date: 2011-11-29
forum: Hardware
---

### Post by dogworth on 2011-11-29
I have the same problem as shown here:
[http://www.youtube.com/watch?v=NydM9c97b3Y&feature=channel_video_title](http://www.youtube.com/watch?v=NydM9c97b3Y&feature=channel_video_title)

I only started having this issue in the past month once I bought an intuos4. Before that I was using a friend's intuos3 without issue a few weeks earlier. Now, both tablets do the funky line thing. I'm not using any script for the tablet, just using it as is out of the box. On a fresh install I did for a relative it worked fine.

xsetwacom -V
0.11.0

gimp -version
2.6.11

---

### Post by Favux on 2011-11-29
Hi dogworth,

Unfortunately a known bug:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  And by the way it affects all tablets not just the Wacoms.

---

### Post by dogworth on 2011-11-29
Thanks for the response and link.

---

