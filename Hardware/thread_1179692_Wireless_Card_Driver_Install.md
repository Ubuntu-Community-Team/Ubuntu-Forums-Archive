---
title: "Wireless Card Driver Install"
date: 2009-06-05
forum: Hardware
---

### Post by laser penguin on 2009-06-05
Can someone please help me install the drivers for my new wireless card. I have no clue how to do it I've never installed anything from a archive it has a read me but i dont understand it at all. Thanks in advance for any help.

Link to wireless card driver page (Linux One)-[http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=81_2&pid=269](http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=81_2&pid=269)

---

### Post by cariboo on 2009-06-06
It woould help if you told us what wireless adapter you are trying to setup, and which version of Ubuntu you are using. Please open an Applications-->Accessories-->Terminal and type:

```
cat /etc/lsb-release
```

and paste the output in your next post. The above command will print out soething that looks like this:

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu karmic (development branch)"
```

I'm running Karmic Koala as you can tell from the above output.

To print out the details of your wireless device, in the same terminal type:

```
sudo lshw -C network
```

The above command will print out the details of your network devices. Please paste the output of the above command in your next post.

---

### Post by laser penguin on 2009-06-06
Im running ubuntu 9.04 jaunty jackolope

---

### Post by laser penguin on 2009-06-06
And for the wireless card there is a link.

---

### Post by laser penguin on 2009-06-06
My bad don't know how i posted the link wrong. Try this one.

[http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=81_2&pid=269](http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=81_2&pid=269)

---

