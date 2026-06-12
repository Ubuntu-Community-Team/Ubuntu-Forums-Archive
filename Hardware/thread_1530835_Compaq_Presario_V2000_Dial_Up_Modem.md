---
title: "Compaq Presario V2000 Dial Up Modem"
date: 2010-07-14
forum: Hardware
---

### Post by zenarcher on 2010-07-14
I'm at a real loss here, as it's been at least 15 years since I've dealt with a dial up setup in a computer.  I really need some help!

I've installed Kubuntu 10.04 (64 bit) in a Comqaq Presario V2000 for a friend, who only has dial up access.  Everything is fine with the system, until I try to set up the dial up using KPPP.

Looking in KinfoCenter, I see the modem shown as an ATI SB400 AC'97 Modem.  I don't have a landline telephone line here in the house to connect to that modem, so currently am connected with my wireless network.

The ISP the friend is using is "DialUp4Less."  They are Linux friendly and offer this setup page for KPPP, with their example as OpenSUSE.

[http://www.dialup4less.com/kppp2.html](http://www.dialup4less.com/kppp2.html)

When I start KPPP, for openers, the "Wizard" does not have an option for U.S. dialup providers, so one is forced to use the Manual setup.

Under the Dial tab, I am able to enter a Connection Name as well as enter a telephone number for the dial up.  Authentication is correct as PAP/CHAP.  Under the IP tab, I am correctly set at Dynamic IP address.  Under the Gateway tab, again I'm set correctly at Default Gateway and the box is checked for Assign the default route to this gateway.

Now, I have a problem.  When I go to the DNS tab, "Manual" is marked and "Automatic" is grayed out.  According to the ISP instructions on the website above, I am to use Automatic DNS Configuration, but I cannot choose that option.

I don't know what I will experience beyond that point, as I cannot proceed past the issue with choosing Automatic DNS configuration.

At this point, I'm totally lost in regard to setting up the dialer and dial up configuration.  I'm not even sure if KPPP is the best approach to setting up a dialer.

I really need some help here and any and all help and troubleshooting assistance would be most appreciated!

Regards,
zenarcher

---

### Post by ieee488 on 2010-07-14
Try setting up a connection without using the wizard.


If you have a modem that is recognized in Ubuntu, you'll connect with or without the wizard.

---

### Post by zenarcher on 2010-07-14
I tried setting up manually, however KPPP will not give me the option to set the DNS to Auto.  However, I installed the gnome dialer which automatically detected the modem, allowed me to set the DNS to Auto and no problem at all.

Thanks much for the suggestion!

Regards,
zenarcher

---

### Post by ieee488 on 2010-07-14
You should set this thread to Solved.

I normally used Gnome-ppp when I had dial-up, but I wasn't sure whether to recommend it to you since you are using Kubuntu.

---

### Post by zenarcher on 2010-07-14
I tried to set it to Solved but couldn't figure out how.  If you can tell me, I will.

---

