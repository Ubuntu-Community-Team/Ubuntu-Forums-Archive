---
title: "torrents start fast and get slow"
date: 2008-09-20
forum: General Help
---

### Post by doorknob60 on 2008-09-20
Well, just recently, when I download torrents, they start out normal, getting up to 200KB/s, then the speed drops down to around 5KB/s and stays there...painful for 3.5 GB's of The Office goodness :D I've tried a few different torrents, and both Deluge and Ktorrent, all with similar results...could it be my majorly crappy and half malfunctioning iBoss router, or my ISP? Last time I used torrents (a month ago max) it worked fine, but I think I might have used a different router...and I can't switch...Any ideas? I don't wanna wait a week for it....

---

### Post by mb_webguy on 2008-09-20
It could be due to several things, or a combination thereof.

If the torrent is not well seeded but has plenty of leeches with a portion of the torrent, then you'll download the common portion of the torrent quickly from the leeches, but then drop to slower speeds as you compete to download the remainder of the torrent from the seeds.  There's not really anything to do about this but to select torrents with better seed/leech ratios.

Your ISP could be throttling your downloads.  Some ISPs reduce your download speed for a while if you exceed a certain quota in a given time period.  There's really not anything you can do about this unless you're willing to switch service providers, and you can find one with a more liberal download policy.

You could also be overwhelming your router.  If your settings in your torrent client are too high, especially those for maximum connections and connection attempts per second, then your router may not be able to handle it.  Some routers will drop the connection completely, while others don't but function at a reduced capacity.  The easy solution to this is to reduce the settings in your torrent client to very low numbers, and then gradually increase them as your router proves capable of handling the traffic.

---

### Post by doorknob60 on 2008-09-20
The thing is, right now my torrent is downloading at about 15-20 KB/s, but there's 28 seeders, and I'm connected to 10 of them. Normally in these circumstances I'd be getting much higher speeds. Also, web pages still load fast like they should (I have cable internet).

---

### Post by technotitclan on 2008-09-20
i have the same problem, but i've gone through 2 different routers. honestly i have no idea what the problem is. i just suffer through the 4 days of d/l for each season of House.

---

### Post by Monotoko on 2008-09-20
Now, i dont mean to be critisizing ubuntu here, but this is just my experiance after trying some things out:

I dual-boot with Ubuntu and Windows Vista, i have noticed a significant increase in download rates torrents on vista, oddly.

I did some investigation, with the same torrent, i downloaded the first 5% of the torrent, and timed it, then moved onto the next OS.

the results were:
ubuntu: 2min 44secs
Vista: 1min 5secs

I repeated the investigation 5 times and on average, thats what they came out at, so maybe its something to do with ubuntu?

---

### Post by aragorn2909 on 2008-09-20
[QUOTE=mb_webguy]
Your ISP could be throttling your downloads.[/QUOTE]

I'd be willing to bet money on it.

[QUOTE=doorknob60]
they start out normal, getting up to 200KB/s, then the speed drops down to around 5KB/s and stays there.[/QUOTE]

Does this happen all through the day?  If I torrent on standard ports, my speed will drop during daylight hours, and jump in the wee hours of the morning.

---

### Post by technotitclan on 2008-09-20
i have both Ubuntu and Vista and have the same prob on both

---

### Post by mb_webguy on 2008-09-20
> **Monotoko said:**
> Now, i dont mean to be critisizing ubuntu here, but this is just my experiance after trying some things out:

I dual-boot with Ubuntu and Windows Vista, i have noticed a significant increase in download rates torrents on vista, oddly.

I did some investigation, with the same torrent, i downloaded the first 5% of the torrent, and timed it, then moved onto the next OS.

the results were:
ubuntu: 2min 44secs
Vista: 1min 5secs

I repeated the investigation 5 times and on average, thats what they came out at, so maybe its something to do with ubuntu?

That would be what I believe is called a statistically insignificant sample size, or anecdotal evidence.  Do that agan about 100 times, downloading the same first 5% of the same torrent, and then you might have some maningful results.

---

### Post by Monotoko on 2008-09-20
i did it with the same 5% of the same torrent, but i am not doing it 100 times -.-

---

### Post by mb_webguy on 2008-09-20
> **Monotoko said:**
> i did it with the same 5% of the same torrent, but i am not doing it 100 times -.-

I didn't really expect you to. :)  I was just saying that there's too many variables involved in downloading torrents to make a judgement based on that one comparison.  Even in the five minutes it took you to boot into Windows, there may be a different collection of seeders and leechers, and even if it's the same group, you're not guaranteed to connect to the same peers.  Internet traffic in your area could be heavier or lighter.  If you're not using the same client in Windows as you are in Linux it could have an effect.

  I'm not saying that you're not getting better average download speeds in Windows for some reason, only there are simply too many things going on to make a decision from one small test like that.

---

### Post by benerivo on 2008-09-20
Has anyone else tried [this]("http://www.theinquirer.net/gb/inquirer/news/2008/05/31/download-accelerator-for-linux"). It seems to improve downlod speeds slighty.

---

### Post by v1nsai on 2009-01-12
I'm downloading the same file with two different BT clients, transmission (ubuntu default) and deluge.  Deluge is downloading at 15-25KB per second, while transmission is downloading at about .25-.5KB per second.  I don't know what my problem could be, I really like transmission and I'd rather solve this problem than patch it.  What could be causing this?

EDIT:
Okay, I just did a few things, and one of them must have done it because my current downloads took off.  I watched them go from .5-1KB/s to 200-500KB/s.  Here's the first thing I did.

```
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
```

(I've read in some places that 6881-6889 should be open, but most just say 6881.  Haven't found a way to use the above code for that without manually entering '6881', '6882', '6883' which I haven't tried yet.  It worked for me.)

Now do:

```
sudo iptables -A INPUT -p tcp --dport 51413 -j ACCEPT
```

This opens the listening port on transmission.

Next, type 'nslookup localhost'.  Type the IP address listed for 'Server:' in the first line of the return into the address bar of your browser.  Depending on your router make it will ask you for your username and password (my netgear's default was uname 'admin' and passwd 'password'.  Forward ports 6881-6889 and port 51413.

Download speeds should take off momentarily.  You may need to 'service iptables restart' after changing the iptables.

---

### Post by sendblink23 on 2009-01-12
> **benerivo said:**
> Has anyone else tried [this]("http://www.theinquirer.net/gb/inquirer/news/2008/05/31/download-accelerator-for-linux"). It seems to improve downlod speeds slighty.

If you didn't notice.... this thread is talking about Torrents ... not normal Downloading utility on a normal browsing experience.

Although yes I have used it before and it works perfectly on normal downloads in the web. I haven't tested on Ubuntu 8.10, but it worked on 8.04.

---

