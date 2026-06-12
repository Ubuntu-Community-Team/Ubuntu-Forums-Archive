---
title: "[SOLVED] resolv.conf and opendns"
date: 2008-11-16
forum: General Help
---

### Post by Ameneon on 2008-11-16
So the last couple of days (weekend, as is normal for problems) my ISP has had some issues with DNS causing a number of sites to not be reachable due to fuzzy DNS connectivity. Being impatient I started looking around today for ways to work around this at least temporarily. I may not have done so in the best way but it was fairly effortless and appears to work as intended; I now have normal network connectivity again (or rather, normal DNS, the connectivit itself was always ok).

Basically, I just added an OpenDNS server to /etc/resolv.conf like so;
nameserver 208.67.222.222

after the default dns server which points to my router which again fetches the DNS from the ISP. So at least technically, if you're having similar problems, it would be my guess that this would work. Now, to leaving the advice and entering the questions instead:

1) I've seen a number of ways to accomplish this, from setting up a DNS server of your own to editing other files (DHCPsomething springs to mind) - is there a reason why one should not do what I've done and just add a DNS server to the resolv.conf file? Ie, will it be deleted on boot or something?

2) OpenDNS seems from what I can tell "legitimate" enough, but I have no experience with them before - anybody know whether using their servers generally would be about as safe as using the ISP's servers?

---

### Post by iponeverything on 2008-11-16
> **Ameneon said:**
> So the last couple of days (weekend, as is normal for problems) my ISP has had some issues with DNS causing a number of sites to not be reachable due to fuzzy DNS connectivity. Being impatient I started looking around today for ways to work around this at least temporarily. I may not have done so in the best way but it was fairly effortless and appears to work as intended; I now have normal network connectivity again (or rather, normal DNS, the connectivit itself was always ok).

Basically, I just added an OpenDNS server to /etc/resolv.conf like so;
nameserver 208.67.222.222

after the default dns server which points to my router which again fetches the DNS from the ISP. So at least technically, if you're having similar problems, it would be my guess that this would work. Now, to leaving the advice and entering the questions instead:

1) I've seen a number of ways to accomplish this, from setting up a DNS server of your own to editing other files (DHCPsomething springs to mind) - is there a reason why one should not do what I've done and just add a DNS server to the resolv.conf file? Ie, will it be deleted on boot or something?

2) OpenDNS seems from what I can tell "legitimate" enough, but I have no experience with them before - anybody know whether using their servers generally would be about as safe as using the ISP's servers?

OpenDNS rocks. You are way less likely to suffer from a dns poisoning attack using opendns, go to there webpage and read about them.  Your resolv.conf will get nuked when your dhcp lease expires. There is an option that you can use for the dhcp client that will prevent this.

---

### Post by Ameneon on 2008-11-16
Thanks for a very clear answer :) I can set the dns servers manually in the router config which I guess then would be the better way to do it, unless that might cause problems with the ISP? I'll look into the dhcp file I saw mentioned earlier as I'm guessing that's the config file for the dhcp client, thanks for the answer again :)

---

### Post by iponeverything on 2008-11-16
> **Ameneon said:**
> Thanks for a very clear answer :) I can set the dns servers manually in the router config which I guess then would be the better way to do it, unless that might cause problems with the ISP? I'll look into the dhcp file I saw mentioned earlier as I'm guessing that's the config file for the dhcp client, thanks for the answer again :)

Nope, it will cause no problems with your ISP and is a perfectly valid way of doing it.

---

