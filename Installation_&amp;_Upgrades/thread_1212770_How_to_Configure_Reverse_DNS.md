---
title: "How to Configure Reverse DNS"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by nara_456 on 2009-07-14
Hi All

Can anybody suggest me on how to build reverse dns

here is my forward dns

$TTL 86400

             @  IN      SOA     ns1.ityug.com.  root.ns1.ityug.com.(
                        2006081401
                        28800
                        3600
                        604800
                        38400
                        )


        IN              NS              ns1.ityug.com.

        IN              MX      10      mta.ityug.com.


   ; Machine Names
localhost   IN   A       10.0.0.3
ityug1      IN   A       10.0.0.2
ityug2      IN   A       10.0.0.5



and created a file rev.0.0.10.in-addr.arpa

$TTL 86400
        @       IN      SOA     ns1.ityug.com. root.ityug.com. (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
                )

        IN      NS      ns1.ityug.com.
1       IN      PTR     ityug.com.
~                                        

Did I made any miskate in Reverse DNS , Please Suggest ME

---

