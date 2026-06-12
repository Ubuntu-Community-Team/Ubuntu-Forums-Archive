---
title: "Squid 3.1 Transparent Proxy"
date: 2008-08-20
forum: General Help
---

### Post by Gohtar on 2008-08-20
I have downloaded and built the latest build of squid and installed it on computer running server 8.04.

My whole goal was to have a transparent proxy that can handle https.  I was reading that the sslBump would allow me to do this.  The main purpose of the proxy is web filtering.  I don't cache anything.

So far I have been able to get it working to the point where it is running in transparent mode and HTTP works just fine.  When you try to access a website that is HTTPS it just times out.

I have added the correct iptable rules for port 443.  I have also tried putting HTTP and HTTPS on different ports like 3128 and 3129.

If I had to guess this is an iptables problem but I am stuck and really new at this.

Thanks

---

### Post by joshuacl on 2009-10-24
Were you ever able to get this working.  I am trying to do the same thing.  Any help would be appreciated. Especially the configure options you used when you compiled the source code.

---

