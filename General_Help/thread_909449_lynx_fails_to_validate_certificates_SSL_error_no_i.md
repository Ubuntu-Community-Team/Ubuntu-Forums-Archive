---
title: "lynx fails to validate certificates: SSL error: no issuer was found-Continue?"
date: 2008-09-03
forum: General Help
---

### Post by PorcelainMouse on 2008-09-03
For all https sites I've tried, lynx fails to validate the site certificates via SSL/TLS.  Can anyone else confirm this?  I've tried using the SSL_CERT_DIR environment variable, but that has no effect on the behavior, as far as I can tell.  I really hope is not related to x86_64 architecture.

$ lynx [https://ssl.scroogle.org/](https://ssl.scroogle.org/)
...
SSL error:no issuer was found-Continue? (y)

$ dpkg --status lynx
Package: lynx
Status: install ok installed
Architecture: amd64
Version: 2.8.6-2ubuntu2

---

### Post by nickleus on 2008-11-06
i'm on a 32 bit system and i get the same thing, for example even when i try to access my own local apache2 https ssl svn site.

---

### Post by PorcelainMouse on 2008-11-12
Well, that's good news, in a way.  Your post means it's not an architecture issue (or build issue specific to the architecture).  So, the root cause could still be a miss match between the package and the Unbuntu distribution or an actual code bug.  Do you agree?

Lynx is still my favorite and it comes in handy so often.  Can anyone help us?  I haven't found the solution, yet.  Let me know if you do.

---

### Post by nickleus on 2008-11-12
i found out that i could add my own site in the computers cacerts file by doing something like this:```

echo |openssl s_client -connect my.localsite.com:443 2>&1 |sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' | sudo keytool -import -trustcacerts -alias "my.localsite.com" -keystore  /usr/lib/jvm/java-6-sun/jre/lib/security/cacerts -storepass changeit -noprompt
```
where my.localsite.com is my locally configured apache2 ssl site.

---

### Post by PorcelainMouse on 2008-11-12
Thanks for the post, nickleus.  I assume that fixed your lynx problem.  Or did it?  If so, that is NOT the problem I am reported.  I have CA certs for all the CAs of all the sites I've tried and openssl will verify the site with my CA certs even though lynx fails to do the same:

$ openssl s_client -CApath /etc/ssl/certs/ -verify -showcerts -connect <server>:<port>
verify depth is 0
CONNECTED(00000003)
...
SSL-Session:
    Protocol  : TLSv1
    Cipher    : DHE-RSA-AES256-SHA
    Session-ID: 28D5466AAC61EF01BE11DB99CFF5CFED51F4915CCDA8BEFBA54ED8F8C3E446FC
    Session-ID-ctx: 
    Master-Key: 71AEA4A6EC5E13D7612042B34A391BA17CB4A08C98C699DE5779112541FD93612BB9CF7CC70523119CA953D9A6283031
    Key-Arg   : None
    Start Time: 1226518697
    Timeout   : 300 (sec)
    Verify return code: 0 (ok)
---
DONE


openssl verifies the site if I use the -CApath option, but not without.  That's why I tried changing the default certificate repository path for lynx.  But, as I reported earlier, that didn't help.

Wait a minute...why did you put your site's certificate in /usr/lib/jvm/java-6-sun/jre/lib/security/cacerts ?  lynx isn't java; that shouldn't have helped.  Does that directory link somewhere else?  Now I'm intrigued.

---

### Post by Stevko on 2009-09-15
Edit lynx.cfg (possibly /etc/lynx-cur/lynx.cfg) and add or uncoment line
```

SSL_CERT_FILE:/etc/ssl/certs/ca-certificates.crt

```

It worked for me now.

---

### Post by PorcelainMouse on 2009-09-16
Well, that definitely works.  But, isn't that env var for a private/personal cert file?  You know, so you don't have to convince the sysadmin to publish your test CA throughout the system.  Why doesn't lynx go get the files in /etc/ssl/certs anyway?  I mean, doesn't the openssl library include a method for finding the local CA cert repository?  I'm almost positive it does.  But, maybe the lynx package should have the default set, instead of commended.  I'd be interested if anyone knows how this is supposed to work.

---

