---
title: "Nagios SSL/NRPE problem"
date: 2008-07-30
forum: General Help
---

### Post by slacker9876 on 2008-07-30
Hello Everyone, 
   I have just finished buting my workstation and wanted to get Nagios up and running which is actually OK. However, localhost cannot be monitored because I need to have the NRPE configured. When trying to install it:

checking for SSL headers... configure: error: Cannot find ssl headers

is all I get, I have verified that both openssl and libssl are installed. Can I get a little help on this one?

TIA!!

---

### Post by slacker9876 on 2008-07-31
{nudge}

---

### Post by fillmore on 2008-10-14
Hi,

Try with ```
./configure --with-ssl=<absolute-path-to-ssl> --with-ssl-lib=<absolute-path-to-ssl-lib> 
```

Example: ```
./configure --with-ssl=/usr/bin/openssl --with-ssl-lib=/usr/lib 
```

Hope this helps.

Cheers!

---

### Post by Vince-0 on 2009-03-04
> **fillmore said:**
> Hi,

Try with ```
./configure --with-ssl=<absolute-path-to-ssl> --with-ssl-lib=<absolute-path-to-ssl-lib> 
```

Example: ```
./configure --with-ssl=/usr/bin/openssl --with-ssl-lib=/usr/lib 
```

Hope this helps.

Cheers!
If the above doesn't work, install the libssl-dev package via apt and try the configure with the directives above.

Worked for me !

---

### Post by blknite on 2010-08-07
This worked for me. :)

"./configure --with-ssl=/usr/bin/openssl --with-ssl-lib=/usr/lib"
After installing libssl-dev

---

### Post by Karl1982 on 2010-08-11
I hit that snag myself once.  The check_http plugin requires the SSL development library to make checks against pages that load via HTTPS (I believe it was *libssl-dev*).

*apt-get install libssl-dev*

... and then redo the make/install steps just for the plugins if you were installing from source.  They have to be recompiled with *libssl-dev* present.

---

### Post by zero-n on 2010-09-02
installing 
```
libssl-dev
```

have fixed my problem too

thanks

---

### Post by Petkaux on 2010-11-04
Same here, libssl-dev was missing. Thanks!

---

### Post by binarypower on 2011-10-12
> **Vince-0 said:**
> If the above doesn't work, install the libssl-dev package via apt and try the configure with the directives above.

Worked for me !

Worked for me as well :popcorn:

---

### Post by oldos2er on 2011-10-13
Back to sleep, old thread. Closed.

---

