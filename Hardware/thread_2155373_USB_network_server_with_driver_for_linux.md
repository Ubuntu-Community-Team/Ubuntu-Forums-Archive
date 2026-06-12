---
title: "USB network server with driver for linux"
date: 2013-06-18
forum: Hardware
---

### Post by jarrebesetoert on 2013-06-18
Hi,

I want to setup some video surveillance using a couple of simple (cheap) webcams. These would have to be connected to my Ubuntu server, which is in another building. I have a wired LAN network connection, so all I need is a way to connect these USB webcams to the wired (UTP) network. I found some USB network servers which would do that, but there seems to be no linux driver support for them. Can anyone please tell me what my best option would be to proceed?

- find a way to get the Windows drivers for this USB network server (which I have: cmp-usbnetbox4) to work on my Ubuntu server?
- use an old laptop (which I have) and install Ubuntu on it with usbip?
- buy a Raspberry Pi (or something like that) and install a linux on it with usbip?
- find a USB network server that does have support for Ubuntu? (do you know any?)
- a secret other option?

---

### Post by dargaud on 2013-06-18
> 
- find a way to get the Windows drivers for this USB network server (which I have: cmp-usbnetbox4) to work on my Ubuntu server?

Probably impossible
> 
- use an old laptop (which I have) and install Ubuntu on it with usbip?

Possible but too much extra work and wasted power.
> 
- buy a Raspberry Pi (or something like that) and install a linux on it with usbip?

You probably need more than the one USB plug of the Pi.
> 
- find a USB network server that does have support for Ubuntu? (do you know any?)

I have no idea what a USB network is.
> 
- a secret other option?
Yes: get webcams that have an ethernet plug instead of USB.

---

### Post by jarrebesetoert on 2013-06-18
Thanks for your fast response, dargaud.

> [COLOR=#000000]I have no idea what a USB network is.

Actually it's a USB network server, a small device with a couple of USB ports on one end and an ethernet port on the other end. That way, the USB ports become "available" on the ethernet (LAN) network (for instance this one: [/COLOR][http://www.marelectronics.gr/products.php?id=14558&lang=en](http://www.marelectronics.gr/products.php?id=14558&lang=en))[COLOR=#000000]

[/COLOR]> [COLOR=#000000]Yes: get webcams that have an ethernet plug instead of USB.

Obviously, this should have been another option in my list, but I was hoping to keep this as a last resort, since these IP camera's can get quite expensive while I already have some very cheap webcams available.

Of course, if there is no other way, I'll probably have to do it that way. I also wanted to attach some storage to this USB network server, so that it could also be a cheap(er) hard disc than those expensive NAS drives.[/COLOR]

---

### Post by user_of_gnomes on 2013-06-18
Did you look into Video 4 Linux and [http://www.zoneminder.com/](http://www.zoneminder.com/) ?

Works pretty well.

---

### Post by jarrebesetoert on 2013-06-18
> [COLOR=#000000]Did you look into Video 4 Linux and [/COLOR][http://www.zoneminder.com/](http://www.zoneminder.com/)[COLOR=#000000] ?

Actually, that's what I'm running on my Ubuntu server ;-)

The problem still remains though that I have USB webcams to connect remotely (through my ethernet LAN going to another building). This can easily be resolved by connecting IP camera's, but they are quite expensive.[/COLOR]

---

### Post by steeldriver on 2013-06-18
it sounds like you need to run some kind of streaming media server on the remote box - I don't know what the latest and greatest is, you could start with ffserver

---

### Post by jarrebesetoert on 2013-06-18
> [COLOR=#000000]it sounds like you need to run some kind of streaming media server on the remote box

Yes, that's exactly right. The problem is, I don't have a remote box (yet). I might use an old laptop for this, a raspberry Pi or something else. However, my first choice was to try an out-of-the-box so called "USB network server", which does this automatically but I cannot seem to find one with support for Linux. So, if no one knows of an easy, cheap way to do this, I'll have to go with one of the options mentioned above.[/COLOR]

---

### Post by msbroadf on 2013-06-29
You could try the software i wrote.

[http://www.virtualhere.com](http://www.virtualhere.com)

Its still in beta but you can use for testing and see if it meets your requirements.

Michael

---

