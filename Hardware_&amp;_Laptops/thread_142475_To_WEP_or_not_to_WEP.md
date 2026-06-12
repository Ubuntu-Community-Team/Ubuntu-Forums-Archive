---
title: "To WEP or not to WEP"
date: 2006-03-10
forum: Hardware &amp; Laptops
---

### Post by m.musashi on 2006-03-10
I used to have my router set up with WAP but when I started to use ubuntu I had to dump it in favor of WEP (WAP didn't play well). However, ubuntu still tended to log on my neighbors network rather than my own so in the end I turned off all encryption and unhid my essid.

My question, how smart is that? I know most web sites with sensitive info encrypt the session (banks and such) and even Yahoo now submits passwords over ssl. So in these examples, is it much of a worry? I guess the content of emails would still be open but as long as I'm aware of that and don't send sensitive data unencrypted is there any concern?

Actually, how easy is it to eavesdrop on unencrypted wireless communication? It seems like something that the average neighbor wouldn't be able to do. I wouldn't know how. And my understanding of WEP is that it's easy to crack. So any neighbor who can figure out how to listen can probably figure out how to crack WEP.

So, what is the recommendation? Turn WEP back on, fight with ubuntu to do WAP, or not worry about it and just be aware of what I send?

---

### Post by Stealth on 2006-03-10
Fight with Ubuntu to get *WPA* ;)

---

### Post by m.musashi on 2006-03-10
[QUOTE=Stealth]Fight with Ubuntu to get *WPA* ;)[/QUOTE]
Okay. Any suggestions? I tried WPA supplicant or something like that. I never could get it to work. Is that the app to use or is there something better?

---

### Post by hw-tph on 2006-03-10
wpa_supplicant is currently *the* app to use to get WPA authentification going in Linux. [This](http://prinsig.se/weekee/index.php/Ubuntu#wpa_supplicant) is how I have it set up.


Håkan

---

### Post by m.musashi on 2006-03-10
[QUOTE=hw-tph]wpa_supplicant is currently *the* app to use to get WPA authentification going in Linux. [This](http://prinsig.se/weekee/index.php/Ubuntu#wpa_supplicant) is how I have it set up.


Håkan[/QUOTE]
Thanks for the link. I'll play around with it again. I'm not using ndiswrapper though (ubuntu configured my wifi card - lucky me). Is that a problem at all or do I just have to know the name of the driver when I do the config file?

Can anyone answer my other question about how easy it is to eavesdrop? If you know what you are doing is it extremely easy? Do you have to really know a lot or can just about any idiot do it? If I only use my laptop for activities I don't really care to keep secret should I even worry about this? I mean, what do I care if someone reads this. I'm posting it to a public forum anyway. I don't do banking or online shopping on my laptop.

---

### Post by lcg on 2006-03-10
[QUOTE=m.musashi]Can anyone answer my other question about how easy it is to eavesdrop? If you know what you are doing is it extremely easy? Do you have to really know a lot or can just about any idiot do it? If I only use my laptop for activities I don't really care to keep secret should I even worry about this? I mean, what do I care if someone reads this. I'm posting it to a public forum anyway. I don't do banking or online shopping on my laptop.[/QUOTE]
If you do not encrypt a wireless link, it's really easy to capture and read packets sent over that link. And, even worse, anyone can associate with that access point and use the internet connection.
I'd recommend at least WEP (and WPA if possible, WEP has some serious cryptographic weaknesses).

HTH,
Lars

---

### Post by ssalman on 2006-03-10
I asked a different but similar question a while ago, you may want to read the [thread]("http://www.ubuntuforums.org/showthread.php?t=123030&highlight=wpa+wep"). On any case I think you will like this [link]("http://www.grc.com/sn/SN-011.htm"), its about how easy it is to break into WEP. And if you still have time to play around with this, check out this [site.]("http://www.ethicalhacker.net/content/view/16/24/")

Good luck! :)

---

### Post by m.musashi on 2006-03-10
[QUOTE=lcg]If you do not encrypt a wireless link, it's really easy to capture and read packets sent over that link. And, even worse, anyone can associate with that access point and use the internet connection.
I'd recommend at least WEP (and WPA if possible, WEP has some serious cryptographic weaknesses).

HTH,
Lars[/QUOTE]
Thanks. Kind of what I expected. Although I'm not too concerned about sharing my internet. I never use it to its full potential anyway. However, I'd rather not share "everything" I send over my wireless. I guess I have another project for the weekend. Thanks for the help.

---

### Post by m.musashi on 2006-03-10
[QUOTE=ssalman]I asked a different but similar question a while ago, you may want to read the [thread]("http://www.ubuntuforums.org/showthread.php?t=123030&highlight=wpa+wep"). On any case I think you will like this [link]("http://www.grc.com/sn/SN-011.htm"), its about how easy it is to break into WEP. And if you still have time to play around with this, check out this [site.]("http://www.ethicalhacker.net/content/view/16/24/")

Good luck! :)[/QUOTE]
Thanks. Those all look interesting and useful. I'll add to my weekend project :).

---

### Post by lcg on 2006-03-12
[QUOTE=m.musashi]Although I'm not too concerned about sharing my internet. I never use it to its full potential anyway.[/QUOTE]
You might want to rethink that position. If someone uses your internet connection for something illegal, you would be the one to get in trouble for it.

Lars

---

