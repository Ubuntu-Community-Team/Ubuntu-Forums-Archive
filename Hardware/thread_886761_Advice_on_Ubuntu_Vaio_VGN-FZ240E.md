---
title: "Advice on Ubuntu Vaio VGN-FZ240E"
date: 2008-08-11
forum: Hardware
---

### Post by jayhad on 2008-08-11
I just bought a Sony Vaio FZ240E and want to run Ubuntu on it.  I am new to Linux but want to try it and see how it compares to Windows.  So, I downloaded Ubuntu and added Wine for windows stuff (like games).

Are there other things I should download to make my Vaio work as it should (I have none of the Vaio drivers downloaded as I have nothing installed on the computer except Ubuntu)???  Are there downloads I need for the webcam, video, etc?  

Thanks, Jay

---

### Post by Nepherte on 2008-08-11
You don't need to install any drivers given by Sony. To get your webcam working, your FZ probably has a ricoh webcam. You can find the linux drivers for it here: [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

To be sure you have the webcam:
```
lspci
```
There should be entry with Ricoh in it.

If you have an ati or nvidia video card, you can install the 3d acceleration drivers by navigating to System > admin > hardware devices. Your card should be listed and you can then enable the check box.

---

### Post by jayhad on 2008-08-13
Thanks!  I have the Intel® PRO/Wireless 4965AGN wireless card.  Will it automatically use the N wireless capabilities (I have an N Apple airport router) or do I need to configure it at all.

In general, is there a way to test if everything is working as it should???

---

