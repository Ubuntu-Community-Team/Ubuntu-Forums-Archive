---
title: "Need help with python-psycopg2"
date: 2008-10-27
forum: General Help
---

### Post by wjhildreth on 2008-10-27
Hello all,

I am in no way a programmer and need a little help. Currently, Ubuntu 8.04 has python-psycopg2 v 2.0.6. There is a problem with a time function that prevents GNUmed 0.3.2 from working on my system. I have been told that the problem has been solved in the 2.0.7 version. I downloaded the source code, and tried to compile it but I am really over my head. I installed build-essentials and the python-dev stuff but I error out when I run the build script. Is there some place I can get a .deb file for this?

Warm Regards,

Joe

---

### Post by orthodoc on 2009-02-11
I know this is a bit too late. This has been worked out to the extent that it can connect and function with a local pre configured postgresql database. However you may not be able to connect to the public server database.

Caveat: I know this works on ubuntu intrepid 32- bit. I see that you are on ubuntu gutsy.

---

### Post by shilbert on 2009-05-07
This has been solved in version 0.3.12 and later. Joe has finally gotten it to work.

---

