---
title: "Ubuntu 10.10 Asrock Core 100HT Intel MCP power or thermal limit exceeded messages"
date: 2010-12-28
forum: Hardware
---

### Post by yoma1977 on 2010-12-28
Hi all, just wanted to let you guys know i got rid of these messages by blacklisting them... (maybe someone else might want to avoid the spamming of there kern.log)
 
Traces like “MCP power or thermal limit exceeded” are showing up every 2 seconds, which is kind of really annoying to say the least. That module was activated (as far as I’ve investigated) in the Maverick release, so in order to avoid you logs growing fast, you can disable that by doing the following:
[LIST]
[*]Edit file /etc/modprobe.d/blacklist.conf
[*]Add at the end of the file **blacklist intel_ips**
[*]Save file and restart.
[/LIST]After restart, if you tail /var/log/messages you should not see that log trace again.
 
What i don't know is if this will have any other affect besides not registering the messages in the logs...

---

