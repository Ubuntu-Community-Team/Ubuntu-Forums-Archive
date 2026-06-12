---
title: "Setup wireless internet on Toshiba laptop"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by slade1988 on 2007-06-25
I have a Toshiba Sat. I pick up wireless internet and i was wondering how i can use it when i install Ubuntu?
Im new to linux.

---

### Post by jml on 2007-06-25
You will need to find out a few things about your laptop first. First find out what chipset your wireless card uses.  This information may be found in yout laptop's supplied documentation.  If not, you may be able to probe your hardware from within Windows.  Once you get that information you can search the forum for your specific card.

 I would suggest that your next step is to download the version of Ubuntu you want, (Ubuntu, Kubuntu, Xubuntu) and boot your laptop from it.  Use it as a live CD.  Once it is up and running, look in the upper right hand corner of the screen.  If you see a series of small vertical bars then you may be home free.  If they are present that means that Ubuntu has detected your wireless card and created a connection.  Click on the Firefox icon (web browser,) and see if you can surf the net.    Most people are not that lucky, so don't be disappointed if it does not work out of the box..

After booting, if you do not see any indication of wireless connectivity, go to Desktop and select System--->Administration--->Networking.  This will start Ubuntu's networking administration utility.  If your wireless card is listed, click on properties and configure the card's settings.  Then back out and you should be good to go.

If your card is not listed, then your task becomes a bit more complex but not impossible.  The specific steps depend on precisely what type of wireless card you have.  If you need to, repost here.

Another suggestion, while you are trying to connect for the first time.  remove all encryption (WEP, WPA, etc,) and turn on SSID broadcasting on your wireless access point.  Once you have things configured on an unencrypted network you can then add the encryption.  Hope that this helps.

Joe

---

