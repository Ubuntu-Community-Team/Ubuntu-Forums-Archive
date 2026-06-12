---
title: "ssh url handler for firefox, help?"
date: 2008-09-24
forum: General Help
---

### Post by Elshar on 2008-09-24
Hey guys,

I'm trying to get firefox to load putty when I click on a ssh:// url. I've got it working in windows, and it works in OSX, but for some reason I just can't get it working on ubuntu. I'm using Firefox 3.0.2 on 8.04. I've added the following bits to firefox via user.js. I know it's loading, because I can see these values in bold and with the values listed below in about:config:

```

user_pref("network.protocol-handler.external.ssh", true);
user_pref("network.protocol-handler.warn-external.ssh", false);
user_pref("network.protocol-handler.expose.ssh", true);
user_pref("network.protocol-handler.app.ssh", "/usr/local/bin/ff_ssh");
```

ff_ssh just contains this:
```

#!/usr/bin/bash
/usr/bin/putty `echo $1 | sed -e "s/ssh:\/\///"`

```

If I run this from the command line, putty fires up. And if I send a proper url as an arg from the command line, it works. In Firefox, it just doesn't do anything. No putty window, no error, nothing.

Has anyone gotten this to work? How?

---

### Post by Elshar on 2008-09-29
I still haven't been able to get any farther in this. I know it can be done. Hard to believe noone's done it in ubuntu?

---

### Post by andguent on 2008-10-28
I'm looking for this information as well. I've found numerous guides, but none seem to get a result. Manually running the handler script with an ip as an argument pops up my terminal window fine. If you got it working I would love to know.

Ubuntu Hardy, Firefox 3.03

---

### Post by andguent on 2008-10-28
Nevermind, got it. It appears that in most of my screwing around, I had leftover settings in Edit -> Preferences -> Applications. I also was not restarting Firefox often enough to do accurate testing. Deleting settings in the Applications box for my ssh protocol and rebuilding helped immensely.

I'm confused how/why you are using putty on Linux rather then just ssh, but hey, Linux is full of choices. Choice is kind of the point...

---

### Post by Elshar on 2008-11-21
> **andguent said:**
> Nevermind, got it. It appears that in most of my screwing around, I had leftover settings in Edit -> Preferences -> Applications. I also was not restarting Firefox often enough to do accurate testing. Deleting settings in the Applications box for my ssh protocol and rebuilding helped immensely.

I'm confused how/why you are using putty on Linux rather then just ssh, but hey, Linux is full of choices. Choice is kind of the point...

It's really just more of a habit from my windows days. There are a few other reasons, like it opening a new window when run from the cli and such.

So what exactly did you do to make it work? Just used the built-in ssh? I could've swore I tried that, but maybe I'll try again. Thanks :)

---

