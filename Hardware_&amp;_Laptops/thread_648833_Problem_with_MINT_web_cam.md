---
title: "Problem with MINT web cam"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by Chainz on 2007-12-24
Hello,
I have a web cam MINT (short description can be found [here]("http://mint-electronics.com/produkty/peryferia/72-MW-2035-350K-USB.html"))
I'd like to use it in Skype.

When I connected it, I managed to use it's build-in microphone without any problems, just like that!
Then I downloaded newest Skype beta and unfortunately it says: no video detected :(

I'm kind of newbie here, so have no idea on even how to start to make it work.
I read some other posts but were either not useful or too hard for me.

I hope there is a way to make this cam work, don't you think so?

---

### Post by linuxwizard on 2007-12-24
Try EasyCam to see if it can find a driver for you.

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by Chainz on 2007-12-25
Thanks so much for the reply, but unfortunately EasyCam didn't help :cry:

---

### Post by linuxwizard on 2007-12-25
Try this in terminal > lsusb -v  [COLOR="Red"]or[/COLOR]  lsusb > post results > this will list vendor & product id#

---

### Post by Chainz on 2008-01-03
lsusb command gives me that output:

```
0c45:60ec Microdia
```


Sorry for such a late response but you know... Christmas, New Year and so on ;)

---

### Post by linuxwizard on 2008-01-03
I did some searching on 0c45:60ec Microdia could not come up with anything showing if it will work or not in linux. Nothing in forum with that ID. I have seen others talk about Microdia webcams using drivers from link below. But not sure if it will work for yours. Try looking around on the website you might come up with something.

[http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by Chainz on 2008-01-03
Thanks for the ultra fast response! :D
I'll try that link.

---

### Post by intel on 2008-01-07
For all those with microdia (0c45:xxxy) webcams, please visit this website

https://groups.google.com/group/microdia

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

---

