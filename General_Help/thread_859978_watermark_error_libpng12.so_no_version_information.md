---
title: "watermark error libpng12.so no version information available"
date: 2008-07-15
forum: General Help
---

### Post by CommunityZ on 2008-07-15
convert -font Arial -pointsize 15 -draw "gravity south fill black text 0,33 'www.mysite.com' fill white text 1,32 'www.mysite.com'" *.jpg

I am trying to use this command to watermark my photos but i got this error 
convert: /usr/local/lib/libpng12.so.0: no version information available (required by /usr/lib/libMagick.so.9)

ls -al of /usr/local/lib
got me this 

-rw-r--r--  1 root root   286880 Jul  3 07:01 libpng12.a
lrwxrwxrwx  1 root root       13 Jul  3 07:01 libpng12.so -> libpng12.so.0
lrwxrwxrwx  1 root root       20 Jul  3 07:01 libpng12.so.0 -> libpng12.so.0.1.2.26
-rwxr-xr-x  1 root root   263065 Jul  3 07:01 libpng12.so.0.1.2.26

How to fix the above error?

---

