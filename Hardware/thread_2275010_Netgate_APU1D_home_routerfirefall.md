---
title: "Netgate APU1D home router/firefall"
date: 2015-04-23
forum: Hardware
---

### Post by Avanesov on 2015-04-23
I recently purchased a [Netgate APU1D]("http://store.netgate.com/kit-APU1C.aspx") to setup as a home router/firewall. My original intent was to install pfsense but I have since decided to try ubuntu server instead for consistency with my home network. Has anyone used Ubuntu for this hardware? Is there a good site for installation instructions? On a side note, what gui (if any) do most people use to manage an ubuntu router/firewall from their internal lan?

---

### Post by pepsifx357 on 2015-04-23
It may be overkill for you, and I know this is an Ubuntu forum, but I use ClearOS as a gateway/firewall.  It has A LOT of features and a GREAT web interface.  It's basically a full fledged small business server.

Here are some screenies: [http://www.clearfoundation.com/Software/screenshots.html]("http://www.clearfoundation.com/Software/screenshots.html")

There's an Ubuntu based Small Business Server/Gateway/Firewall software called Zentyal, but I could never get it to work right, so I can't recommend it.  I think you can install it on an Ubuntu system if you've already got Ubuntu installed.

PFsense is good, if you just want a gateway/firewall.  It's probably going to be the lightest weight distro to install.

If you're just going with Ubuntu I think the easiest firewall to use is UFW(Uncomplicated Firewall). [https://help.ubuntu.com/community/UFW]("https://help.ubuntu.com/community/UFW")

It doesn't have an interface, but it's extremely easy to use.  You might could look into webadmin.  I think they have a module for UFW.

I still suggest ClearOS though, I haven't had ANY problems with it and I can't think of another gateway/firewall that I can think of that's better IMO.  That is, if it can be installed on it.

---

### Post by Avanesov on 2015-04-25
Thanks for the reply. Ill check on ClearOS. In my op I used the term "gui", but "interface" would have been more accurate. The hardware has no video output. The image thats put onto the sdcard must be configured by serial port, or over the network if it can be booted up with ssh or a web interface available. It is basically a DIY kit for a linksys/buffalo etc.. type access point or router.

---

