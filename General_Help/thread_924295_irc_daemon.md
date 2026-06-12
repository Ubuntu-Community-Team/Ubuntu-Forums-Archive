---
title: "irc daemon"
date: 2008-09-19
forum: General Help
---

### Post by Th3Professor on 2008-09-19
Looking for an irc daemon and help/howto on installation/setup.

Some offer nice and pretty installers, though apparently they require sudo/root.

Others offer a --prefix option, presumably for a local install (without requiring root access), though a problem comes up in the config, preventing completion of compile/install/etc.

If there is a team of business associates who collaborate via message board on a site that one of them runs (without root access), and they would like to be able to chat via irc on that site, how would they do that? Or, in other words:

How would one go about setting up an irc daemon on a server that's hosting their website?

Thank you.

---

### Post by northern lights on 2008-09-19
[http://www.irchelp.org/irchelp/networks/]("http://www.irchelp.org/irchelp/networks/")

---

### Post by Th3Professor on 2008-09-19
> **northern lights said:**
> [http://www.irchelp.org/irchelp/networks/](http://www.irchelp.org/irchelp/networks/)

Thank you but I don't think that specific link addresses the subject. Did you mean to paste this link:

[http://www.irchelp.org/irchelp/ircd/](http://www.irchelp.org/irchelp/ircd/)

If you are recommending the use of hybrid, okay.

...will take a look at this:

[http://www.irchelp.org/irchelp/ircd/h7setup.html](http://www.irchelp.org/irchelp/ircd/h7setup.html)

...and try that out... though would be grateful if anyone could provide assistance directly via this thread.

Thank you!

---

### Post by Th3Professor on 2008-09-19
```

[ircd@server ~/public_html/irc/bin]$ ./ircd 
ircd: version hybrid-7.2.3
ircd: pid 711
ircd: running in background mode from /home/ircd/public_html/irc

```Used all of the steps in the hybrid h7setup link. The message, above, came up when starting the daemon. Though, when attempting to connect via irc client it would not connect. Any ideas?

UPDATE:

Trying different IRC daemons... it's always in the conf file, apparently, unless there aren't any open ports... not really sure either way.

---

### Post by Th3Professor on 2008-09-20
?

---

