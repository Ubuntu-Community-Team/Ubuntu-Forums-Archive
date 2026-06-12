---
title: "Tomboy + webdav, how to setup?"
date: 2008-08-18
forum: General Help
---

### Post by B3rt on 2008-08-18
Hi,

I use Ubuntu Hardy and I want to synchronize tomboy on a location on my webserver using webdav.

Eachtime I try to activate webdav I get an error of tomboy, I cannot get it to work.

Webdav runs on a apache 2.2.8 webserver, webdav is installed and running, I made a map called "tomboy" in my public_html folder of my domain (the server uses Direct Admin as control panel)
The webdav link would be [http://www.mydomain.com/tomboy](http://www.mydomain.com/tomboy)

I edited the httpd.conf of the user and added the following code to the virtual box of this domain:

```

        Alias /tomboy /home/<username>/domains/mydomain.com/public_html/tomboy/

--- more code which is default present in DA ---

        <Directory /home/<username>/domains/mydomain.com/public_html/tomboy>
                DAV On
                Options all
                Order Allow,Deny
                Allow from all
                AuthType Digest
                AuthName DAV-upload
                AuthUserFile /home/<username>/domains/mydomain.com/public_html/user.passwd
                <Limit PUT POST DELETE PROPFIND PROPPATCH MKCOL COPY MOVE LOCK UNLOCK>
                        require user <username>
                </Limit>
        </Directory>

```

I run also the following command:
```
htdigest -c "/home/<username>/domains/mydomain.com/public_html/user.passwd" DAV-upload <username>
```

In tomboy I specified the url as:
[http://www.mydomain.com/tomboy/](http://www.mydomain.com/tomboy/)
username: <username>
password: ********

<username> would be in all cases the username of the domain in directadmin

Most time I get an user/pass error, but I am sure these are correct, tomboy log states:
```

18-8-2008 18:16:42 [DEBUG]: FUSE mount call succeeded, but mount path does not exist. This may be an indication that incorrect user credentials were provided, but it may also represent any number of error states not properly handled by the FUSE filesystem.
18-8-2008 18:16:42 [DEBUG]: Successfully unmounted wdfs

```

What do I wrong here and how to solve this?

---

### Post by B3rt on 2008-08-19
bump

Nobody knows this?

---

### Post by mtonnies on 2008-12-02
I am having the exact same problem. Does anybody know what the problem might be?

---

