---
title: "[SOLVED] Need mail help"
date: 2008-09-19
forum: General Help
---

### Post by dbyrne on 2008-09-19
I can't figure this one out at all, any help appreciated ...

I run a Ubuntu server on my home network as a utility server for the PCs around the house. My cable provider has a mail gateway, and all PCs in the house are configured to send mail via the ISP smtp server. However the Ubuntu server runs an smtp sendmail server which sends all mail from unix users logged into the server directly to the MX server for the target domain. It also relays mail for my roaming PC which connects into the home network via an openvpn tunnel over whatever wifi or mobile broadband I happen to be using at work or on the road.

While that's fine for many mail destinations, other networks reject mail because it's coming from the dynamic IP address assigned to my router.

What I need to do is have the Ubuntu server emulate a mail client, always sending email via my ISPs SMTP gateway.

Any ideas ? Is sendmail the right tool for the job ?

edit: got after a couple of hours browsing. sendmail is  spot-on, the DS directive was what I needed. I can now compose mail online or offline and then send mail when connected from my eee PC via home wifi, work wifi, internet cafes or vodafone mobile broadband through my home server. Super cool !!

---

