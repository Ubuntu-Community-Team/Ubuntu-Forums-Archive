---
title: "Torrentflux - Cannot start torrents"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by eyeonthewinner on 2009-06-09
I'm running a lamp server and TorrentFlux on top of that. I was wondering why I cannot get past the status of Starting. My downloads will not start. I feel that it must be something simple because this is my first TorrentFlux installation.

So, I have forwarded ports on my router including 80 and some ports for bittorrent 6881 - 6990. I have all the green lights on the TorrentFlux settings page. I have a feeling that it has something to do with forwarding the same ports through apache? this is my /etc/apache2/ports.conf
```

Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>


```

Can someone who is experienced with this please help me? There is a lot of help for Torrentflux users using FreeBSD but not much for us ubuntu users. I've been googling for hours haha.

Thanks in advance!

---

