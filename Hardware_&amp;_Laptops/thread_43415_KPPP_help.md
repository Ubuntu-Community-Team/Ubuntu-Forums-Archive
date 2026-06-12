---
title: "KPPP help"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by mokong on 2005-06-21
hey

        hope you guys can help me with this i have just installed kubuntu 5.04 / the problems is with the KPPP it wont connect just say initailze and then disappears ,
i found this website [http://www.blibbleblobble.co.uk/](http://www.blibbleblobble.co.uk/)  that gives some description 
about some kubuntu problems  imnot sure if i did some of this right

 ( First problem: /etc/resolv.conf hadn't been created. Need to sudo touch /etc/resolv.conf to even allow KPPP to run.
Second problem: KPPP couldn't connect to the internet. Need to add a * to the end of the line containing your password in /etc/ppp/chap-secrets, and add a noauth to /etc/ppp/options.)

how do i put noauth to /etc/ppp/options.

really been searchin for this in days now 
MAIN QUESTION REALLY IS how do i fix the problem with KPPP /will not connect
no errors /just says initialize modem and then disappear

im using a winmodem /
dual with win xp

help PLSS

---

### Post by Locke897 on 2005-06-27
Mokong,

Have you configured ppp (using *sudo pppconfig*) and KPPP? If you haven't, let me know and I'll post some instructions.

If you already have both ppp and KPPP configured, to change "auth" to "noauth" in your /etc/ppp/options file, type the following in a terminal:
```
sudo nano /etc/ppp/options
```
Then find the section that reads:
```
# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
auth
```
and change "auth" to "noauth." Press Ctrl+o then Enter to save and Ctrl+x to exit.

To add an * to your /etc/ppp/chap-secrets file, type the following in a terminal:
```
sudo nano /etc/ppp/chap-secrets
```
Place an asterisk between your username and password, so that it looks like:
```
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses


username       *       password
```
(At least this is what my /etc/ppp/chap-secrets file looks like; hopefully it will work for your system as well.  ;-) )

Good luck!

---

### Post by yoyo on 2005-07-04
Thanks for the "noauth" info Locke. I've mucked around all over without getting KPPP to work.

Cheers
Yo

---

### Post by cdhinch on 2005-07-19
Here is the prefered method of adding noauth.

```
sudo kedit /etc/ppp/peers/kppp-options
``` 

File before
```
#noauth
``` 

File after
```
noauth
```

Charles

---

