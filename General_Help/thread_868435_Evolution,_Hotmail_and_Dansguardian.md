---
title: "Evolution, Hotmail and Dansguardian"
date: 2008-07-23
forum: General Help
---

### Post by Clayton South on 2008-07-23
Hi everyone,

I'm using Hardy 8.04 with all the updates, and I'm running dansguardian filter, with evolution as my mail client. I have followed the instructions for setting up hotmail found online, but evolution is unable to connect to hotmail when dansguardian is enabled - though it works just fine when it's disabled. 

I've placed the SMTP for hotmail (127.0.0.1:2500) in the IP to not filter category, but so far it has not worked. 

Any ideas?

Thanks! It's really appreciated.

-Clayton South

---

### Post by Clayton South on 2008-09-02
Still having this problem. Can anyone offer a suggestion?

---

### Post by mssever on 2008-09-02
Have you looked through the logs to find out why it's being blocked?

---

### Post by Clayton South on 2008-09-04
> **mssever said:**
> Have you looked through the logs to find out why it's being blocked?

Hi,

Thanks for the response - this issue has been on my mind for months! 

I have not checked the logs to find out why it's being blocked - can you tell me how to do this?

Thanks!

-Clayton South

---

### Post by mssever on 2008-09-04
> **Clayton South said:**
> I have not checked the logs to find out why it's being blocked - can you tell me how to do this?
Logs live in /var/log. Look in your dansguardian logs. Your proxy server's logs might also be relevant.

---

### Post by Clayton South on 2008-09-09
> **mssever said:**
> Logs live in /var/log. Look in your dansguardian logs. Your proxy server's logs might also be relevant.

I'm looking at the Dansguardian logs now, and while I don't see anything telling so far, the error within evolution was "Unable to connect to POP server 127.0.0.1 Error sending password: broken pipe." Should I also check the logs for tinyproxy?

This doesn't occur when I shut off dansguardian, and hotmail seems to work when dansguardian is off, so i know this is a configuration issue. 

Thoughts?

-Clayton South

EDIT: I should also note that I can check hotmail,even with dansguardian enabled, through firefox web browser. The problem seems to be Evolution specific.

---

### Post by mssever on 2008-09-09
> **Clayton South said:**
> the error within evolution was "Unable to connect to POP server 127.0.0.1 Error sending password: broken pipe." Should I also check the logs for tinyproxy?

This doesn't occur when I shut off dansguardian, and hotmail seems to work when dansguardian is off, so i know this is a configuration issue.
Check all potentially-relevant logs, including tinyproxy. A broken pipe error often (though not always) indicates a crash or other hiccup in a program the complaining program is trying to communicate with.

As far as configuration goes, check the configuration of dansguardian, tinyproxy, and your proxy settings to make sure they're correct. I use Gmail (the web interface) for all my e-mail, so I have no experience using dansguardian for mail filtering.

---

