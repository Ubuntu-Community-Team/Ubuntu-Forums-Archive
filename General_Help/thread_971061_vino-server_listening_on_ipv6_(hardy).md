---
title: "vino-server listening on ipv6 (hardy)"
date: 2008-11-04
forum: General Help
---

### Post by rampageoberon on 2008-11-04
Hi,

I'm having troubles with vino-server in hardy. I understand there was a bug which made it listen on ipv6 when "local connections only" was enabled.

To get  round this I created rules in iptables to allow only local connections.

I just noticed that vino-server has been listening on ipv6 regardless. How can I change this to make it listen on ipv4?

The iptables rules fail for this and I don't use ipv6 anyway. The suggestions from [http://ubuntuforums.org/showthread.php?t=518965](http://ubuntuforums.org/showthread.php?t=518965) didn't work for me.

Thanks

---

### Post by seanx820 on 2011-11-22
did anyone figure this out, I am having this same problem with an up-to-date Fedora Core 13...

---

### Post by rampageoberon on 2011-11-22
Sorry never figured it out. I just used iptables to allow only local connections to the port.

---

