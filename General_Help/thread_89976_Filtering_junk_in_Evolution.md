---
title: "Filtering junk in Evolution"
date: 2005-11-13
forum: General Help
---

### Post by peterbrowne on 2005-11-13
I cannot seem to be able to get evolution to automatically filter spam...  how do i do it?

TIA,
Peter

---

### Post by steil on 2005-11-14
You need to install a filtering program such as spam assassin.

---

### Post by btdown on 2005-11-14
Well, I have installled Spamasassin, and enabled it in the config file (as other threads here suggest) and Evolution STILL doesnt filter any spam even though I've been training it for three weeks. Could anyone help diagnose the problem?
 
Thanks
BT

---

### Post by Darrin on 2005-11-27
Im with you on it. Ive been training it for a couple of weeks and nothing shows up in the junk mail unless I put there manually. :(

---

### Post by btdown on 2005-11-27
Yeah i gave up on it...I'm really disappointed that it doesn't work. I've tried it under imap and pop, no joy. By looking at the spam log it is identifying the email as spam, just nothing happens to it in evo. I wound up deleting the evo icon from the upper bar and installing/replacing it with Thunderbird. Not exactly what I wanted, but it better than that piece of garbage Evolution. 

Who develops Evoultion, and where are they?

---

### Post by Darrin on 2005-11-27
I bummed. I also wanted to use evolution over thunderbird. I Still dont want to give up on it, but Im frustrated over it.

---

### Post by Darrin on 2005-11-28
In case I might be doing something incorrectly here. Here's what my  /etc/default/spamassassin shows. Maybe someone can take a look.

```
# /etc/default/spamassassin
# Duncan Findlay

# WARNING: please read README.spamd before using.
# There may be security risks.

# Change to one to enable spamd
ENABLED=1

# Options
# See man spamd for possible options. The -d option is automatically added.

# NOTE: version 3.0.x has switched to a "preforking" model, so you
# need to make sure --max-children is not set to anything higher than
# 5, unless you know what you're doing.

OPTIONS="--create-prefs --max-children 5 --helper-home-dir"

# Pid file
# Where should spamd write its PID to file? If you use the -u or
# --username option above, this needs to be writable by that user.
# Otherwise, the init script will not be able to shut spamd down.
PIDFILE="/var/run/spamd.pid"

# Set nice level of spamd
#NICE="--nicelevel 15"
```

---

### Post by clp on 2005-11-28
I've got the same problem.

Anyone knows the solution?

---

