---
title: "NetworkManager, no connection on startup"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2005-10-15
I tried using NetworkManager on Breezy, and it works fine.
The big issue is that I do not have network on startup, my main networks are all non-broadcasting with WEP encryption on.  

NM only starts these after I have logged in, but then I cannot use my kerberos passwords.

Is there any way to give it a list of networks with WEP keys to connect to at bootup?

Thanks

---

### Post by nocturn on 2005-10-17
bump

---

### Post by knappen on 2005-10-17
What if you manually add your essid and wep to you etc/network/interfaces file?

I used the NetworkManager under Fedora and it worked really great.

---

### Post by nocturn on 2005-10-17
[QUOTE=knappen]What if you manually add your essid and wep to you etc/network/interfaces file?

I used the NetworkManager under Fedora and it worked really great.[/QUOTE]

It's in there.  If I remove NetworkManager (or prevent it's daemon from starting), the interfaces come up.

With NeworkManager, they only start after I log in and select an AP.

---

### Post by nocturn on 2005-10-18
*bump*

---

### Post by plutoprime on 2005-10-19
As far has I know the current version of NM daemon doesn't handle wireless connections with WEP until the applet gets loaded. I believe the reason for this is how the WEP keys are stored for additional security which requires keyring authentication before you are allowed access to that WAP....

---

### Post by nocturn on 2005-10-19
[QUOTE=plutoprime]As far has I know the current version of NM daemon doesn't handle wireless connections with WEP until the applet gets loaded. I believe the reason for this is how the WEP keys are stored for additional security which requires keyring authentication before you are allowed access to that WAP....[/QUOTE]


That could explain it.  And the netdaemon probably takes over before /etc/network/interfaces is read...

This is very unfortunate for my personally, so I cannot use NM.

---

### Post by civilwarlord on 2005-10-19
When I boot up, Ubuntu connects to my wireless network (with wep), but I'm not sure how I did it.  I think it had something to do with me adding the wifi-radar.

---

### Post by Confuse on 2005-10-19
This is not too related, but I'd rather post here than start another networkmanager thread. Is there any way to save my keyring password so networkmanager connects at startup automatically without that keyring password?

---

### Post by nocturn on 2005-10-20
[QUOTE=civilwarlord]When I boot up, Ubuntu connects to my wireless network (with wep), but I'm not sure how I did it.  I think it had something to do with me adding the wifi-radar.[/QUOTE]

wifi-radar does the same thing as NM, but in a different way.  The keys are saved to /etc/wifi-radar and read at boottime.  
Unfortunately, it hangs my machine (ndiswrapper).

---

