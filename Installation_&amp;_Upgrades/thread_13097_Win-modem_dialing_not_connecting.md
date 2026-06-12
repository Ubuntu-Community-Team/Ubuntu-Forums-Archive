---
title: "Win-modem dialing not connecting"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by recmar on 2005-01-28
Finally I managed to install my agere ac'97 dial-up modem.  :mrgreen: I configured connection using Computer-SystemConfiguration-NetworkSettings in Gnome. When I'm trying to connect modem dials the number but I can't open any webside. :cry:  What's wrong? When configuring /etc/default/sl-modem-modules should I put in country from which I'm trying to dial-in (I'm in GB but in Windows my modem is set-up to USA and works fine).  Any suggestions, please.

---

### Post by az on 2005-01-28
in a console, do

sudo pppconfig
and enter your info.  Be sure to add your user in to the dip group in the advaced functions.

sudo pon
sudo tail -f /var/log/messages
to see what is going on.

Add the modem lights applet to your panel and change the settings so that the /var/lock points to the right file.

---

### Post by recmar on 2005-01-29
First of all - thak you very much for all your help Azz. 
Talking about my dial-up connection:
sudo tail -f /var/log/messages
J&#314;n 29 13:51:32 localhost chat[4708]: abort on (DELAYED)
Jan 29 1&#314;:51:32 localhost chat[4708]: send (ATZ^M)
Jan 29 13:51:32 local&#314;ost chat[4708]: expect (OK)
Jan&#314;29 13:51:32 localhost chat[4708]: ATZ^M^M
Jan 29 13:51:32 local&#314;ost chat[4708]: OK
Jan 29 13:51&#314;32 localhost chat[4708]:  -- got it
Jan 29 13:51:32 localhost c&#314;at[4708]: send (ATDT08458006122&#314;M)
Jan 29 13:51:32 localhost ch&#314;t[4708]: expect (CONNECT)
Jan 29 13:51:32 localhost chat[4708]:&#314;^M
Jan 29 13:51:32 localhost ch&#314;t[4708]: ATDT08458006122^M^M
Ja&#314; 29 13:52:02 localhost chat[4708]: CONNECT
Jan 29 13:52:02 loca&#314;host chat[4708]:  -- got it
Jan&#314;29 13:52:02 localhost chat[4708]: send (\d)
Jan 29 13:52:03 loc&#314;lhost pppd[4707]: Serial connection established.
Jan 29 13:52:0&#314; localhost pppd[4707]: Using in&#314;erface ppp0
Jan 29 13:52:03 loc&#314;lhost pppd[4707]: Connect: ppp0 <--> /dev/modem
Jan 29 13:52:37&#314;localhost pppd[4707]: LCP: timeout sending Config-Requests
Jan &#314;9 13:52:37 localhost pppd[4707]: Connection terminated.
Jan 29 &#314;3:52:38 localhost pppd[4707]: Exit.

There's few spelling errors which occured during copying text file to windows. Any idea whtat's wrong?

---

