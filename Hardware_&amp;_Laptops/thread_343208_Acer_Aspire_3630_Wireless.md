---
title: "Acer Aspire 3630 Wireless"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by pod25 on 2007-01-21
Hi.
I finally installed ubuntu onto my acer laptop.
My biggest problem is getting the wireless to work, it's onboard along with the wired card.
I have followed several Howto's but without any luck.
I have installed the NDISWRAPPER but still no luck in getting this damn wireless to work.
Under the Network section (System/Administration/Networking/) my card it listed, there are 3 devices listed :
**Wireless connection** The interface eth1 is [COLOR="Red"]not active[/COLOR].
**Ethernet connection** The interface eth0 is [COLOR="Red"]active[/COLOR].
**Modem connection** The interface ppp0 is [COLOR="Red"]not configured[/COLOR].

Can someone please help to resolve this, the only way I can currently connect is to sit in the dark small cold ,very cold server room, my feet are bloody freezing :)

---

### Post by pod25 on 2007-01-21
Just to add.
My drivers for the wireless card are installed and can be seen via Device Manager.
Also I'm not sure if I already mentioned, but if I set the IP to dynamic then apply that, it does turn the wireless to [COLOR="Red"]Active[/COLOR] I then OK that, then I open Networking again to check to find it's be turned off again ! .
If I use a static IP set up, then apply that, I get an instant error, (config error)  !

I'm at a loss now.

---

### Post by FooAtari on 2007-01-21
Hi, I just installed Ubuntu on a Acer Aspire 3050 (i think thats the model) and got the wireless working fairly easy.

I'm no expert, the very opposite :)  But did it install properly?  I used this guide here, [http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper)

Worked first time, I didn't need to installed the acerhk driver (it was working, I didn't want risk breaking it), but maybe you do, there is a HowTo for that here; [http://ubuntuforums.org/showthread.php?t=224350](http://ubuntuforums.org/showthread.php?t=224350)

The wireless light came on straight away after installing the ndiswrapper driver, and I configured static IP and was good to go.

Sorry if I'm pointing out the obvious here :)  Thats as much as I know im afraid, I'm a bit of a noob with this linux carry on :D

Now if I only I could fix the bloody sound that easily...  It's difficult going from an experienced windows users, to linux a linux user, I really dont have a clue :biggrin:

---

### Post by pod25 on 2007-01-21
> **FooAtari said:**
> Hi, I just installed Ubuntu on a Acer Aspire 3050 (i think thats the model) and got the wireless working fairly easy.

I'm no expert, the very opposite :)  But did it install properly?  I used this guide here, [http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper)

Worked first time, I didn't need to installed the acerhk driver (it was working, I didn't want risk breaking it), but maybe you do, there is a HowTo for that here; [http://ubuntuforums.org/showthread.php?t=224350](http://ubuntuforums.org/showthread.php?t=224350)

The wireless light came on straight away after installing the ndiswrapper driver, and I configured static IP and was good to go.

Sorry if I'm pointing out the obvious here :)  Thats as much as I know im afraid, I'm a bit of a noob with this linux carry on :D

Now if I only I could fix the bloody sound that easily...  It's difficult going from an experienced windows users, to linux a linux user, I really dont have a clue :biggrin:

Well Mr Linux newbie, well done.
It probably helped by upgrading from 6.06 to 6.10 , but that howto (ndiswrapper) did the job.
I installed the package and the second it was complete my wireless light on the front of the laptop lit up like a HUGE firwork  =D>

---

### Post by FooAtari on 2007-01-21
I actually helped someone with a linux problem? WOOP :D

Well ok, I just pointed you in the right direction, but still, good enough for me ;)

---

