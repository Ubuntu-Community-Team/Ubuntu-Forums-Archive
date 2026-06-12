---
title: "CLI auto-login with authless sudo"
date: 2008-10-31
forum: General Help
---

### Post by fuzzypig on 2008-10-31
No, I haven't gone mad.

I am attempting to make a customized livecd from Ubuntu 8.10 CLI. I don't intent to provide any GUI in this livecd. What I need to know is:

1. How do I set the OS to automatically log in as a non-root user directly after boot without any user input?

2. How do I set up sudo and/or su so that they can be toggled without entering a password?

I've seen other livecds with similar setups, so I'm sure that this is possible. Any suggestions?

---

### Post by DGortze380 on 2008-10-31
> **fuzzypig said:**
> No, I haven't gone mad.

I am attempting to make a customized livecd from Ubuntu 8.10 CLI. I don't intent to provide any GUI in this livecd. What I need to know is:

1. How do I set the OS to automatically log in as a non-root user directly after boot without any user input?

2. How do I set up sudo and/or su so that they can be toggled without entering a password?

I've seen other livecds with similar setups, so I'm sure that this is possible. Any suggestions?

Take a look at the gentoo install cd. It is not encouraged by ubuntu, but I think it would be easier to auto-login as root with a random root password.

---

### Post by fuzzypig on 2008-11-01
I would rather not log directly into root. I also don't want to examine a livecd for hours trying to figure out what was changed. Some instructions would be helpful.

Edit: After some searching I found that editing the /etc/sudoers file will allow me to bypass the password prompt on sudo. This just leaves question #1.

---

### Post by fuzzypig on 2008-11-01
Sorry for the double post


/etc/sudoers had no effect.

How can I automatically log in to root on startup?

Edit: /etc/sudoers fixed. Back to question 1.

---

