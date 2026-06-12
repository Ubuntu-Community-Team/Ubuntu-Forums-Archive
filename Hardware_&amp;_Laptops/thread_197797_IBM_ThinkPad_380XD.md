---
title: "IBM ThinkPad 380XD"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by cloakable on 2006-06-16
I've had this laptop for a while now, and recently got it fully working with Ubuntu. However, I have a few questions/requests.

I got the sound working, thanks to [this]("http://www.ubuntuforums.org/showpost.php?p=22546&postcount=6"), but I have no idea how to make this change permanent. I have the commands as a script now, but having to run the script every time I boot up is a bit of a chore.

I've installed xdm, but when the laptop finishes booting, the screen briefly goes blank, then I'm back at the normal login prompt. How can I fix this?

I would like to install some useful lightweight programs onto it. I'm using fluxbox at the moment, but I would like a good IM client, a file manager, a web browser, and an email client. I'm already using Gaim, but it's a bit heavy for my laptop (96Mb RAM), and I'd like something lighter. Preferably GUI :) I'm used to the command line, but the GUI is good for simply relaxing.

---

### Post by DarthMandeep on 2006-06-16
I think the /etc/rc.local file exists so that you can run your own scripts at startup. If your script is executable you can just add it to the bottom of that file, just remember to type the full path. I don't use it though, I just add a link to my scripts in the /etc/rc2.d directory, since I boot into the command line and prefer to have my startup scrips seperated. But the /etc/rc.local file works fine.

As for apps, I like JWM for my desktop as it provides an interface similar to IceWM while using half the memory. Rox-filer is an awesome file manager, very light and can also be used to manage your desktop wallpaper and desktop icons, if you like that stuff. I use Firefox on all my systems, but you might want to consider Opera. For machines even older than yours I would use Dillo for browsing, or glinks. Sylpheed is a light email client, also does usenet. I'm not familiar with a lighter graphical AIM client, naim is light but text-only.

Edit: Since your machine is memory-limited, make sure you're running as few background daemons as you can.

---

### Post by cloakable on 2006-06-19
[QUOTE=DarthMandeep]I think the /etc/rc.local file exists so that you can run your own scripts at startup. If your script is executable you can just add it to the bottom of that file, just remember to type the full path. I don't use it though, I just add a link to my scripts in the /etc/rc2.d directory, since I boot into the command line and prefer to have my startup scrips seperated. But the /etc/rc.local file works fine.[/QUOTE]
Ahhh, good :) Thanks for letting me know that.
> As for apps, I like JWM for my desktop as it provides an interface similar to IceWM while using half the memory. Rox-filer is an awesome file manager, very light and can also be used to manage your desktop wallpaper and desktop icons, if you like that stuff. I use Firefox on all my systems, but you might want to consider Opera. For machines even older than yours I would use Dillo for browsing, or glinks. Sylpheed is a light email client, also does usenet. I'm not familiar with a lighter graphical AIM client, naim is light but text-only.

Edit: Since your machine is memory-limited, make sure you're running as few background daemons as you can.
Hmm. I do prefer fluxbox, but can I get JWM from the Ubuntu archives?
I cannot use Firefox - 266Mhz and 98Mb RAM makes it a pig. It's a pity, it's so good. Is Opera any better? Dillo does produce good performance on my comp.
I'm using Sylpheed Claws on my laptop.
And it's okay - I've found Ayttm. It's similar to Gaim, but thankfully (much) lighter. Perfect for the laptop - I don't need the frills.

And what background daemons would you say are essential, and what ones can I safely get rid of? How do I do this? Are there any daemons from a server install I won't need on a laptop?

---

### Post by DarthMandeep on 2006-06-19
JWM is in the Ubuntu repos, I think Multiverse. It's an old version, but works fine. Getting a newer version would require compiling, so just try out the repo version, see if you like it. It looks like the old Windows interface, so I use it on the old machines I've setup for guest use. 

Opera is supposed to be lighter and faster than Firefox, but I've not tried it on old machines, so I can't really say. I'd use Dillo for most web pages on that laptop but for things that require javascript, SSL, and other features, I'd load up Opera.

I hadn't heard of Ayttm, I'll try it out.

I usually do a server install on all my machines, regardless of specs, so that I can customize the install. I don't recall if the default server install ships with any really unneeded background services, but you could run "top" to see what's loaded, and then Google each service to see if it's of any use to you. I've no need for things like Cron, Anacron, DHCPd, so I remove them. 

Lots of programs that run in the background, like web servers and print spoolers, are set to turn on when you boot Ubuntu. On old machines I rename the scripts that load those daemons so that they don't start by default. I've setup my old laptop to use CUPS for printing, but I don't load the cups daemon until I actually need to print. I've got the lighttpd web server installed so I can test my web pages and scripts, but I don't load that until I need it. It's not a real hassle for me, and it does help on low-mem machines.

BTW, how's X working for you? I had to use the FastVram and accel options on my Thinkpad 600e to get it working at a resonable speed.

---

### Post by cloakable on 2006-06-21
Hmm. X is nice and quick, but that could be because I'm using a different window manager - do you know the relative sizes of JWM/fluxbox?

And bugger - JWM is in the Dapper and Edgy archives, and I don't have a 6.06 disk yet. Ah well, it's on order.

And thanks for the services tips - I'm never going to use CUPS on the laptop, so that can go.

---

### Post by DarthMandeep on 2006-06-21
I think JWM is slightly lighter than Fluxbox, but I've tried other wms and that's not the issue. I think my slower draw rates are caused by the newer driver for the NeoMagic video card in my 600e. At least that's what Google has turned up.

Anyways, I installed Opera 9 on my laptop and it looks like it uses half as much RAM as Firefox. I do miss my extentions though. Seems like the lightest browser that's still functional for most people, compared to Dillo or glinks.

---

### Post by cloakable on 2006-06-22
Ahhh. Well, the 380XDs video chip seems well supported, whatever it is :)

And I'll see about getting Opera onto the lappy. Is there a version in the Ubuntu archives, or do I have to visit somewhere else?

---

### Post by DarthMandeep on 2006-06-23
I'm sure Opera 9 is in one of the unofficial repos somewhere, but I was feeling lazy so I just went to the official website and got the .deb file for Ubuntu. A quick "dpkg -i" later I was reading Slashdot in Opera and measuring its memory use.

---

### Post by cloakable on 2006-06-30
Cool.

---

