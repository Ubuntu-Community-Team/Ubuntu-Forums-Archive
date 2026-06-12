---
title: "Can a driver damage the LCD?"
date: 2011-12-04
forum: Hardware
---

### Post by brunces on 2011-12-04
Friends,

Please, I need some help, if possible. I have a laptop computer which  has a SiS Mirage 3 video card. This is a "complicated" video card, not  say something else. (eheh) I am Brazilian and many people here have  laptop computers with this video card.

We can find some drivers for this card on internet, but unfortunately, there's no 3D acceleration. We get only 2D acceleration.

I used to use this script to install the driver:

```
sudo apt-get install git xorg-dev mesa-common-dev libdrm-dev libtool
sudo apt-get build-dep xserver-xorg-video-sis
git clone git://github.com/hellnest/xf86-video-sismedia-0.9.1.git
cd xf86-video-sismedia-0.9.1
./configure --prefix=/usr --disable-static
make
sudo make install
sudo reboot
```Then, I came to know that it's possible to install the driver via PPA, using this:

```
sudo add-apt-repository ppa:acasagrande/xf86-video-sismedia
sudo apt-get update
sudo apt-get install xserver-xorg-video-sismedia
```Anyway, both drivers (I don't know if they are the same) work well, I mean, they offer a correct screen resolution of 1280x800.

I'm a member of a Brazilian forum and we've been discussing about this  video card and these drivers. Then, another member mentioned something  that made me a little worried. He posted this video...

[http://www.youtube.com/watch?v=wAGKSpYPhHU](http://www.youtube.com/watch?v=wAGKSpYPhHU)

... to show a problem that happens every time he starts Ubuntu. Every  time, before the X server is loaded, this weird effect happens with the  screen. Notice, the screen gets white from the edges towards the center. I  don't know if there's a name for this, sorry.

The point is, everybody who has this video card and uses these drivers  (and others we can find on the net) gets the same weird effect, me included.

That same member claims that his LCD got damaged (stopped working)  because (he thinks) of this effect. He said that, at first, the effect  was "weak". That white color went not so far from the edge towards the  center. Then, time passed and he said that the effect became stronger.  That white color almost reached the center of the screen. After that,  his LCD stopped working. He had to change his LCD, at a technical  assistance store. He doesn't know exactly if that effect caused the  damage, but he doesn't discard this possibility.

Now, I'm here to know your opinions on this. Can anyone tell if this  effect can really damage the LCD? Do you think that guy's LCD stopped  working because of this effect, happening lots of times, during a long  period of time? What do you have to say about this?

Thanks a lot, guys. :)

brunces

---

### Post by brunces on 2011-12-05
Anyone? Please... :)

---

### Post by foresthill on 2011-12-05
I think it's possible, especially with LCD displays. LCD displays are supposed to send out EDID data to the OS that lists the resolutions and refresh rates that the LCD can handle.

If this info is ignored by the video card due to a bad driver or no driver at all, and an LCD that can only handle a 60 hz signal gets sent a 120 hz signal, it's not hard to see how a display might be damaged. 

And this seems much more likely to happen when using an old video card that was manufactured back before there were LCD displays, and assumes the display is a CRT that can easily handle a 120 hz signal.

---

### Post by brunces on 2011-12-05
foresthill, thanks for your answer. Well, so I think I'd better stop using Ubuntu, before I get my LCD damaged. Pity! :(

When I buy a new computer, somewhen in the future, I'll make sure to buy one which doesn't have these crappy SiS components again.

Cheers, :)

brunces

---

### Post by jrfonseca on 2012-06-07
Hello brunces,

I had the same problem with my desktop.

Good luck!

---

