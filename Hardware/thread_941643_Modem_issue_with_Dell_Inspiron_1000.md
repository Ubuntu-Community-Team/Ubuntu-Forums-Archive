---
title: "Modem issue with Dell Inspiron 1000"
date: 2008-10-08
forum: Hardware
---

### Post by achase79 on 2008-10-08
I have a Dell Inspiron 1000 and have been trying to get linux to be able to use my modem for dial-up.  I have read everything I can from this and other forums, linmodems.org, and other user's websites, but I continue to have the same problems.  I can usually install the modem driver (sl-modem) and get it to dial out but then it just hangs and give a no carrier response.  Has anyone gotten this to work in Hardy? I have run out of ideas.

---

### Post by phidia on 2008-10-08
Have you tried the "sudo pppconfig" command from a terminal?

pppconfig creates files and allows you to select a dial out user too.

If you need more in depth guidence the Ubuntu wiki has a complete howto on dial up [here]("https://help.ubuntu.com/community/DialupModemHowto").

Maybe though I'm not certain you are having problems because xfce has a slightly different way of handling ppp. What does your /etc/ppp directory contain?

---

### Post by achase79 on 2008-10-09
in /etc/ppp is
[IMG]http://thewickedneedle.com/images/Files.jpg[/IMG]
I can dial but it keeps giving me "No Carrier" when I wvdial.
I used pppconfig so I could use pon to start the session but it never connected either.
I have checked the ubuntu wiki and followed the instructions (because I thought it might be my driver) but no luck.

---

### Post by achase79 on 2008-10-13
Does anyone have any advice?

---

