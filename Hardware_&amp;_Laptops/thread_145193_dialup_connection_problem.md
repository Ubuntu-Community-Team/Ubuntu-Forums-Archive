---
title: "dialup connection problem"
date: 2006-03-15
forum: Hardware &amp; Laptops
---

### Post by zzigahertz on 2006-03-15
I am trying to set up my dialup connection on Ubuntu 5.10.

I installed a USR PCI modem model 5660a, and installed the free driver for it from Linuxant. When I activate the modem from the Network Connections interface, I hear the dial tone and hear the modem dial out. When I start Firefox and enter a URL or click on "getting Started" to go to Mozilla's website, it hunts around for a while, then gives me a message that the website cannot be found; please check the URL and try again.

If I just start Mozilla, I do not hear the modem dial tone or dialout, or any other modem sounds.

I suspect that Mozilla is not using the modem, but I don't know how to find out, or how to fix it...

I looked at the modem configuration and did not see anything unexpected. I did the modem diagnostic dump; it is a very long text file that didn't enlighten me a bit

Thanks for any suggestions.

---

### Post by Bentu on 2006-03-18
I suggest that you use wvdial to get your connection working. If you have the correct modem driver installed, it will work. You may have to install wvdial off your cd, if it hasn't already been installed. When you run wvdial in a terminal you will be able to see what it's doing, one line at a time. When it has finished connection and just sits there, leave the terminal open and then start your browser. Type in something like google.com, if it comes up you're good to go. From that point you can download kppp, or whatever you want to use regularly (you can use wvdial forever, if you want). To disconnect, just use cntrl-c. Search the forum for wvdial instructions, it's pretty easy to use, as a matter of fact when you install it off your cd it will step through the setup, asking you for your login, password, etc.

---

