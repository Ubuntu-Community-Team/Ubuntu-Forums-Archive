---
title: "Transimission Bittorrent Client often not connecting to peers"
date: 2008-08-29
forum: General Help
---

### Post by AkaiUsagi on 2008-08-29
Since I have started using Transmission, I've had trouble connecting to peers with many of my torrents. Before moving to linux I had been a long time uTorrent user, which I loved, so lack of torrenting experience isn't the problem, but Transmission seems not to work so well for me and I don't know how to fix it.

I mostly use torrents for anime. I recently downloaded Blade of the Immortal ep 3 and got a consistent speed of ~500kb/s. When I try to download FMP:F (with 63 seeders and 95 peers) and FMP:TSR(47 seeders, 81 peers), they are completely idle. When I download these same torrents using uTorrent on Vista, I don't have this issue. 

Could anyone explain what is the problem here and how I can fix it? Any help would be appreciated.

Thanks.

---

### Post by quibbler on 2008-08-29
I don't use Transmission. I use Deluge, which you can find in Synaptic.
You could also install Utorrent with Wine, which works fine in Ubuntu.

Regards quibbler

---

### Post by Therion on 2008-08-29
I had the exact same issue with Transmission at first.  Then, for some inexplicable reason, it started connecting and traffic started flowing.  I didn't change a single thing, it was like it just took some time for it to come up to speed (torrenting Ultimate Edition as I type this).  

If your patience is at an end, **Deluge** is a hugely popular BT client, as is **Azureus**.  Both would be in Synaptic.  I like Transmission though, for it's simplicity and low overhead.  Maybe give it some more time...  Not sure what else to suggest.  I'm sure something will work for you.

---

### Post by AkaiUsagi on 2008-08-29
Thanks, both of you. I installed Deluge and so far like the interface better than Transmission, but I'm having the same problem again. It acknowledges that the peers are there, but it won't connect with them.

For good measure, I opened a port for deluge, that's not one of the default ones, successfully. Does anyone know why this is happening?

---

### Post by tjwoosta on 2008-08-29
transmission works fine

i use it daily for downloading all kinds of stuff

(speeds usualy above 350kb/s on a standard dsl connection)

i can download an entire 4 season tv series within a day or two!

the reason your not getting connections is probably because you dont have the proper ports open

(this would also cause utorrent and deluge or any torrent client to run slower then they could be!)

are you using a router?

if so you would need to acess you router and setup port forwarding for whatever port the torrent client uses 
 (the ports that it uses can usually be found in the preferences)

here is a link that should help you figure out how to acess your router and how to setup forwarding
[http://portforward.com/routers.htm]("http://portforward.com/routers.htm")

(i recomend you DON'T use the pfconfig, instead just look up your router and learn how to open the ports yourself because that way you will understand exactly what is going on and how to open and close any ports of your choosing, also you dont have to worry about malicious software)

next you should check your OS firewall (windows or ubuntu, depending on which OS you are using) and make sure the proper ports are open on your firewall

now when you you connect with the client it will have all the correct ports available 
(meaning all your connections will connect ! )

this will greatly enhance the speeds with any torrent client

---

### Post by AkaiUsagi on 2008-08-29
tjwoosta, I appreciate the advice, but I've  already opened up the appropriate ports. You just didn't see my above post.  =)
Deluge and Transmission both work to some degree, but there are some files for which it doesn't work at all, like these FMP seasons. However, I've never had any problems with uTorrent on vista, even with these same torrents. In fact, they happen to move pretty fast. Can you tell my why this is, when  it works fine for other torrents?
And also, how do I check the firewall here on ubuntu to assure the right ports are open?

---

### Post by quibbler on 2008-08-29
> **AkaiUsagi said:**
> tjwoosta, I appreciate the advice, but I've  already opened up the appropriate ports. You just didn't see my above post.  =)
Deluge and Transmission both work to some degree, but there are some files for which it doesn't work at all, like these FMP seasons. However, I've never had any problems with uTorrent on vista, even with these same torrents. In fact, they happen to move pretty fast. Can you tell my why this is, when  it works fine for other torrents?
And also, how do I check the firewall here on ubuntu to assure the right ports are open?
In Deluge I use ports 50029-50035 (Edit - Preferences - Network)
In Firestarter [frontend for the firewall] I've made a Policy for
inbound traffic Deluge with these ports open (50029-50035).

---

### Post by Chrigi on 2008-11-12
I had the same problem and I figured out that it was because of my firestarter settings.
I had the "Outbound policy" set to restrictive but opened the BT port. BUT when you connect to other peers, it connects to their open ports and therefore all that traffic was blocked...
I then set the mode to permissive and it worked better.

Could someone tell me how I can configure firestarter, so that it does not interfere with Transmissions traffic but is set to restrictive?

---

