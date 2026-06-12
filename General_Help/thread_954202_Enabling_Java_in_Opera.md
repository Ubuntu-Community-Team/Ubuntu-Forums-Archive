---
title: "Enabling Java in Opera"
date: 2008-10-20
forum: General Help
---

### Post by writer3 on 2008-10-20
Hello folks,

I'm using Ubuntu 8.04(Hardy Heron). I just recently decided to switch over from Firefox 3 to Opera. I've been fighting with the Java options for over 2 hours and just can't get a solution. 

What I've found tells me that I have to go to Tools > Preferences > Content > Java Options and validate the Java "path" but when I do this, I get this error message;

"Could not find a valid Java installation. Enter another directory and try again."

Of what I know, that IS the correct directory. I found a site that told me to run "locate libjava.so" in a terminal and it would tell me where the proper directory is, so I ran that, and got "/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386/libjava.so"

So I took that to the Java validation and got the above error message. 

Can someone please tell me what I'm doing wrong? I really don't want to go back to Firefox 3. It's horrible.

Thanks in advance.

---

### Post by TransitMan on 2008-10-21
When you go to validate the path, use only the following - "/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386" (without quotes).
Once you have this path listed, then validate Java. As with mine, it validated with no problems.

---

### Post by writer3 on 2008-10-21
Ahh, thank you! Worked like a charm. Only problem is, it still isn't displaying youtube videos/things of the like. :confused:

---

### Post by TransitMan on 2008-10-21
YouTube requires Flash to be installed.

You can either install Flash from the repos (with medibuntu repos listed) or go to Adobe's website and download the latest .deb for Flash.
I did this and install via gdebi and it works well.

---

