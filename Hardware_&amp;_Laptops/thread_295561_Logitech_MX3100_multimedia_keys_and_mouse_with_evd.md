---
title: "Logitech MX3100: multimedia keys and mouse with evdev, possible solution?"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by Tiftof on 2006-11-08
hey,

there is a problem when configuring the mx1000 from the mx3100 combo with the evdev driver: the multimedia keys from the keyboard don't work anymore. I've searched a couple of times here already and didn't found a solution. But a guy using gentoo has a solution. The problem is I don't know how to apply his fix. He talks about it [here]("http://www.tester.ca/2006/09/30/keyboard-with-way-too-many-keys/"). 

Could anyone tell me how to apply his fix in ubuntu? It'll probably involve recompiling the evdev driver, but that's all I can figure out...

Also check out [this post]("http://www.tester.ca/2006/09/28/xorg-71-and-the-logitech-mx3100-mousekeyboard-combo/") from him for the start of his mx3100 story.

thanks

---

### Post by bmoniker on 2006-11-09
Here's the skinny on recompiling evdev with the patch:

First, you need to make sure that you have all of the required includes:

```
sudo apt-get install xorg-dev
```

Which should install a lot of stuff, if I have the name right.  Then, grab the evdev source:

```
apt-get source xserver-xorg-input-evdev
```

That patch needs a quick edit to apply nicely... notice how it has stuff like --- a/src and +++ b/src when it's referring to the locations to patch.  Chop off the a/'s and b/'s so it just reads, for example, src/evdev_key.c.

Now enter the xserver-xorg-input-evdev-1.1.2 directory that apt-get made you, and:

```
patch -p0 < /path/to/fixed/patch
./autogen.sh --prefix=/usr
make
sudo make install
```

When you run the patch command, it should say that two chunks applied cleanly.

I tried this out for my mx3000, but lo and behold it didn't fix the other problem where evdev segfaults and hangs the system :(

---

### Post by Tiftof on 2006-11-10
hmmm, I still want to test this, can't hurt to try. But how would I disable the patch if it is giving me any problems?

---

