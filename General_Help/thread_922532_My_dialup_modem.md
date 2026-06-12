---
title: "My dialup modem"
date: 2008-09-17
forum: General Help
---

### Post by jras20 on 2008-09-17
I tried my dialup modem it says Modem not found on system.  How can I get it to detect it?  I have a Acer 5050-3785.  Of course the modem works fine in Vista.  But I'm not using Vista any more.

---

### Post by directcharitycontribution on 2008-09-17
dial-up is increasingly less supprorted to linux.

you can try a how-to page or more search.

and when u come to end put some []

---

### Post by EmanresuusernamE on 2008-09-17
How are you trying to access the modem?  Does the manufacturer have Linux drivers for it?

---

### Post by editrix on 2008-09-17
Check the link in my sig. You'll have to scroll through a lot, and don't be put off that it's for Dapper. Dialup hasn't changed at all, to my knowledge, since then.

---

### Post by phidia on 2008-09-17
The Ubuntu wiki on dial up [here]("https://help.ubuntu.com/community/DialupModemHowto") is probably the most clear and complete guide specifically for Ubuntu users.

---

### Post by jras20 on 2008-09-17
Thanks I'll look at the links, I'm not sure if my modem will work under Linux or not.  I never really messed with the drivers.  I'd just like to have it setup so that just in case I need dialup I can get on.

---

### Post by rraj.be on 2008-09-17
> **jras20 said:**
> Thanks I'll look at the links, I'm not sure if my modem will work under Linux or not.  I never really messed with the drivers.  I'd just like to have it setup so that just in case I need dialup I can get on.


Try this command and it will search for ur serial modems
```

sudo wvdialconf

```
and esit the configuration in the file ```
/etc/wvdial.conf
```

---

### Post by oilchangeguy on 2008-09-17
> **jras20 said:**
> I tried my dialup modem it says Modem not found on system.  How can I get it to detect it?  I have a Acer 5050-3785.  Of course the modem works fine in Vista.  But I'm not using Vista any more.

dial-up is on the way out. unless you live in a part of texas that's so remote, you should be able to get dsl or cable. most phone and cable companies have highspeed deals that have pricing very near that of dial-up. do yourself and your computer a favor. it's time to come into the 21st century. get a highspeed internet connection.

---

### Post by Shazaam on 2008-09-17
> **oilchangeguy said:**
> dial-up is on the way out. unless you live in a part of texas that's so remote, you should be able to get dsl or cable. most phone and cable companies have highspeed deals that have pricing very near that of dial-up. do yourself and your computer a favor. it's time to come into the 21st century. get a highspeed internet connection.

The op was asking for a way to set up dialup as a backup in case he needed it.
```
I'd just like to have it setup so that just in case I need dialup I can get on.
```
jras20, follow the link that phidia gave you.

---

### Post by oilchangeguy on 2008-09-17
> **Shazaam said:**
> The op was asking for a way to set up dialup as a backup in case he needed it.
```
I'd just like to have it setup so that just in case I need dialup I can get on.
```
jras20, follow the link that phidia gave you.

next time i'll have to read more, before i post. that being said most isp's don't support a manual dial-up connection. and good luck in getting an isp's dial-up software loaded on a computer running a non windows os.

---

### Post by EmanresuusernamE on 2008-09-17
> **oilchangeguy said:**
> dial-up is on the way out. unless you live in a part of texas that's so remote, you should be able to get dsl or cable.
Actually this is still not a viable option for lots of other regions.  Places like Hawaii, Alaska, middle of the dessert/mountains/forest.  I had a customer in Hawaii once call in for tech support, they couldn't get DSL period as they where too far away, and while they could have gotten cable, they would have had to pay to get the cable out to their location, which cost around 4-5 thousand, plus the monthly service.

Dial-up hasn't gone the way of the Dodo for a reason.

---

### Post by phidia on 2008-09-17
You don't need the isp's dial up software in linux. Gnome-ppp or other dialer will work fine if set up correctly.

---

### Post by jras20 on 2008-09-17
> **rraj.be said:**
> Try this command and it will search for ur serial modems
```

sudo wvdialconf

```
and esit the configuration in the file ```
/etc/wvdial.conf
```

I did that code, but it said modem was not detected

---

### Post by phidia on 2008-09-17
> **jras20 said:**
> I did that code, but it said modem was not detected

You need to follow the guide I linked earlier or go to [linmodems]("http://www.linmodems.org/") but I really recommend the guide since it's ubuntu specific. Most internal modems were designed to work with windows. Some of the components of those modems were eliminated and software replicated the hardware function. They can be made to work in linux but it's rarely fun.

---

### Post by jras20 on 2008-09-18
How do I find out what kind of modem I have?  I don't want to download the wrong driver.  I cant get the modem scanner to work.

---

