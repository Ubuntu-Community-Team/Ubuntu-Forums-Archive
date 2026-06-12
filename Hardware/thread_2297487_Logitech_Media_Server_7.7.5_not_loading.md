---
title: "Logitech Media Server 7.7.5 not loading"
date: 2015-10-02
forum: Hardware
---

### Post by BarryD9545 on 2015-10-02
I've done a fresh install of Ubuntu 15.04 with Gnome Fallback.


I reinstalled Logitech Media Server from the .deb available at [http://www.mysqueezebox.com/download](http://www.mysqueezebox.com/download) (redirected from [http://logitech.com/mediaserver](http://logitech.com/mediaserver)), and even after a seemingly successful restart via
 ```
sudo service logitechmediaserver restart
```
the server does not show as a source on my Logitech Media Player (on a Logitech Revue), and I can't get the web interface to come up (standard "webpage is not available") using the direct IP address on my LAN (192.168.1.3:9000).

Logitech Media Player _does_ find MediaTomb as a source, and start it's web interface.

It all worked on an UPGRADE to 15.04 before the fresh install, and after three days of banging my head I'm ready for some advice.


Thanks...

---

### Post by BarryD9545 on 2015-10-05
Bump

---

### Post by BarryD9545 on 2015-10-05
[U][B]UPDATE:

[/B][/U]As stated above, I had LMS running and after a fresh install to 15.04, the LMS UI wouldn&#8217;t come up , and is no longer found by my Logitech revue.

Following advice from Logitech Support, I installed LMS 7.8.0, followed by *today&#8217;s* version, logitechmediaserver_7.8.1-1443766387_all.deb, but still no UI or broadcast.

System Monitor shows that squeezeboxserver_safe (owned by squeezebox) is starting&#8230;I&#8217;m used to seeing squeezeboxserver (sans &#8220;safe&#8221;) as the process. 

I see squeezeboxserver_safe starting and stopping when I run

```
 $sudo service logitechmediaserver start
```
and
```
$sudo service logitechmediaserver stop
```

After a few moments of inactivity, user "squeezebox" starts the process "sleep".

I&#8217;m using software center to install the .deb, so it&#8217;s being installed as an admin&#8230;I&#8217;ve run out of ideas.

MediaTomb and BubbleUPnP are running flawlessly; albeit not as efficiently.

Any clues would be awesome.

Thanks...

---

### Post by 41Nick on 2016-05-01
I have had similar issues trying to get this to work with ubuntu 16.04. I had just downloaded version 7.9 of LMS and that seems to work (I havent tested much yet)

---

