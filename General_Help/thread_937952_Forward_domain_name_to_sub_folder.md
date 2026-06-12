---
title: "Forward domain name to sub folder?"
date: 2008-10-04
forum: General Help
---

### Post by t mac on 2008-10-04
I have several sites on my new Ubuntu server. One of my sites uses a CMS for the site pages and then I have a forums area.  The CMS is hosed up currently, so I want to forward the domain so it goes directly to the /forums sub-directory.  How do I go about doing that with the command line? (server admin is gone for a few days)

Thanks all!

---

### Post by Calmatory on 2008-10-04
Which web server is the server using?

In lighttpd that would be something like this in /etc/lighttpd/lighttpd.conf:

```

$HTTP["host"] == "forums.examplesite.org" {
server.document-root = "/var/www/examplesite.org/forums/"
}

```

or

```

$HTTP["host"] == "exampleforums.org" {
server.document-root = "/var/www/examplesite.org/forums/"
}

```

---

