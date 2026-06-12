---
title: "Changing DNS forwards"
date: 2012-10-03
forum: Hardware
---

### Post by wlraider70 on 2012-10-03
I have a DNS caching server setup. Originally I had used openDNS, but I don't want those crap "http://www.website-unavailable.com" pages I want a real error. 

I have been searching for any mentioned of open dns and changing to goggle, but I still get those fake error pages.

I have also run "rndc flush"


/etc/bind/named.conf.options  says
```



options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                8.8.8.8; 8.8.4.4;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};


```

---

