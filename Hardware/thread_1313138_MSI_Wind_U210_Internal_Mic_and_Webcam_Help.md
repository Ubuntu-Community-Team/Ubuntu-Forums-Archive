---
title: "MSI Wind U210 Internal Mic and Webcam Help"
date: 2009-11-03
forum: Hardware
---

### Post by ryman102990 on 2009-11-03
This thread is dedicated to enabling the webcam and internal mic in the MSI Wind U210 for use in common webchat/video chat programs such as skype or pidgin. I have been in touch with someone who has figured out that both the mic and webcam are recognized, but not fully supported. 

Hopefully someone has the knowledge to get these working!

---

### Post by DaPunk on 2009-11-07
I have a MSI model MS-1451-ID1 and lsusb showed:

Bus 001 Device 004: ID 5986:0241 Acer, Inc

With some Google time, I found a URL that lists UVC compatable devices

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)    

My device shows as in the URL:    
5986:0241 Bison (MSI Wind Top AE1900 nettop) Bison Electronics

I got it to work by installing in Ubuntu 9.10 (using cheese to capture):

sudo apt-get install uvccapture
sudo apt-get install subversion

Now if I can only get the rt3090 to work without having to do a "sudo modprobe rt3090sta" after login. Also, no WPA access yet, only WEP.

---

### Post by monarchheels on 2010-01-26
I just bought the MSI U210-008US last week and put Ubuntu Netbook Remix on it. The webcam wasn't automatically detected.
However, after ran updates last night (25 January 10) the issue was fixed on its own.

---

### Post by Nerdfest on 2010-09-02
At some point during the tweaking for a wireless fix in 10.04, my webcam has stopped working. There don't seem to be any kernel modules loaded. I've tried modprobe uvcvideo, but still see no video devices under /dev. Can anyone help?

---

### Post by lidex on 2010-09-03
> **Nerdfest said:**
> At some point during the tweaking for a wireless fix in 10.04, my webcam has stopped working. There don't seem to be any kernel modules loaded. I've tried modprobe uvcvideo, but still see no video devices under /dev. Can anyone help?

See this:
[http://www.linlap.com/wiki/msi+wind12+u210](http://www.linlap.com/wiki/msi+wind12+u210)

---

### Post by Nerdfest on 2010-09-03
Sadly, that solved my problem. I say "sadly", as all I needed to do was  press FN-F6. I'd like to say that problem has never happened to me  before (with wireless on other laptops), but I'd be lying. Thanks for  the help.

---

