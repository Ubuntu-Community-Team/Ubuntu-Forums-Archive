---
title: "Suggestions for inexpensive hardware?"
date: 2015-09-20
forum: Hardware
---

### Post by Robert C on 2015-09-20
I am a middle school computer technology teacher. My robotics students are interested in progressing from the Lego EV-3 environment to the Arduino environment. However, due to various school policies (no programming, no hacking [no, there is no definition for ‘hacking’]) we cannot use the school computers for the Arduino IDE.

I am curious if anyone direct me to an inexpensive device that my students can use for installing sketches?

This device will not be permitted to be connected to the internet; as such, sketch installs will need to be via sneaker-net. Further, there can be no expectation of an ability to install additional libraries or updates (unless they come via USB). I can get the peripherals, we just need the box. Any suggestions for something cheap and, while educational, likely to actually work?


[Note: I would have used an existing “cheap hardware” thread; but they seem to all be locked]

---

### Post by tshade on 2015-09-20
There are some little boxes with Intel Mobile that might suit you. They're like books.

---

### Post by mastablasta on 2015-09-21
would raspbery pi work?

what about Banana Pi or similar "clones"?

if you need i386, then there are various SoC options you could use but price will be about 130 EUR per system

---

### Post by Robert C on 2015-09-21
I went and looked at the Banana Pi, I see the same problem ion that one as I saw aon another cheap, single board, PC. It only has 1gb of ram and it isn't easy to upgrade. This is a problem because 64bit Ubuntu claims to require 2gb.

I would love to go with one if these single board computers because I think the process of putting it together would be good for the students. However, it would need at least 3 USB ports: Keyboard, Mouse, Arduino controller (yes, I can add an adapter). I see that the Banana is HDMI; so I would also need a HDMI to VGA adapter.

Si, yes, I am interested in any of the miniaturized single board PCs'; but it needs to be one that can run Ubuntu. These are students who are really struggling with real basics. If it is frustrating for you, it will be a showstopper for them.

The only one that looks close to what I need is the Raxda Rock Pro. I would still need a HDMI to VGA adapter, some secondary storage (microSD or SDXC card), and a usb port expander. In all that brings the 'low' cost price to a bit over $200. I still may go this route; I am just looking for other alternatives.

---

### Post by Bucky Ball on 2015-09-21
> **Robert C said:**
> ... due to various school policies (no programming, no hacking [no, there is no definition for &#8216;hacking&#8217;]) we cannot use the school computers for the Arduino IDE.

No offense, but this is a school where they teach things related to the early 21st century? :)  

> **Robert C said:**
> [Note: I would have used an existing &#8220;cheap hardware&#8221; thread; but they seem to all be locked]

Please start new threads rather than adding to another with your support request or awakening old ones (probably old ones were locked). This will improve your chances of support and avoid confusion.

Yes, the Raspberry Pi or an Odroid or Banana Pi would do fine, but one thing to remember is that, no matter what device you use, if you are using an open-source OS, part of the idea is that it can be tweaked, programmed, 'hacked' (in a good way), unless you purposely create guest accounts with a set of restrictions for the users.

Good luck with it. ;)

PS: Arduinos, in my opinion, are probably not the way to go for your purpose. That device is definitely about programming, hacking, tweaking, and having a great deal of creative fun with as you connect it to other devices and make it do all sorts of interesting things! You can do the same with RPis.

* Just read your last post. The [Odroid]("http://www.hardkernel.com/main/main.php") might be workable.

---

