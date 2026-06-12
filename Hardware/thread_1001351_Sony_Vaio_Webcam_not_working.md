---
title: "Sony Vaio Webcam not working"
date: 2008-12-03
forum: Hardware
---

### Post by steve101101 on 2008-12-03
My webcam will not work for skype. I have a sony vaio VGN-CR120E. I got it working before, but on an early version of ubuntu and don't remember what I did. I entered the following code following someones elses advice. But it did nothing please help

```


sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make clean &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)


```

---

### Post by steve101101 on 2008-12-04
I was able to get the video to work however the test image is very blurred and looks mirrored. Other people have had this issue but I cannot fix it. Please help.

---

### Post by duxi on 2010-02-22
Here's a tutorial for sony webcam r5u870:
[http://duxthefux.blogspot.com/2009/11/webcam-ricoh-r5u870-einrichten.html](http://duxthefux.blogspot.com/2009/11/webcam-ricoh-r5u870-einrichten.html)

---

