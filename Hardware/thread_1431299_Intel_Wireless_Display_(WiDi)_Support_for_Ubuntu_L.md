---
title: "Intel Wireless Display (WiDi) Support for Ubuntu Linux?"
date: 2010-03-16
forum: Hardware
---

### Post by Coder543 on 2010-03-16
I've done research, but there is not even a single instance of the words WiDi and Linux being in the same sentence anywhere in the entire internet. At least, none that I could find. So, I thought I would be the first. I would like to know if there is going to be support in Linux, specifically Ubuntu, for Intel's WiDi technology. This would be rather cool. Thoughts? Opinions?

---

### Post by teward on 2010-03-16
I will bet you that 65%+ of the people here have no clue what WiDi is.  Informational links please?

---

### Post by Coder543 on 2010-03-16
[http://www.intel.com/consumer/products/technology/wirelessdisplay.htm](http://www.intel.com/consumer/products/technology/wirelessdisplay.htm)

[http://www.engadget.com/2010/02/01/toshiba-satellite-e205-with-intel-wireless-display-review/](http://www.engadget.com/2010/02/01/toshiba-satellite-e205-with-intel-wireless-display-review/)

Its an interesting feature on some new laptops that enables the users to wireless connect to a TV, ideally for the purpose of streaming video.

---

### Post by teward on 2010-03-17
I'm going to assume that this technology is so new that Ubuntu (and Linux in general) does not support it.

---

### Post by Boondoklife on 2010-06-04
> **TrekCaptainUSA said:**
> I'm going to assume that this technology is so new that Ubuntu (and Linux in general) does not support it.

I really don't think he wanted to know if it is supported as of now, but more so will it be supported.

*crosses fingers* I hope there will be a USB adapter or something that will give older laptops that ability!

---

### Post by linuxlovinwarren on 2010-06-09
I would love to see this I have it on my laptop, and can only use it in windows. The tech is too new though,  it's very slow, and cuts in and out on a whim... I'd like to see Ubuntu kick the crap out of windows service for it!

---

### Post by finny388 on 2010-10-13
I was hoping this was OS independent.

Anyone know if there is news on linux support?

---

### Post by jeevas.v on 2010-12-24
From what I read, this technology uses the the same radio as wifi. So as per intel the Intel's new 6200/6250 and newer wifi cards support this. I don't know if this is using the same protocol stack as the WIFI. may be a WIFI ad-hoc network between the laptop and the netgear reciever and then the laptop streaming the video in a compressed format and the receiver decoding it??

In that case the processing power should be so high to do this thing real-time and may be that explains why this is only supported in very few laptop models with intel's selected few i3, i5 and i7 processors.

One sony vaio model with which they demonstrated this video got a dedicated key for this. My guess is that is just another short-cut key which will just activate the service.

If that is the case this can be easily(with lot of original development provided we have all the technology documents) accomplished in ubuntu also using a server software kind of thing or patching the xserver or whatever..


I hope intel open up this inexpensive technology and give us the wireless freedom...:)

---

### Post by jeevas.v on 2010-12-24
Ok now I see that the transmission is thru Wifi protocol itself and the bandwidth is limited to 720p at 10Mbps and there is approx half a second to one second delay.

So the technlogy is only usable to stream videos with sound also thru hdmi. So as of now it is not exciting or as usable. 

But the concept is interesting. Stream the laptop Video and Audio as a single stream thru Wifi.The adapter should have HDMI and other video outputs as well as analog and digital sound outputs. It should support atleast 1920x1080 with no noticeable delay.

By the time the Hardware is ready the Linux team should also come up with some interesting solution.

---

### Post by gcristof on 2011-05-29
Just got a new quad core Toshiba Satellite A660 that has WiDi technology. Am trying out Ubuntu and would love to see this feature working.. Could be very interesting in particular on Mythbuntu!

---

### Post by sh4d0000 on 2011-06-07
I have a vaio, I'm hoping intel WiDi will come soon on ubuntu

---

### Post by sac3528 on 2011-07-21
Frankly, most tv's already support streaming 1920X1080 video without lag over wifi, but only in the form of a file. i am working on an app for samsung Smarttv that allows streaming over wifi, and a backend on the pc side. the same will obviously work for ubuntu.

---

### Post by Frank Henderson on 2011-09-02
I wonder, until Ubuntu is made to work with Push2TV, if it might work in a Virtualbox installation of Windows 7. Does anybody know of any reason why it wouldn't?

---

### Post by Frank Henderson on 2011-09-06
I'm giving thought to what to do about windows 7 (which I need for my Netgear Push2tv adapter) and its relationship to ubuntu. According to Intel, widi needs Windows 7 in addition, of course, to a widi capable computer (like my new Dell Inspiron 17R). I need access to ubuntu from windows 7 for the pictures and other stuff I might want to put on the tv for viewing. So, as I see it, here are my alternatives:

1. Windows 7 and wubi for ubuntu
2. Dual boot with Windows 7 and ubuntu
3. Ubuntu and virtualbox with a windows 7 installation (ubuntu would be the host; windows the guest)
4. Windows with virtualbox with an ubuntu installation  (windows would be the host; ubuntu the guest)

Rationales:
1. I think I'd have total access to files on ubuntu in wubi. That's what I'd like. I'm not so sure about how well wubi will perform though.
2. Dual boot: probably not a good choice, because of lack of access. Apparently, according to something I read, sharing windows to ubuntu will work, but not the other direction. And it's the other direction I need. And then I'd have to reboot every time I wanted to use my push2tv gadget
3. I just don't know if windows 7 in virtualbox will allow me access to the "wireless display" (widi) capability of my computer. The two OSes do show their files and that's what widi does: shows whatever's on the computer screen.
4. This might be the answer: I'd have full use of widi via the installed Wndows and access to windows and ubuntu as needed. Boot-up would be longer since both windows and ubuntu would have to boot up. Startup could be set to automatically start ubuntu.

I wonder if there are any more alternatives. Any ideas or suggestions or comments (besides "Henderson, you're nuts!?)

---

### Post by dun270 on 2011-09-08
Try Totem, with plug-in "coherence DLNA/UPnP Client" installed(download separately), and configure it in totem.

---

### Post by kuvanito on 2011-09-11
WiDi is relatively new and the technology comes with Intel processors of the iX family it is Hardware related and not software.
The idea of transmitting A/V wireless from a PC to a TV is not new PC2TV has been here for some time.Nowadays you can buy these types of adapters almost everywhere,check out Walmart for example,Bestbuy,TigerDirect,Brandsmart USA,etc,etc,etc
Google PC2TV and you'll see.
There are quite few manufactures of differents brands of hardware,mostly for Windows based PCs but some are not Software Related either so we may be in good luck here just with the current OS we are running.

---

### Post by dbombtek on 2012-04-29
I have the widi card on my toshiba i5 and as far as I can tell 11.10 doesn't know it exists. I'm not sure if it is a seperate wifi card or no so I don't have a clue how to trouble shoot it. I would like to see Mrs on this but if not that's the reason I fall back to win7.

---

### Post by KoRnKloWn on 2012-12-09
WiDi uses the existing wifi standards, the computer and the push2tv box must be on the same wireless network, it's not using 2 separate wifi cards or anything. I can't find anything about Linux support though, which really sucks, because none of the other methods are really that good, all the other push2tv services are really laggy, and most don't get to 1080p, not to mention few have any Linux support whatsoever.

---

### Post by wormbuntu on 2012-12-09
> **Frank Henderson said:**
> I'm giving thought to what to do about windows 7 (which I need for my Netgear Push2tv adapter) and its relationship to ubuntu. According to Intel, widi needs Windows 

I've read that the recent Push2TV boxes are also DLNA renderers. [[http://www.anandtech.com/show/6321/netgear-updates-entertainment-lineup-with-push2tv-3000-and-neotv-300-series]](http://www.anandtech.com/show/6321/netgear-updates-entertainment-lineup-with-push2tv-3000-and-neotv-300-series]) 

So, you should be able to use normal DLNA to stream to the box, right? (easier to stream to TV but I'm assuming you don't have a "Smart" TV).

If the box/TV can handle DLNA then I'd suggest MediaTomb, which is fantastic and perhaps Upnp AV Control Point (which allows you to push from PC rather than pull from TV. 

I've got Widi on my laptop, but TV doesn't support it hence I use DLNA.

---

### Post by ledj0 on 2013-01-12
Just bought a Dell XPS 13 and configured it to match the DEll Developer Edition that runs a customized version of Ubuntu 12.04.

I am currently an enterprise architect but spent most of my 30+ years career as a developer and team lead. I can tell you that in both of these roles, I would deploy lots of efforts to be able to connect to TV monitor or overhead projector that are basic and indispensable tools in workshops and group meetings.

I love using Ubuntu on the desktop but, to my experience, its most important weakness is to downplay those special features that are used day in and out in corporate environment. Connecting a laptop to a large monitor is a move me and most of my co-workers do many times per day since many years. TO this day, we still have to toss around an lenghty and heavy VGA cable that keeps unpluging from the laptop connector due to its shear weight.

Maybe this WIDi feature is not "mainstream" to a majority of user but I can assure you that it would make a killing in the developper / architect / project manager / business executive and so on. And these are the ones who influence or decide on technology orientation and purchasing.

This technology is not that new since Windows 7 supports it since quite some time now. To be able to take its place in corporate envirionment, Ubuntu desktop should exercice a better leadership in prioritizing corporate type features.


Jacques

---

### Post by ventharin on 2013-10-24
I found a way to live transmit my desktop to a dlna capable renderer. I know, that isn't a miracast solution. It's more like a hack, but you know... my goal was to display my desktop's content on a tv. Whole article you can find [here]("http://realmike.org/blog/2011/02/09/live-desktop-streaming-via-dlna-on-gnulinux/").

Unfortunately, till today I didn't found any article or software you can run on linux, that will support miracast :( Perhaps it will be some day. Hope still exists.

---

### Post by brettmichaelis on 2014-03-08
has ubuntu or any linux distro been able to support WIDI yet.  Its been a while now since the technology was released

---

